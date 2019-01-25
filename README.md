# jq_slideImage
**使用**
```
          var mySlideImage = new SlideImageVerify('#slideImageWrap',{
            slideImage:['image/0034034888570098_b.jpg','image/1155116361608498_b.jpg','image/b6d5128741fee79a077f9e72a36797cc.jpg'],
            slideAreaNum:1,
            refreshSlide:true,
            getSuccessState:function (res) {
                console.log(res);
            }
          })
```

**参数**

| slideImage |       图片的src,可以为一个图片的src,也可以是多张图片的 src 数组 |
|--|--|
| slideAreaNum |  误差范围 +- 5   默认5   number|
| refreshSlide | 是否需要刷新按钮 默认true  Booleans|
| getSuccessState|成功回调  返回true   Function|
| initText|初始展示的提示文字 默认“向右滑动完成拼图” str|

重置方法

```
	resetSlide()

	//mySlideImage.resetSlide();
```
调整尺寸

```
	resizeSlide()
	//mySlideImage.resizeSlide();
	window.onresize = function () {
            mySlideImage.resizeSlide();
	}
	//有个问题是  会闪烁 ，暂时没处理好，一般正常用的话，不会用到需要实时根据屏幕调整尺寸的
```
注：需要给初始dom设置宽高或百分百，（不设的话，会默认宽300 高190（减去滑动条的高度，图片有150高）），样式需要自己覆盖修改，或者在源码里面搜索 修改
```
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
		<script src="jquery.min.js" type="text/javascript" charset="utf-8"></script>
		<script src="jq_slideImage.js" type="text/javascript" charset="utf-8"></script>
		<style>
			.demo1{
				width: 100%;
				height: 300px;
			}
			.demo2{
				width: 300px;
				height: 200px;
			}
		</style>
	</head>
	<body>
		<div class="demo1" id="slideImageWrap">
	        
	    </div>
	    <button id="reset-one">
	        重置test1
	    </button>
	
	    <div class="demo2" id="slideImageWrap2">
	
	    </div>
	    <button id="reset-two">
	        重置test2
	    </button>
    <script>
    	//实1
        var mySlideImage = new SlideImageVerify('#slideImageWrap',{
            slideImage:['image/0034034888570098_b.jpg','image/1155116361608498_b.jpg','image/b6d5128741fee79a077f9e72a36797cc.jpg'],
            slideAreaNum:1,
            refreshSlide:true,
            getSuccessState:function (res) {
                console.log(res);
            }
        })
        $("#reset-one").on('click',function () {
            mySlideImage.resetSlide();
        })
        window.onresize = function (ev) {
            mySlideImage.resizeSlide();
        }
        
        //实2
        var mySlideImage2 = new SlideImageVerify('#slideImageWrap2',{
            slideImage:'image/d98ad358f746d8936c7e24dad895f52b.jpg',
            slideAreaNum:20,
            refreshSlide:false,
            getSuccessState:function (res) {
                console.log(res);
            }
        })
        
        $("#reset-two").on('click',function () {
            mySlideImage2.resetSlide();
        })
        
    </script>
	</body>
</html>

```
