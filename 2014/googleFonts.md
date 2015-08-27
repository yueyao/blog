使用 @font-face 引入你喜欢的字体
---------------

###原理
`CSS3的自定义字体@font-face` 规则的工作原理

使用` @font-face `规则初看起来非常简单。从本质上看，它只需要两个步骤。 首先，使用 ` @font-face `规则链接到在一个 Web 服务器上托管的字体。 然后，在 CSS 规则中的 `font-family` 属性中使用该字体。 非常简单。

###一些问题
你需要准备该字体在 Mac 和 Windows 计算机上正确显示字母或在所有 Web 浏览器中运行所需的所有变体(如下)。
	如果需要支持所有平台，你需要：
	
	 @font-face {
        font-family: 'uxiconfont';
        src: url('uxiconfont.eot'); /* IE9*/
        src: url('uxiconfont.eot?#iefix') format('embedded-opentype'), /* IE6-IE8 */
             url('uxiconfont.woff') format('woff'), /* chrome、firefox */
             url('uxiconfont.ttf')  format('truetype'), /* chrome、firefox、opera、Safari, Android, iOS 4.2+*/
             url('uxiconfont.svg#uxiconfont') format('svg'); /*  iOS 4.1- */
		}
###icon-font支持状况
1. IE：从IE4开始支持eot格式，IE9开始支持woff。
2. webkit/safari：支持TrueType/OpenType(.ttf)，OpenType PS(.otf)，iOS4.2+支持.ttf，iOS 4.2以下只支持SVG字体； Safari5.1+ 开始支持woff格式
3. Chrome：除webkit支持的以外，从Chrome 6开始，开始支持woff格式；
4. Firefox：支持.ttf和.otf，从Firefox 3.6开始支持woff格式；
5. Opera：支持.ttf、.otf、.svg。 Opera 11开始支持woff；
6. iPad, iPhone and Android 3.0+ 支持SVG fonts。

###使用 Google Web Fonts
[官网](www.google.com/webfonts)
1. 您喜欢的字体，然后单击右下角字体名称下的 Quick-use 链接
2. 挑选你希望展示的样式 

	1. Choose the styles you want:
		Varela Round
			Normal 400
3. 紧接着下面会给出如何引用这些链接
3种方式，link的方式最简单：
	
	`<link href='http://fonts.googleapis.com/css?family=Alegreya+Sans' rel='stylesheet' type='text/css'>`
4. 然后它会给出示例 如何调用
	
		font-family: 'Alegreya Sans', sans-serif;