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









































































































