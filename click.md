##click

click 携带 300 延迟，用blue 优雅处理时候将setTimeout() 延时大于300
blur() {
        // console.log('blur')
        //延时优雅处理 blur
        setTimeout(() => this.closeHistorys(), 400)
    }