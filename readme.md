### handlebars
#### 一. 为什么要使用模板引擎

> 1.可维护性（后期修改方便）；

> 2.可扩展性（随时增加新功能，新需求）；

> 3.开发效率提高（程序逻辑组织更好，调试方便）；

> 4.html和js分离，不需要使用字符串拼接（不容易写错）；

#### 二.如何使用Handlebars
> 1.下载Handlebars

- [官网下载](http://handlebarsjs.com./installation.html)
- [GIT官网](https://github.com/daaain/Handlebars.git)
- [jQuery-CDN](http://www.bootcdn.cn/jquery/)
- [Handlebars-CDN](http://www.bootcdn.cn/handlebars.js/)
- 通过npm下载: npm install --save handlebars
- 通过bower下载: bower install --save handlebars

> 2.引入Handlebars

- 注意：handlebars依赖jQuery，首先要引入jQuery，在引handlebars

> 3.创建使用模板

- 步骤一: 通过一个<script>将需要的模板包裹起来
- 步骤二: 在<script>标签中填入type和id，type类型可以是除text/javascript以外的任何MIME类型,但推荐使用type="text/template",更加语义化
id是在后面进行编译的时候所使用,让其编译的代码找到该模板.
- 步骤三: 在<script>标签中插入我们需要的html代码,根据后台给我们的接口文档,修改其需要动态获取的内容
    ```
    <script type="text/template" id="myTemplate">
        <div class="demo">
            <h1>{{name}}</h1>
            <p>{{content}}</p>
        </div>
    </script>
    ```
> 4.在JS代码中编译模板

```
//用jQuery获取模板
var template = $("#myTemplate").html();
//预编译模板
var func = Handlebars.compile(template);
//匹配json内容
var str = func(data);
//输入模板
$('#box').html(str);
```
以上述代码为例进行解释:

- 步骤一: 获取模板的内容放入到template中,这里$("#myTemplate")中填入的内容为你在上一步创建模板中所用的id.
提醒: 这里我使用的jQuery的选择器获取,当然,你可以使用原生javascript的DOM选择器获取,例如:docuemnt.getElementById('myTemplate')和document.querySelector('#myTemplate')
- 步骤二: 使用Handlebars.compile()方法进行预编译,该方法传入的参数即为获取到的模板
- 步骤三: 使用func()方法进行编译后得到拼接好的字符串,该方法传入的参数即为上一步预编译的模板.
- 步骤四: 将编译好的字符串插入到你所希望插入到的html文档中的位置,这里使用的是jQuery给我们提供的html()方法.同样,你也可以使用原生的innerHTML
