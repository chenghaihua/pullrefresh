# pullrefresh
H5下拉刷新上拉加载更多使用教程

1.在页面上添加两个元素<br>
&lt;div id="demo"&gt;&lt;div style="text-align:center"&gt;正在加载中...&lt;/div&gt;&lt;/div&gt;<br>
&lt;div class="x-pullfresh-more"&gt;加载更多&gt;/div&gt;

2.加载数据方法<br>
pullrefresh.doRefresh({<br>
&nbsp;&nbsp;&nbsp;&nbsp;debug: true,		 // 模拟真实请求数据，否则会出现ajax跨域，正式使用中请去h5.js中删除debug代码<br>
&nbsp;&nbsp;&nbsp;&nbsp;url: './list.json',  // 必填，ajax加载数据请求的地址<br>
&nbsp;&nbsp;&nbsp;&nbsp;data: {size: 20},   // 非必填，ajax请求数据的参数，如果启用了缓存，将影响浏览器的缓存数据<br>
&nbsp;&nbsp;&nbsp;&nbsp;dataType: "json",   // 非必填，ajax请求返回的数据类型<br>
&nbsp;&nbsp;&nbsp;&nbsp;container: '#demo', // 非必填，用于计算document.body.scrollTop等于多少时自动加载更多数据<br>
&nbsp;&nbsp;&nbsp;&nbsp;cache: 'test',	    // 非必填，如果不想让浏览器缓存请写false，否则请写唯一的标记，具体请观察sessionStorage<br>
&nbsp;&nbsp;&nbsp;&nbsp;success: function(list, page, size){ // ajax请求成功后服务端返回来的数据<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;// 在此处理服务器返回的数据，绑定到demo元素中<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return true; // 返回true表示还有更多数据;返回false表示没有更多数据了我通常写return list.length >= size<br>
&nbsp;&nbsp;&nbsp;&nbsp;}<br>
});

3.引用样式
<br>***下拉刷新样式***
<br>.x-pullfresh-wrapper{position:fixed;left:0;top:-42px;width:100%;height:42px;margin:0 auto;z-index:10;opacity:0}
<br>.x-pullfresh-wrapper .x-pullfresh-loading{position:relative;width:40px;height:40px;overflow:hidden;background-color:rgba(255,255,255,0.9);border:1px solid rgba(230,230,230,0.5);border-radius:36px;margin:0 auto;text-align: center;line-height: 40px;-webkit-transition: all 1s;-moz-transition:all 1s;-o-transition:all 1s;}
<br>.x-pullfresh-wrapper .x-pullfresh-canvas{margin:4px 4px}
<br>.x-pullfresh-wrapper .x-pullfresh-svg.x-on,.x-pullfresh-wrapper .x-pullfresh-canvas.x-on{-webkit-animation:loading 1s linear infinite;-webkit-transform:rotate(0);animation:loading 1s linear infinite;transform:rotate(0)}
<br>.x-pullfresh-wrapper .x-pullfresh-svg{width:100%;height:100%}
<br>.x-pullfresh-wrapper .x-pullfresh-path{stroke-linecap: round;stroke: rgb(52, 190, 51);fill: none;stroke-width: 1px;}
<br>.x-pullfresh-wrapper #x-pullfresh-arrow path{fill: rgb(52, 190, 51);}
<br>***更多数据样式***
<br>.pullfresh-up{line-height:30px;overflow:hidden;text-align:center;transition-duration:600ms;margin-bottom:20px}
<br>.pullfresh-up .loader{font-size:0px;padding:0px;display:none}
<br>.pullfresh-up .loader span{vertical-align:middle;border-radius:100%;display:inline-block;width:10px;height:10px;margin:0 2px;-webkit-animation:pfloader 0.8s linear infinite alternate;animation:pfloader 0.8s linear infinite alternate}
<br>.pullfresh-loading .loader{display:block}
<br>.pullfresh-up .pullfresh-label{font-size:12px;color:#999;display:none}
<br>.pullfresh-up.no-more .pullfresh-label{display:block}
<br>.no-more .pullfresh-label{display:block}
<br>.pullfresh-up .loader span:nth-child(1){-webkit-animation-delay:-1s;animation-delay:-1s;background:rgba(245,103,115,0.6)}
<br>.pullfresh-up .loader span:nth-child(2){-webkit-animation-delay:-0.8s;animation-delay:-0.8s;background:rgba(245,103,115,0.8)}
<br>.pullfresh-up .loader span:nth-child(3){-webkit-animation-delay:-0.26666s;animation-delay:-0.26666s;background:rgba(245,103,115,1)}
<br>.pullfresh-up .loader span:nth-child(4){-webkit-animation-delay:-0.8s;animation-delay:-0.8s;background:rgba(245,103,115,0.8)}
<br>.pullfresh-up .loader span:nth-child(5){-webkit-animation-delay:-1s;animation-delay:-1s;background:rgba(245,103,115,0.4)}
<br>@keyframes pfloader{from{transform:scale(0,0)}
<br>to{transform:scale(1,1)}
<br>}@-webkit-keyframes pfloader{from{-webkit-transform:scale(0,0)}
<br>to{-webkit-transform:scale(1,1)}
<br>}
