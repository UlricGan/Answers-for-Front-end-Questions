#Answers For Interview Questions

所有的题目来自于 [Front-end Job Interview Question](https://github.com/darcyclarke/Front-end-Developer-Interview-Questions#html) 

##HTML

+ ####What is `doctype` do?  
`doctype`描述了该页面的HTML类型。同时浏览器通过`doctype`来决定如何渲染页面，如果不含`doctype`或是`doctype`错误会导致浏览器触发怪癖模式。目前`<!DOCTYPE html>`是个好选择（大部分浏览器支持，包括IE6）。详细见[What's up, Doctype?](http://stackoverflow.com/questions/414891/whats-up-doctype)

+ ####Difference between standards mode and quirks mode?  
在怪癖模式时，浏览器会根据不标准的行为渲染（处理）页面，并且不同浏览器的怪癖模式不同（尤其是IE和其他浏览器）；相反在标准模式时，所有浏览器会根据统一的标准（理想上）。  
对于HTML文件浏览器通过`doctype`来决定选择哪种模式；对于XHTML（`'application/xhtml+xml'`）则无需`doctype`浏览器也会选择标准模式，但IE8及更低版本无法识别该种类型的文件而触发下载，如果XHTML使用`text/html`MIME type，则浏览器会将其看作HTML，所以选择标准模式需要`doctype`。详细可以看[Quirks Mode and Standards Mode](https://developer.mozilla.org/en-US/docs/Quirks_Mode_and_Standards_Mode)

+ ####limitations when serving XHTML pages  
IE8及更低版本无法识别`application/xhtml+xml`类型

+ ####serve a page with content in multiple language  

###JavaScript

+ ####Explain event delegation  

+ ####Explain `this` in JavaScript  
函数中的`this`的值取决于函数调用的模式：  
  1. 方法调用模式  
  当函数被保存为对象的一个属性时，成该函数为该对象的方法。函数中`this`的值为该对象。
  2. 函数调用模式  
  当函数并不是对象的属性。函数中`this`的值为全局对象  
  note：某个方法中的内部函数中的`this`的值也是全局对象，而非外部函数的`this`
  3. 构造器调用模式
  即使用`new`调用的函数，则其中`this`将会被绑定到那个新构造的对象。
  4. 使用`apply`或`call`调用模式  
  该模式调用时，函数中`this`被绑定到apply或call方法调用时接受的第一个参数。
  
+ ####Explain prototypal inheritance  
所有的object都是基于prototype的，同时prototype也是object，定义了基于它的object的属性和方法。在大部分浏览器中object的_proto_属性对应这其prototype。
例如一些内建的Array, Function, 他们实例的prototype均为Object
所以object会拥有两类属性和方法：实例类和原型类
note: hasOwnProperty方法可以判断某属性或方法属于哪一类。
举个例子：  

		var Paper = function(){};
		var Book;
		Book.prototype = new Paper();
		var book1 = new Book();
		var book2 = new Book();
		
  图释：  
  ![prototype inheritance](images/prototypal inheritance.png)
  