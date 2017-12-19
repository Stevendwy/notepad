<template>
  <div class="hub-container">
    <div class="title-container">
      <div class="title">
        <span class="t-name" v-once>萤火虫卖家中心</span>
        <span class="t-company">{{userInfo.company}}</span>
        <span class="t-hub" v-once>库存管理</span>
      </div>
    </div>
    <div class="h-content">
      <search
        title="库存管理"
        @search="search"
        @change="searchChange"></search>
      <div class="total-info">
        <div class="info">
          <div class="total">
            <span class="remind">上线状态:</span>
            <span :class="!currentReq.online && 'selected'" @click="checkOnline({online: ''})">全部库存({{total}})</span>
            <span :class="currentReq.online === '1' && 'selected'" @click="checkOnline({online: '1'})">已上线库存({{total_online}})</span>
            <span :class="currentReq.online === '0' && 'selected'" @click="checkOnline({online: '0'})">待上线库存({{total_offline}})</span>
          </div>
        </div>
        <div class="ctrl">
          <el-button class="refresh" type="success" v-once
            :loading="fLoading"
            @click="refresh">刷新</el-button>
          <el-button class="save" type="primary" v-once
            :loading="sLoading"
            @click="save">保存</el-button>
        </div>
      </div>
      <h-table />
    </div>
  </div>
</template>

<script>
import search from "./search.vue";
import hTable from "./table.vue";
import Vuex from "vuex";

export default {
  components: {
    search,
    hTable
  },
  data() {
    return {
      fLoading: false,
      sLoading: false
    };
  },
  computed: {
    ...Vuex.mapState(["userInfo"]),
    ...Vuex.mapState("hub", [
      "agency",
      "total",
      "total_online",
      "total_offline",
      "currentReq"
    ])
  },
  mounted() {
    this.aUserInfo();
  },
  methods: {
    ...Vuex.mapActions(["aUserInfo"]),
    ...Vuex.mapMutations("hub", ["updateCurrentReq"]),
    ...Vuex.mapActions("hub", ["aList", "edit"]),
    refresh() {
      this.fLoading = true;
      this.aList().then(() => (this.fLoading = false));
    },
    save() {
      this.sLoading = true;
      this.edit({ item: {}, closeMum: true }).then(
        () => (this.sLoading = false)
      );
    },
    search(query) {
      this.aList();
    },
    searchChange(query) {
      this.updateCurrentReq({ query, page: 1 });
      if (query.length < 1) this.aList(); // 如果输入框字数为 0，默认请求一次
    },
    checkOnline(payload) {
      this.updateCurrentReq({ online: payload.online, page: 1 });
      this.aList();
    }
  }
};
</script>

<style lang="less" scoped>
.hub-container {
  display: flex;
  flex-direction: column;
  align-items: center;

  @sColor: #0063ff;

  div {
    color: #333;
    font-size: 14px;
  }

  .title-container {
    display: flex;
    justify-content: center;
    width: 100%;
    background-color: white;
    box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.24);
    border-radius: 2px;
    z-index: 2;

    .title {
      position: relative;
      display: flex;
      align-items: center;
      width: 1024px;
      height: 60px;

      .t-name {
        font-size: 20px;
        color: #0076ff;
        margin: 0 50px 0 20px;
      }

      .t-company {
        font-size: 14px;
        color: #333;
      }

      .t-hub {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 70px;
        height: 32px;
        margin-left: 40px;
        font-size: 14px;
        // color: #20a0ff;
        // border: 1px solid #20a0ff;
        border-radius: 4px;
        // cursor: pointer;
      }
    }
  }

  .h-content {
    background: white;

    .total-info {
      display: flex;
      justify-content: space-between;
      align-items: center;
      width: 1024px;
      height: 50px;
      background: white;

      .info {
        display: flex;
        flex-direction: column;

        .user {
          margin-left: 10px;
          margin-bottom: 10px;

          span {
            margin-left: 8px;
          }
        }

        .total {
          margin-left: 20px;

          span {
            margin-right: 40px;
            text-decoration: underline;
            cursor: pointer;
          }

          .selected {
            color: @sColor;
          }

          .remind {
            margin: 0 10px;
            color: #9b9b9b;
          }
        }
      }

      .ctrl {
        margin-right: 10px;

        button {
          width: 80px;
          border-radius: 4px;
          color: white;
          font-size: 14px;
          padding: 8px 10px;
        }

        .save {
          background: @sColor;
          border-color: @sColor;
        }
      }
    }
  }
}
</style>
