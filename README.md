# InterestCss
实现一些有趣的纯css效果

## 动态颜色渐变充电效果
<img src="./EffectPicture/1.gif">
```css
background-image: linear-gradient(rgba(calc(255 - var(--progress) * 1.4),calc(var(--progress) * 2.5),calc(var(--progress) * 1.8)) calc(100% - calc(var(--progress) * 1%)), lime 0%);
background-clip: text;
-webkit-background-clip: text;
/* clamp的原理：最小值，可适应值、最大值
	calc计算当前的值  使用变量progress 除 100 得到一个小数
	然后用当前小数减0.99 0.01~0.98减0.99都是负数 负数则默认使用最小值1
	当相减的值不是负数  再乘以两百，就会得到一个很大的值，这个值超出了最大值的1.3的范围
	则会使用最大限度值1.3  
*/
transform: scale(clamp(1, calc(((var(--progress) / 100) - 0.99) * 200), 1.3));
```

