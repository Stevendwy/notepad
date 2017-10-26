##js 本地图片上传
 <!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title></title>
    </head>
    <body>
        <input accept="image/*" name="upimage" id="upload_file" type="file">
        <textarea id="base64_output" name="Word" style=" width:820px"></textarea>
        <script type="text/javascript">
            document.getElementById("upload_file").onchange = function () {
                gen_base64();
            };
            function $_(id) {
                    return document.getElementById(id);
            }
            function gen_base64() {
                var file = $_('upload_file').files[0];
                r = new FileReader();  //本地预览
                r.onload = function(){
                    $_('base64_output').value = r.result;
                }
                r.readAsDataURL(file);    //Base64
            }
        </script>
    </body>
</html>

//解决本地上传base64 上传方式