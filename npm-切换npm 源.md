##npm-切换npm 源

nrm  是一个npm 源管理器，允许快速切换 npm源

安装： npm install -g nrm

列出可用源：    nrm ls
    
    * npm ---- https://registry.npmjs.org/
      cnpm --- http://r.cnpmjs.org/
      taobao - http://registry.npm.taobao.org/
      eu ----- http://registry.npmjs.eu/
      au ----- http://registry.npmjs.org.au/
      sl ----- http://npm.strongloop.com/
      nj ----- https://registry.nodejitsu.com/

带 * 为当前使用源 

切换 切换到 taobao
    nrm use taobao
    
    Registry has been set to: http://registry.npm.taobao.org/

增加源
    nrm add <registry> <url> [home]

删除源
    nrm del <registry> 
测试源速度
    nrm test

许可
    nrm 为开源 使用 MIT 许可  

》参考于： https://github.com/Pana/nrm