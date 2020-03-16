# 下载base64图片

```javascript
// base64转blob
export function base64ToBlob(code) {
  let parts = code.split(';base64,');
  let contentType = parts[0].split(':')[1];
  let raw = window.atob(parts[1]);
  let rawLength = raw.length;

  let uInt8Array = new Uint8Array(rawLength);

  for (let i = 0; i < rawLength; ++i) {
    uInt8Array[i] = raw.charCodeAt(i);
  }
  return new Blob([uInt8Array], { type: contentType });
}
```

```javascript
// 下载base64图片
export function downloadBase64Img(fileName = 'QRcode.jpg', content) {
  if (!content) return;
  let aLink = document.createElement('a');
  let blob = base64ToBlob(content); // new Blob([content]);
  let evt = document.createEvent('HTMLEvents');
  evt.initEvent('click', true, true);// initEvent 不加后两个参数在FF下会报错  事件类型，是否冒泡，是否阻止浏览器的默认行为
  aLink.download = fileName;
  aLink.href = URL.createObjectURL(blob);
  aLink.dispatchEvent(new MouseEvent('click', { bubbles: true, cancelable: true, view: window }));// 兼容火狐
}
```



# 下载Excel文件

```javascript
export function downLoadXls(data, filename) {
  if (typeof window.chrome !== 'undefined') {
    // Chrome version
    let link = document.createElement('a');
    link.href = window.URL.createObjectURL(data);
    link.download = filename;
    link.click();
  } else if (typeof window.navigator.msSaveBlob !== 'undefined') {
    // IE version
    const blob = new Blob([data], { type: 'application/force-download' });
    window.navigator.msSaveBlob(blob, filename);
  } else {
    // Firefox version
    const file = new File([data], filename, { type: 'application/force-download' });
    window.open(URL.createObjectURL(file));
  }
}
```

