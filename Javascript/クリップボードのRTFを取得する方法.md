# クリップボードのRTFを取得する方法

ExcelでコピーしたRTFをJavascriptを取得する方法を調べたのでメモ

```html
<html>
<head>
</head>
<body>
<textarea id="paste_area"></textarea>
<div id="rtf" ></div>

<script>
function pasteIntercept(e) {
        let rtf = e.clipboardData.getData('text/rtf')
        document.getElementById('rtf')
                .appendChild(document.createTextNode(rtf + "\n"));

}
document.getElementById("paste_area").addEventListener("paste", pasteIntercept);
</script>

</body>
</html>
```

ポイントは
- `onpaste` イベントを使う
- `e.clipboadData.getData('text/rtf)` で rich text を取得できる
