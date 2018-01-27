# DOM_KuoZhan
JS_DOM扩展





            classList 属性



                   在操作类名时，需要通过className属性添加，删除，替换，因为className中是一个字符串，
                   所以即使只修改字符串一部分，也必须每次都设置整个字符串的值

                     如下：例子  删除类中 ki



                                      <div  id="div" class="is ki opp"></div>

                           var text=document.getElementById("div")

                      首先，取到类名 把这三个类拆分成数组
                            var classns=text.className.split(/\s+/);
                            var pos=-1;
                            for(var i=0;i< classns.length;i++){
                            if(classns[i]=="ki"){
                                删除类名(ki)
                                classns.splice(i,1);
                              break;

                            }
                          }    

                    把剩下的类名拼成字符串，并重新设置
                           text.className=classns.join(" ");
                           console.log(text.className)     输出    is opp 



                   HTML5新增了一个操作类的方法，className()

                        这个新类型 还定义了如下方法

                          add(value)   将给定的字符串值添加到列表中,如果值存在,就不添加了
                          contains(value)  表示列表中是否设置值, 如果存在返回true,否则返回false 
                    remove(value)    从列表中删除给定的字符串
                    toggle(value) 如果列表中已经存在给定的值,删除它,如果列表中没有给定值,添加它



                    add(value)   将给定的字符串值添加到列表中,如果值存在,就不添加了
                       添加“div”类
                       div.classList.add("div")

                    contains(value)  表示列表中是否设置值, 如果存在返回true,否则返回false 
                         确定元素中是否包含既定的类名
                   if(div.classList.contains("bd")&& !div.classList.contains("disd")){
                    //执行操作
                    }

                    remove(value)    从列表中删除给定的字符串
                       删除“div”类
                       div.classList. remove("div")

                    toggle(value) 如果列表中已经存在给定的值,删除它,如果列表中没有给定值,添加它
                        切换“div”类
                             div.classList. toggle("div")

                   注意支持 classList的属性浏览器 有 Firefox3.6+和 Chrome




             焦点管理




                  focus()  主要是用于获取焦点，说白了，就是自动把光标放到此组件上面，无须用户再次操作

                   document.hasFocus() 是否得到焦点，如果得到焦点 返回 true, 没有焦点 返回fasle

                       var text= document.querySelector("#inpt");
                    text.focus()
                      if( document.hasFocus()){
                      console.log("得到焦点");
                         }else{
                      console.log("没有焦点");
                      }

                         输出   得到焦点 




                readyState：属性  (他一般实现一个指示文档已经加载完成的指示器)


                   下面是它的两个可能值	      
                     loading  正在加载
                     complete  已经加载完成

                       if(document.readyState=="loading"){
                        alert("正在加载。。。。。");
                       }else if(document.readyState=="complete"){
                         alert("加载完成。。。。。")
                       }



                兼容模式



                       IE给document添加了一个名为compatMode的属性,这个属性告诉开发人员浏览器采用了那种渲染模式,

                      1: 在标准模式下 document.compatMode的值等于 "CSSlCompat"
                      2:在混乱模式下  document.compatMode 的值等于 "BackCompat"


                      if(document.compatMode=="CSSlCompat"){
                   alert("我是标准模式的浏览器");
                      }else if(document.compatMode=="BackCompat"){
                    alert("我是混乱模式的浏览器");
                      }



            插入标记



               innerHTML： 方法

                     <div id="bt2"></div>

                     var div= document.querySelector("#bt2");
                     div.innerHTML="<p>66666</p>";

                   浏览器输出  
                     <div id="bt2">
                    <p>66666</p>
                     </div>



                 outerHTML：方法      outerHTML与innerHTML差别看浏览器输出结果 就有区别了

                       <div id="bt2"></div>

                         var div= document.querySelector("#bt2");
                       div.outerHTML="<p>66666</p>";

                          浏览器输出
                            <p>66666</p>




                 insertAdjacentHTML() 新增的插入方法

                               beforebegin 在当前元素之前插入一个紧邻的同辈元素

                   afterbegin  在当前元素之前插入一个新的子元素或第一个子元素之前再插入新的元素

                   beforeend  在当前元素之下插入一个新的子元素或在最后一个子元素之后再插入新的子元素

                   afterend     在当前元素之后插入一个紧邻的同辈元素


                         var div= document.querySelector("#bt2");

                     作为前一个同辈元素插入
                         div.insertAdjacentHTML("beforebegin","<p>66666</p>")

                     作为 第一个子元素插入
                         div.insertAdjacentHTML("afterbegin","<p>66666</p>")  

                     作为最后一个子元素插入
                         div.insertAdjacentHTML("beforeend","<p>66666</p>")

                     作为后一个同辈元素插入
                         div.insertAdjacentHTML("afterend","<p>66666</p>")





             scrollIntoView()  滚动




                            scrollIntoView(ture)元素上边框与视窗顶部齐平

                            scrollIntoView(false)元素下边框与视窗底部齐平



                    例子
                  #slvFalse{
                        position: absolute; 
                        bottom: 0;
                        position: absolute;
                    }
                  #div{
                    height: 800px;
                    background: #008000;
                    position: relative;
                    }

                  </style>

                   <button id="btn1">btn1</button>
                   <button id="bt2">bun2</button>

                    <div style="height: 200px;background: #008000;"></div>

                    <div id="div">
                  <span>scrollIntoView(ture)元素上边框与视窗顶部齐平  </span>
                 <span  id="slvFalse" >scrollIntoView(false)元素下边框与视窗底部齐平</span>
                    </div>


                        document.querySelector("#btn1").onclick=function(){

                                 document.querySelector("#div").scrollIntoView(true);

                        }
                        document.querySelector("#bt2").onclick=function(){
                          document.querySelector("#div").scrollIntoView(false);
                        }




               contains() 方法 ：查看一个节点是不是另一个节点的后代


                如果A元素包含B元素，则返回true，否则false。唯一不支持这个方法的是IE的死对头firefox。
                不过火狐支持compareDocumentPosition() 方法,这是W3C制定的方法，标准浏览器都支持，
                不过实用性性很差，它的使用形式与contains差不多，但返回的不是 一个布尔值，
                而是一个很奇怪的数值 


                         例子

                              <div>
                    <span></span>
                 </div>
                             <a></a> 

                          var  a=document.querySelector("a");
                          var  div=document.querySelector("div");
                          var span =document.querySelector("span");

                          console.log(a.contains(div))       //false

                          console.log(div.contains(span))   // true


