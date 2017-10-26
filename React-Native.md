##React-Native
###配置完整的开发环境后

**参考文章地址**
    *http://blog.csdn.net/Cloudox_/article/details/52386495*

**脚手架**
    
    npm install -g react-native-cli
 
**创建新项目，项目名称为 Test**
    react-native init Test
    //注释：创建时间会下载相关依赖，时间较长
    
**执行**
    
    IOS 执行：
        react-native run-ios
        或者：XCode 执行
            双击ios 目录中 Test.Xcodeproj 文件，在打开Xcode 开发环境后点击 Run
            
    Android 执行
        //1.开启安卓模拟器或者连接真机，真机设置为调试模式
        adb devices
        //2.开始一个命令控制台，进入项目目录,该命令是开启jsbundle 服务器，用于测试Reload.js 的服务器
        cd 到该项目下后 执行react-native start
        //3.再开启一个新的命令行控制器，进入项目目录
        react-native run-android
        
**调试**
    
    可以通过摇晃设备或者选择ios 模拟器的Hardware 菜单中 ‘Shake Gesture’ 来打开开发菜单。运行于iphone 模拟器时候使用 Command + D 快捷键，运行Android 模拟器时使用 Command + M 快捷键
    //注意：在(release/producation builds) 中开发者菜单会关闭
    
**刷新JavaScript**

    不用每次都重新编译app ，可以直接重载JavaScript 代码，就选择菜单中Reload 。也可以在ios 模拟器中 Command+R 或者在Android 模拟器中按两次 R。
    
    如果Command+R快捷键没能重载iOS模拟器，去往Hardware菜单，选择Keyboard，然后确保“Connect Hardware Keyboard”是勾选的。
    
**自动重载**
    
    自动重载可以在开发者菜单中选择 'Enable Live Reload' 来打开
    
    更进一步想在添加新文件到 JAVASCRIPT 包中时保持App 运行新的版本。可以选择开发者菜单中 ‘Enable Hot Reloading’ 来打开。
    
    有一些热重载无法完美实现的情况。如果运行到了任何问题，使用全重载来重置你的app。