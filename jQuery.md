# jQuery笔记

## jQuery的特点
- jQuery是一个简单快速的Javasc代码库，他不是一种新的语言，也不能取代JS，他能帮助我们简单快速的使用JS。
- 他有优质的选择器和筛选器
- 方便的隐式迭代
- 强大的链式编程

## 两个入口函数：

### Javascript入口函数：
```js
window.onload = function(){
    //....
}
```
> Javascript的onload事件是等到所有内容，包括外部图片之类的文件全部加载完成后才会执行。且只会执行一次，如果执行多次前面的就会被后面的覆盖掉。

### jQuery入口函数：
```js
$(document).ready(function(){
    //....
});
或者:
$(function(){
    //....
})
```
> jQuery的入口函数是在所有的html标签（DOM）全部加载完成后才会执行，并且可以执行多次，前面的不会被覆盖。

## jQuery选择器
> 通过jQuery选择器选择的对象是经过jQuery封装过后的对象，并不是js的原生对象，所以js对象的属性和方法不能用。
### 普通选择器
1. class选择器： $('.demo')
2. ID选择器：$('#demo')
3. 标签选择器：$('div')
4. 包含选择器：$('#demo p')
5. 子元素选择器： $('#demo>p')
6. 群组选择器：$('#demo, body, div')
7. 属性选择器： $('input[type=button]')
### 特殊选择器
1. $('#box:first')
2. $('#box:last')
3. $('#box:eq(3)')
4. $('#box:odd')
5. $('#box:even')
### 筛选方法
> 对选择器选获取到的一组标签对象进行筛选--便于链式编程
1. .first() 匹配第一个元素
2. .last() 匹配最后一个元素
3. .eq() 通过下标来选择第n个元素
4. .find() 匹配指定的后代元素
5. .children() 匹配指定的子元素
6. .prev() 匹配上一个兄弟元素
7. .prevAll() 匹配上面的所有兄弟元素
8. .next() 匹配下面的兄弟元素
9. .nextAll() 匹配下面所有的兄弟元素
10. .siblings() 匹配所有的兄弟元素，不管是上下
11. .parent() 匹配直接的父元素
12. .parents() 匹配所有的父元素
13. .filter() 筛选出与指定表达式相匹配的元素集合
14. .end() 回退操作


## jQuery的属性操作
1. prop()方法
> - 标签对象.prop(属性) ：获取指定属性的属性值
> - 标签对象.prop(属性，属性值) ：设定属性和属性值
> - 标签对象.prop(自定义属性，属性值) ：设定自定义属性和属性值
> 设置内置属性时，可以直接显示在标签上的为内置可见属性；设置自定义属性时，不会直接显示在标签上，为不可见的自定义属性。
2. attr()方法
> - 标签对象.attr(属性) ：获取指定属性的属性值
> - 标签对象.attr(属性，属性值) ：设定属性和属性值
> - 标签对象.attr(自定义属性，属性值) ：设定自定义属性和属性值
> 设置属性时，直接显示在标签上，为可见的内置或自定义属性
3. removeProp()方法
> 标签对象.removeProp(属性)  删除指定的属性，多用于自定义属性
4. removeAttr() 方法
> 标签对象.removeAttr(属性)  删除指定的属性

## jQuery的样式操作
1. .css()方法
> - 标签对象.css(属性) 获取指定属性的属性值
> - 标签对象.css(属性：属性值) 设定属性和属性值
> - 标签对象.css({属性：属性值}) 以对象的形式设定多个属性和属性值

## 标签对象的内容操作
1. .html()方法：效果类似于原生js中的innerHTML
> - 标签对象.html()  没有参数是获取标签内容
> - 标签对象.html(内容)  有参数是设定标签内容
2. .text()方法: 效果类似于原生js中的innerText
> - 标签对象.text()  没有参数是获取标签内容
> - 标签对象.text(内容)  有参数是设定标签内容

## 标签对象的class操作
1. .hasClass() 判断标签是否具有某个class，返回布尔值
2. .addClass() 添加css类名，可以添加多个
3. .removeClass()  删除类名，可以删除多个
4. .toggleClass() 判断当前标签是否具有某个class类名，如果有就删掉，没有就添加

