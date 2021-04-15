# jsPDF-html2canvas
純前端pdf 辦法

method_1參考：https://www.mdeditor.tw/pl/2A2Q/zh-tw

method_2參考：https://www.uj5u.com/qiye/181610.html

使用html2canvas產生圖片，並用 jsPDF 輸出PDF

使用到CDN

```html
<script src="https://html2canvas.hertzen.com/dist/html2canvas.min.js"></script>
<script src="https://unpkg.com/jspdf@latest/dist/jspdf.umd.min.js"></script>
```

以下兩個地方，解決輸出後有灰底區塊及調整輸出長寬

```javascript
//獲取元素寬高 讓其以一個規律或者固定寬高伸展
width: w + 120,
height: h + 250,
//將截圖移入中心位置
scrollX: 0,
scrollY: 100,
```

```javascript
//a4紙的尺寸[595.28,841.89]，html頁面生成的canvas在pdf中圖片的寬高
var imgWidth = 625.28;
var imgHeight = (610.28 / contentWidth) * contentHeight;
```

儲存檔案時，支援Callback function

pdf.save("test.pdf", { returnPromise: true }).then(alert("PDF render all done!"));