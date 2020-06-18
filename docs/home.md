# Java开发手册

> Java开发手册在线文档版



**感谢世界上最好的编程语言JAVA**

####  点击切换主题
<div class="demo-theme-preview">
  <a data-theme="vue">vue.css</a>
  <a data-theme="buble">buble.css</a>
  <a data-theme="dark">dark.css</a>
  <a data-theme="dolphin">dolphin.css</a>
</div>


<style>
  .demo-theme-preview a {
    padding-right: 10px;
  }
 .demo-theme-preview a:hover {
    cursor: pointer;
    text-decoration: underline;
  }
</style>

<script>
  var preview = Docsify.dom.find('.demo-theme-preview');
  var themes = Docsify.dom.findAll('[rel="stylesheet"]');
  preview.onclick = function (e) {
    var title = e.target.getAttribute('data-theme')
	themes.forEach(function (theme) {
      theme.disabled = theme.title !== title
    });
  };
</script>