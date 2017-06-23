# JavaScript事件
javaScript与HTML之间的交互是通过事件实现的.事件,就是文档或浏览器窗口中发生的一些特定的交互瞬间,可以使用侦听器(或处理器)  
来预定事件,以便事件发生是执行相应的代码.     
  
  
**js事件三要素** :事件源,事件,事件处理程序三部分组成  
**事件源:** 指的是发生事件的对象  
**事件:** 指的是做了什么动作  
**事件处理程序:** 发生事件时要做的事情  
  
  事件名|事件说明
  :--:|:--:
  onclick|鼠标单击
  ondbclick|鼠标双击
  onkeyup|按下并释放键盘上的一个键时触发
  onchange|文本内容或下拉
  onfocus|获得焦点,表示文本框等获得鼠标光标
  onblur|失去焦点,表示文本框等失去鼠标光标
  onmouseover|鼠标悬停,即鼠标停留在图片等的上方
  onmouseout|鼠标移出,即离开图片等所在的区域
  onload|网页文档加载事件
  onunload|关闭网页时
  onsubmit|表单提交事件
  onreset|重置表单时
  
##  :large_blue_circle: 事件处理
  **事件处理的四中方式:**
  1. HTML事件处理,即添加到HTML结构中   
  `<button onclick="alert('hello')">按钮</button>`  
  2. DOMO级的事件处理程序,把函数赋值给一个事件处理程序  
  `obj.onclick = function(event){ ... }`
```js
  <script type="text/javascript">
        window.onload = function() {
            //window.onload 等整个页面的所有资源都加载完毕之后才会执行这里面的代码

            var btn1 = document.getElementById("btn1"); //document.getElementById("id") 根据指定的id 属性值得到对象.
            //返回id属性值等于sID的第一个对象的引用.假如对应的是一组对象,则返回
            //改组对象中的第一个.如果无符合条件的对象,则返回null
            //console.log(btn1); //<button id="btn1">按钮1</button>

            //DOM 0级
            /*
            事件处理四种方式：
            1. HTML事件处理，即添加到HTML结构中
                <button onclick="alert('hello');">按钮</button>
            2. DOM0级的事件处理程序,把函数赋值给一个事件处理程序
                obj.onclick = function(event){ ....};
            3. DOM2级事件处理
                obj.addEventListener("事件名", "事件处理函数", "布尔值")
                    true 事件捕获方式
                    false  事件冒泡

                obj.removeEventListener("事件名", "事件处理函数", "布尔值")

            IE事件处理程序
                obj.attachEvent("on事件名", "事件处理函数")
                obj.detachEvent("on事件名", "事件处理函数")

            */

            // 获得结点
            // document.getElementById(“id”) id 为标记的 #id
            // document.getElementsByTagName(“div”) 所有的div div
            // document.getElementsByClassName(“test”) 所有类名为 test


            btn1.onclick = function(event) { //注册点击事件
                console.log("click 111");
            }

            btn1.onclick = null; //删除注册的点击事件

            var form = document.getElementById("form");

            //在form 元素上 注册submit事件
            //onsubmit 属性在提交表单时触发。onsubmit 属性只在 <form> 中使用。当表单提交时 会触发 sumbit事件
            form.onsubmit = function() {
                console.log("触发 submit。");
            };

            //为 form表单注册 onreset事件
            //onreset 事件 会在表单中的重置按钮被点击时发生
            form.onreset = function() {
                console.log("触发 reset 。。。。");
            }
        }
    </script>
```
  3. DOM2级事件处理
```js
  <script type="text/javascript">
        var f = document.getElementById("f") //获取 id = f 的元素
        var s = document.getElementById("s") //获取 id = s  的元素



        //事件的注册
        function clickHandlerF(event) {
            console.log("click F");
        }

        function clickHandlerFF(event) {
            console.log("click FF");
        }

        function clickHandlerS(event) {
            console.log("click S");
        }

        f.addEventListener("click", clickHandlerF, false);

        f.addEventListener("click", clickHandlerFF, false);

        s.addEventListener("click", clickHandlerS, false);

        f.removeEventListener("click", clickHandlerF, false); //移除注册的事件

        addEvent(f, "click", clickHandlerF);
        //removeEvent(f,"click" clickHandlerF)

        //兼容IE的事件添加和移除
        //DOM2级
        function addEvent(elem, eventName, handler) {
            if (elem.addEventListener) {
                elem.addEventListener(eventName, handler, false);
                console.log("1");
            } else if (elem.attachEvent) {
                elem.detachEvent("on" + eventName, handler);
                console.log("2");
            } else {
                elem["on" + eventName] = handler;

                // addEvent(f, "click", clickHandlerF);
                console.log("3");
            }
        }

        function removeEvent(elem, eventName, handler) {
            if (elem.removeEventListener) {
                elem.removeEventListener(eventName, handler, false);
            } else if (elem.attachEvent) {
                elem.detachEvent("on" + eventName, handler);
            } else {
                elem["on" + eventName] = null;
            }
        }
    </script>
```