## jQuery事件
1. 绑定事件：on()方法
> $('button').on('click', function(){})
2. 移除事件：off()方法
> $('button').on('click', handler)
> 
> $('button').off('click', handler)
3. 只执行一次的事件——one()方法
> $('button').one('click', handler)
4. 直接触发事件——trigger()方法
> 代码执行到这里的时候会自动触发button的click事件
> $('button').trigger('click')

## jQuery可以直接使用的事件 
1. .click()事件
```js
$('div').click(function(){
    console.log('我被点击了');
})
```
2. .dblclick()事件:直接给div绑定一个双击事件
```js
$('div').dblclick(function(){
    console.log('我被双击了');
})
```
3. scroll()事件
```js
$('div').scroll(function(){
    console.log('滚动触发事件');
})
```
4. hover()事件
> 这个事件包含两个事件处理函数，一个是移入的时候触发，一个是移除的时候触发，经过子级标签边界时不会触发
```js
$('div').hover(function(){
    console.log('移入的时候触发')
}, function(){
    console.log('移出的时候触发')
})
```
5. ready()事件
> jQuery的ready事件与window.onload事件有些相似。
> 相同点：都是在文件加载完成以后才执行程序
> 不同点：window.onload是当所有内容加载完成后包括图片显示完整，才会加载外部执行程序；ready是当标签结构加载完成后就会加载外部执行程序。

## jQuery阻止冒泡事件
```js
$('.inner').click(e=>{
    //通过事件对象，阻止冒泡事件
    e.stopPropagation();
    //通过return false，阻止冒泡事件
    return false;
})
```

## jQuery阻止默认事件
```js
$('form').click(e=>{
    //如果输入的内容不是crystal，就阻止表单提交
    if($('input').val() != 'crystal'){
        e.preventDefault();
        //通过return false阻止默认事件
        return false;
    }
})
```
**jQuery中的return false号称可以阻止一切**

## jQuery的隐式迭代
> 隐式——计算机程序自动默认执行的操作
> 迭代——此处指的是遍历循环操作
**jQuery会默认对数组中所有标签对象进行循环遍历，都执行相应操作**

## jQuery的元素操作
1. 创建元素
```js
//创建一个标签对象，同时可以定义标签的内容和属性等
var div = $('<div class="demo">我是一个div标签</div>');
```
2. 内部插入元素
```js
//向div中插入一个p元素，放在最后
$('div').append($('<p>hello</p>'));
//把p元素插入到div中去，放在最后
$('<p>hello</p>').appendTo($('div'));
```
3. 外部插入元素
```js
//在div后面插入一个p元素
$('div').after($('<p></p>'));

//在div前面插入一个p元素
$('div').before($('<p></p>'));

//把p元素插入到div元素的后面
$('div').insertAfter($('<p></p>'));

//把p元素插入到div元素的前面
$('div').insertBefore($('<p></p>'));
```
4. 替换元素
```js
//把div元素替换成P元素
$('div').replaceWith($('<p></p>'));

//用p元素替换掉div元素
$('<p></p>').replaceAll($('div'));
```
5. 删除元素
```js
//删除当前元素下的所有子节点
$('div').empty();

//把自己从页面中移出
$('div').remove();
```
6. 克隆元素
```js
//.clone()方法有连个参数，一个是false表示只是单纯的复制，其绑定的事件处理程序不会被复制，而true既克隆元素也克隆其绑定的事件。
$('li').cloen();//此时只是复制了li这一个元素
```

## jQuery的元素尺寸
1. 操作元素的宽和高
```js
//获取div元素内容区的高度，不包括padding和border
$('div').height();

//设置div内容区的高度为200像素
$('div').hieght(200);

//获取div元素内容区的宽度，不包括padding和border
$('div').width();

//设置div内容区的宽度
$('div').width(200);
```
2. 获取元素内置宽和高
```js
//获取div元素内置的高度，包括padding，不包括border
$('div').innerHeight();

//后去div元素内置的宽度，包括padding，不包括border
$('div').innerWidth();
```
3. 获取元素外置的高和宽
```js
//获取div元素外置的高，包括padding和border
$('div').outerHeight();

//获取div元素外置的高，包括padding和border还有margin
$('div').outerHeight(true);

//获取div元素外置的宽，包括padding和border
$('div').outerWidth();

//获取div元素外置的宽，包括padding和border还有margin
$('div').outerWidth(true);
```

