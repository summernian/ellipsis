# ellipsis
多行文本的文字溢出及省略号显示，文本未超出则不显示溢出，兼容写法纯CSS
 
### 已有文本框P标签
文本结构 ：
```

<div class='ellipsis'>
	<p>这里是一大堆可能会造成多行溢出的文字</p>
</div>

```
 
### 设置属性
 
```
.ellipsis {
	overflow: hidden;//这是溢出文字隐藏，宽度可以在这里设置，也可以直接继承父级的宽度，建议继承
	height: 82px;//这是文本框的高度和间距 lineHight * 3 + marginTop
	line-height: 24px;// 82px - 24px * 3 = 10px, marginTop为10px，高度和行高决定产生几行文本 
}

.ellipsis:before {
	content: '';
	float: left;
	width: 5px;
	height: 82px;//这个高度要与文本框的高度一致，其他样式不改动
}

.guide_tabbox dl dd .ellipsis > *:first-child {//这就是原文本框p标签的属性设置
	float: right;
	width: 100%;
  margin-left:-5px;//以上三条是必须加的属性，不需要加高度，高由内容撑开，私有属性可以在下面设置
	margin-top:10px; //若没有margin就不用加，与前面的marginTop保持一致
	color:#818181; //设置文本颜色
}

.ellipsis:after {
	content: "\02026";//省略号，兼容样式，以下样式皆保持一致不用改动
	box-sizing: content-box;
	-moz-box-sizing: content-box;
	-webkit-box-sizing: content-box;
	
	float: right;
	position: relative;
	top: -25px;
	left: 100%;
	width: 3em;
	margin-left: -3em;
	padding-right: 5px;
	
	text-align: right;
	background-size: 100% 100%;
  /* 512x1 image, gradient for IE9. Transparent at 0% -> white at 50% -> white at 100%.*/
	background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAgAAAAABCAMAAACfZeZEAAAABGdBTUEAALGPC/xhBQAAAwBQTFRF////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////AAAA////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////wDWRdwAAAP90Uk5TgsRjMZXhS30YrvDUP3Emow1YibnM9+ggOZxrBtpRRo94gxItwLOoX/vsHdA2yGgL8+TdKUK8VFufmHSGgAQWJNc9tk+rb5KMCA8aM0iwpWV6dwP9+fXuFerm3yMs0jDOysY8wr5FTldeoWKabgEJ8RATG+IeIdsn2NUqLjQ3OgBDumC3SbRMsVKsValZplydZpZpbJOQco2KdYeEe36BDAL8/vgHBfr2CvTyDu8R7esU6RcZ5ecc4+Af3iLcJSjZ1ivT0S/PMs3LNck4x8U7wz7Bv0G9RLtHuEq1TbJQr1OtVqqnWqRdoqBhnmSbZ5mXapRtcJGOc4t2eYiFfH9AS7qYlgAAARlJREFUKM9jqK9fEGS7VNrDI2+F/nyB1Z4Fa5UKN4TbbeLY7FW0Tatkp3jp7mj7vXzl+4yrDsYoVx+JYz7mXXNSp/a0RN25JMcLPP8umzRcTZW77tNyk63tdprzXdmO+2ZdD9MFe56Y9z3LUG96mcX02n/CW71JH6Qmf8px/cw77ZvVzB+BCj8D5vxhn/vXZh6D4uzf1rN+Cc347j79q/zUL25TPrJMfG/5LvuNZP8rixeZz/mf+vU+Vut+5NL5gPOeb/sd1dZbTs03hBuvmV5JuaRyMfk849nEM7qnEk6IHI8/qn049hB35QGHiv0yZXuMdkXtYC3ebrglcqvYxoj1muvC1nDlrzJYGbpcdHHIMo2FwYv+j3QAAOBSfkZYITwUAAAAAElFTkSuQmCC);
  
  background: -webkit-gradient(linear, left top, right top,from(rgba(255, 255, 255, 0)), to(white), color-stop(50%, white));
  background: -moz-linear-gradient(to right, rgba(255, 255, 255, 0), white 50%, white);           
  background: -o-linear-gradient(to right, rgba(255, 255, 255, 0), white 50%, white);
  background: -ms-linear-gradient(to right, rgba(255, 255, 255, 0), white 50%, white);
  background: linear-gradient(to right, rgba(255, 255, 255, 0), white 50%, white);
```
over
