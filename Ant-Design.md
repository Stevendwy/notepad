##ant-design 

    npm install dva-cli -g
    dva new myapp
    cd myapp
    npm start
    
###真实环境下开发
    
*步骤如下：*
    
     Install dva-cli
    Create New App
    Integrate antd
    Define Router
    Write UI Components
    Define Model
    Connect
    Build
    What's Next    

**Install dva-cli**
    
>npm install dva-cli -g
>
>dva -v

**Create New App**

>dva new objname
>
>cd objname
>
>npm start

    following output:
    Compiled successfully!

    The app is running at:
    
      http://localhost:8000/
    
    Note that the development build is not optimized.
    To create a production build, use npm run build.
    
    open http://localhost:8000 will see dva welcome page
     
**integrate antd**

>npm install antd babel-plugin-import --save
>
    
    Edit .roadhogrc to integrate babel-plugin-import 
    
    "extraBabelPlugins": [
    -    "transform-runtime"
    +    "transform-runtime",
    +    ["import", { "libraryName": "antd", "style": "css" }]
      ],