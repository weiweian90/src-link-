# src-link-
src和link的区别
 之前在修改联通网上营业厅密码，查看源码时，注意到多个js文件通过一个script引入
 `<script src="/cust/js/??esf/jquery-1.7.2.min.js,esf/jquery.json-2.2.min.js,esf/core.js,esf/jq-overlay.js,custweb/resetpwd/resetpwd.js,common/progress.js,common/jquery.mouseDelay.min.js,common/jquery.cookie.min.js,component/ValidateUtils.js,component/aircity.js,component/cityAutoComplete.js,component/suggest.js,component/mails.js,component/loginmailsuggest.js,component/mailsuggest.js" language="javascript" type="text/javascript"></script>`
 在页面看来，其实只是一个js文件。？？后面的参数表示这个请求实际上是一个后台处理程序，，由后台（服务器）程序将多个js文件或css文件打包成一个response，由此减少页面请求数量
 
# 由此引发对link和src的思考
 js，css文件作为外部文件可以通过script， link引入，为什么引入的方式会不一样
 
 src和href之间存在区别，能混淆使用。src用于替换当前元素，href用于在当前文档和引用资源之间确立联系。
src是source的缩写，指向外部资源的位置，指向的内容将会嵌入到文档中当前标签所在位置；在请求src资源时会将其指向的资源下载并应用到文档内，例如js脚本，img图片和frame等元素。
  
  `<script src ="js.js"></script>`  
  
当浏览器解析到该元素时，会暂停其他资源的下载和处理，直到将该资源加载、编译、执行完毕，图片和框架等元素也如此，类似于将所指向资源嵌入当前标签内。这也是为什么将js脚本放在底部而不是头部。
href是Hypertext Reference的缩写，指向网络资源所在位置，建立和当前元素（锚点）或当前文档（链接）之间的链接，如果我们在文档中添加
  
  `<link href="common.css" rel="stylesheet"/>`  
  
那么浏览器会识别该文档为css文件，就会并行下载资源并且不会停止对当前文档的处理。这也是为什么建议使用link方式来加载css，而不是使用@import方式。
 
