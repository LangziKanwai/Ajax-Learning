# Ajax

Ajax 是一种使用 XMLHttpRequest 技术构建更复杂，动态的网页的编程实践。主要用于与服务器进行通信。

## axios 库

使用 axios 库，与服务器进行数据通信。

语法：

```html
<!-- 引入 axios.js 库 -->
<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
<script>
  // 使用 axios 函数
  axios({
    // 需要访问的服务器资源地址
    url: "http://hmajax.itheima.net/api/province",
  }).then((result) => {
    // then 回调函数获取接收到的数据
    console.log(result); // 获取到的是一个对象
  });
</script>
```

## URL

URL 就是统一资源定位符，简称网址，用于访问网络上的资源。

结构：

```js
const obj = {
  // https: 协议
  // hmajax.itheima.net: 域名
  // api/province: 资源路径
  // 协议://域名/资源路径
  url: "http://hmajax.itheima.net/api/province",
};
```

### URL 查询参数

定义：浏览器提供给服务器的额外信息，让服务器返回浏览器想要的数据。

```js
axios({
  url: "http://hmajax.itheima.net/api/city",
  // 参数查询
  params: {
    // 参数名: 值
    pname: "安徽省",
  },
}).then((result) => {
  // 服务器传回的数据
  console.log(result);
});
```

## 请求方法与数据提交

请求方法：对服务器资源，要执行的操作。

GET 获取数据

POST 提交数据

PUT 修改全部数据

PATCH 修改部分数据

DELETE 删除数据

### POST 提交数据

axios 中 method 可以设置请求的方法，当使用 GET 请求时可以省略。

其中 axios 中的 data 属性可以设置提交的数据。

```js
axios({
  url: "目标资源地址",
  method: "请求方式",
  data: {
    参数名: 值,
  },
}).then((result) => {
  // 获取服务器返回的数据进行后续处理
});
```

## HTTP 协议

HTTP 协议规定了浏览器发送及服务器返回内容的格式。

### 请求报文

浏览器按照 HTTP 协议要求的格式，发送给服务器的内容，即为请求报文。

组成：

1. 请求行：包含请求的方法和网址

2. 请求头：携带的信息

3. 空行

4. 请求体：提交的数据

### 响应报文

服务器按照 HTTP 协议要求的格式，返回给浏览器的内容。

组成：

1. 响应行：包含协议、HTTP 响应状态码、状态信息

2. 响应头：以键值对的形式携带的附加信息

3. 空行：分隔响应头

4. 响应体：返回的数据

### HTTP 响应状态码

用来表明请求是否成功完成。

1xx 信息

2xx 成功

3xx 重定向消息

4xx 客户端错误

5xx 服务端错误

## 接口文档

接口文档：描述接口的文章。

接口：使用 Ajax 和服务器通讯时，使用的 URL 和请求方法、参数等。

## form-serialize 插件

作用：快速收集表单元素的值。

```html
<form action="javascript:;" class="example-form">
  <input type="text" name="username" />
  <br />
  <input type="text" name="password" />
  <br />
  <input type="button" class="btn" value="提交" />
</form>
<!-- 引入插件 -->
<script src="./lib/form-serialize.js"></script>
<script>
  document.querySelector(".btn").addEventListener("click", () => {
    const form = document.querySelector(".example-form");
    // 参数：需要获取数据的表单、配置对象
    // 配置对象：
    /* hash 设置获取数据结构
     *    - true：JS 对象（推荐）一般请求体里提交给服务器
     *    - false: 查询字符串
     * empty 设置是否获取空值
     *    - true: 获取空值（推荐）数据结构和标签结构一致
     *    - false：不获取空值
     */
    const data = serialize(form, { hash: true, empty: true }); // {username: 'asdfg', password: '123456'}
    // const data = serialize(form, { hash: false, empty: true }); // username=asdfg&password=123456
    // const data = serialize(form, { hash: true, empty: false }); // {username: 'asdfg'}
    console.log(data);
  });
</script>
```
