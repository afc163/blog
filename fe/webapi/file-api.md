# Exsample code

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Test Index</title>
    <!-- <link rel="stylesheet" href="dist/css/base.css"> -->
    <script>
        window.onload = function () {
            var fileInput = document.querySelector('#file'),
                info = document.querySelector('#info'),
                preview = document.querySelector('#preview');
            fileInput.onchange = function () {
                var file = fileInput.files[0],
                    fileName = file.name,
                    fileSize = file.size,
                    fileType = file.type;
                if (fileType.indexOf('image') == -1) {
                    alert('您选择的不是图片！请重试');
                    return;
                }
                info.innerHTML = '文件名：' + fileName + '<br />'
                    + '文件大小：' + fileSize + '<br />'
                    + '文件类型：' + fileType;

                var reader = new FileReader();
                reader.onload = function (e) {
                    var data = e.target.result;
                    preview.style.backgroundImage = 'url(' + data + ')';
                }
                reader.readAsDataURL(file);
            }

        }
    </script>
</head>

<body>
    <form action="">
        <div> <input type="file" id="file"></div>
        <div id="info"></div>
    </form>
    <div id="preview" style="width:100%;height:200px;border:1px solid gray"></div>
</body>

</html>
```