## jQuery的元素位置
1. 元素相对页面的位置
```js
//获取元素相对于页面的位置
$('div').offset();
//得到一个对象：{left:值， top:值}

//设置当前元素相对于页面的位置
$('div').offset({left:100, top:100});
```
2. 获取相对父元素的偏移量
```js
//获取当前元素相对于父元素的偏移量（定位的值）
$('div').position();
//返回一个对象：{left:值, top:值}
```
3. 获取元素在滚动条滚动后的宽度和高度
```js
window.onscroll() = function(){
    //获取高度
    console.log($(window).scrollTop());
}

window.onscroll() = function(){
    //获取宽度
    console.log($(window).scrollLeft());
}
```

## jQuery的动画
1. show()显示动画
```js
//当元素本身是display：none的时候可以设置show让他显示出来
$('div').show();

//里面传递三个参数：
$('div').show(1000, 'linear', function(){
    console.log('显示完成');
});
```
2. hide()隐藏动画
```js
$('div').hide();
//如果当前元素是display：block则可以隐藏

$('div').hide(1000, 'liner', function(){
    console.log('隐藏完成');
})
```
3. toggle动画  显示隐藏动画
```js
$('div').toggle()
//如果元素本身显示，则隐藏；如果隐藏则显示

$('div').toggle(100, 'linear', function(){
    console.log('动画执行完毕');
})
//次方法也可以接受三个参数
```
4. slideDown动画  下拉显示
```js
$('div').slideDown();
//元素本身隐藏，此方法就可以让他下拉显示

$('div').slideDown(1000, 'linear', function(){
    console.log('动画执行完毕');
})
```
5. slideUp动画  上拉隐藏
```js
$('div').slideUp();
//上拉隐藏动画

$('div').slideUp(1000, 'linear', function(){
    console.log('动画执行完毕');
})
//此方法也可以接受三个参数
```
6. slideToggle动画  上下切换动画
```js
$('div').slideToggle();
//如果元素本身显示就上拉隐藏，否则就下拉显示

$('div').slideToggle(1000, 'lenear', function(){
    console.log('动画执行完毕');
})
```
7. fadeIn动画  逐渐显示动画
```js
$('div').fadeIn();
//给元素绑定逐渐显示动画

$('div').fadeIn(1000, 'linear', function(){
    console.log('动画执行完毕');
})
```
8. fadeOut动画  逐渐隐藏动画
```js
$('div').fadeOut();
//给元素绑定逐渐隐藏动画

$('div').fadeOut(1000, 'linear', function(){
    console.log('动画执行完毕');
})
```
9. fadeToggle动画  逐渐显示隐藏动画
```js
$('div').fadeToggle();

$('div').fadeToggle(1000, 'linear', function(){
    console.log('动画执行完毕');
})
```
10. fadeTo切换到指定透明度
```js
$('div').fadeTo('fast', .2, function(){
    console.log('动画执行完毕');
});
//让当前元素切换到指定透明度。里面有三个参数：speed(fast, normal, slow), opacity(0~1), 回调函数

$('div').fadeTo(1000, .2, 'linear', function(){
    console.log('动画执行完毕');
})
//感觉这两个方法一样啊
```
11. animate动画  自定义动画
```js
$('div').animate({
    width: 200,
    height:200,
    borderWidth: 10,
    fontSize: 24
})
//这个方法可以按照自己的想法来写一些参数，从而达到理想中的效果。
```
**jQuery的动画，如果上一次动画没有执行完毕就触发下一次动画的话，默认情况下会在上一次动画执行完毕后再执行下一个动画**
12. stop()动画
> 当前动画直接停止，动画就停止在当前位置，然后立即执行下一次动画
13. finish()动画
> 当前动画直接结束，动画直接执行至终止状态，然后立即执行下一次动画