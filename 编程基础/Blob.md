### 1. Blob 定义

> 一直以来，js都没有比较好的方法处理二进制的方法。而blob的存在，允许我们可以通过js直接操作二进制数据。

```tet
一个Blob对象就是一个包含只有只读原始数据的类文件对象。
```

```tex
Blob对象可以看作是存放二进制数据的容器，此外还可以通过blob设置二进制数据的MIME类型。
```

### 2. 创建Blob

```javascript
var blob = new Blob(dataArr:Array<any>, opt: {type: string});
```

- dataArray: 数组，包含了要添加到blob对象中的数据，数据可以是任意多个ArrayBuffer、ArrayBufferView、Blob、或者DOMString对象。
- opt：对象，用于设置Blob对象的属性（如：MIME类型）。

### 3. Blob.slice()

此方法返回一个新的Blob对象，包含了原Blob对象中指定范围内的数据。

```javascript
Blob.slice(start:number,end:number,contentType: string)
```

- start: 开始索引，默认为0
- end: 截取结束索引（不包含end）
- contentType: 新Blob的MIME类型，默认为空字符串

### 4. canvas.toBlob()

```js
const canvas = document.getElementById("canvas");
canvas.toBlob(function(blob) {
    console.log(blob);
});
```

### 5. 应用场景

File接口基于Blob，继承了Blob的功能并进行了扩展，故我们可以像使用Blob一样使用File对象。

#### **分片上传**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>分片下载</title>
</head>
<body>
<input type="file" id="file"/>
<script type="text/javascript">
    function initUpload() {
        const chunk = 100 * 1024; // 每片大小
        const input = document.getElementById("file"); // input
        input.onchange = function (e) {
            const file = this.files[0];
            let query = {};
            const chunks = [];
            if (!!file) {
                let start = 0;
                for (let i = 0; i < Math.ceil(file.size / chunk); i++) {
                    let end = start + chunk;
                    chunks[i] = file.slice(start, end);
                    start = end;
                }
                
                query = {
                    fileSize: file.size,
                    dataSize: chunk,
                    nextOffset: 0
                };
                
                upload(chunks, query, successPerUpload);
            }
        }
    }
    
    function upload(chunks, query, cb) {
        const queryStr = Object.getOwnPropertyNames(query).map(key => {
            return key + "=" + query[key];
        }).join("&");
        const xhr = new XMLHttpRequest();
        xhr.open("open", "http://xxxx/upload?" + queryStr);
        xhr.overrideMimeType("application/octet-stream");
        
        const index = Math.floor(query.nextOffset / query.dataSize);
        getFileBinary(chunks[index], function (binary) {
            if (xhr.sendAsBinary) {
                xhr.sendAsBinary(binary);
            } else {
                xhr.send(binary);
            }
        });
        
        xhr.onreadystatechange = function (e) {
            if (xhr.readyState === 4) {
                if (xhr.status === 200) {
                    let resp = JSON.parse(xhr.responseText);
                    // resp = {
                    //     isFinish: false,
                    //     offset: 100 * 1024
                    // };
                    if (typeof cb === "function") {
                        cb.call(this, resp, chunks, query);
                    }
                }
            }
        }
    }
    
    // 每片上传成功后执行
    function successPerUpload(resp, chunks, query) {
        if (resp.isFinish === true) {
            alert("上传成功");
        } else {
            // 未上传完毕继续上传
            query.offset = resp.offset;
            upload(chunks, query, successPerUpload)
        }
    }
    
    // 获取文件二进制数据
    function getFileBinary(file, callback) {
        let reader = new FileReader();
        reader.readAsArrayBuffer(file);
        reader.onload = function (e) {
            if (typeof callback === "function") {
                callback.call(this, this.result);
            }
        }
    }
    
    initUpload();
</script>
</body>
</html>
```

通过Blob.slice方法，可以将大文件分片，轮巡向后提交各文件片段，即可实现文件的分片上传。

分片上传逻辑如下：

- 获取要上传的File对象，根据chunk（每片大小）对文件进行分片。
- 通过post方法轮循上传每片文件，其中url中拼接quertString用于描述当前上传的文件信息；post body中存放本次要上传的二进制数据片段。
- 接口每次返回offset，用于执行下次上传。

#### **通过url下载文件**

window.URL对象可以为blob对象生成一个网路地址，结合a标签的download属性，可以实现点击url下载文件。

```js
createDownload("download.txt","download file 123");

function createDownload(fileName, content) {
	let	blob = new Blob([content]);
    let link = document.createElement("a");
    link.innerHTML = fileName;
    link.download = fileName;
    link.href = URL.createObjectURL(blob);
    document.body.appendChild(link);
}
```

#### **通过url显示图片**

img的url属性，都可以通过接收图片的网络地址或base64来显示图片，同样的，也可以把图片转化为Blob对象，生成URL(URL.createObjectURL(blob)),来显示图片。

```html
<img src="blob:null/6144bb9b-abc4-4181-afaa-11bf935e9b9d">
```

使用blob url的好处在于可以在一定程度上干扰爬虫。











































































































