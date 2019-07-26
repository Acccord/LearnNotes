## WebView相关

### header传参
WebView原生的api里边有post参数的api
```
//post是一个byte[]  
webview.postUrl(url,post) ;
```
添加header的Api有
```
//headers是一个map
webview.loadUrl(url,headers);
```
这两个Api只能单独使用,不能两个同时使用;



###
