## 入群考核

#### js方向：

 1.编写一个forEachCustom 函数，要求拥有与数组的forEach函数一样的功能。
 
 2.编写一个能够深copy数组和对象的方法。
 
 3.依次写出下面程序执行后的打印结果：
  ```js
  console.log(a);
  var a = 1;
  console.log(a);
  console.log(window.a);
  console.log(this.a);
  function fun(){
    console.log(this.a);
    console.log(a);
    var a = 2;
    console.log(a);
  }
  fun();
  ```
  
 4.[附加题1] 请用观察者模式实现下面的自定义事件Event对象的接口，功能见注释，	该Event对象的接口需要能被其他对象拓展复用。
  ```js
  Event.on('test', function (result) {
      console.log(result);
  });
  Event.on('test', function () {
      console.log('test');
  });
  Event.emit('test', 'hello world'); // 输出 'hello world' 和 'test'
  var person1 = {};
  var person2 = {};
  Object.assign(person1, Event);
  Object.assign(person2, Event);
  person1.on('call1', function () {
      console.log('person1');
  });
  person2.on('call2', function () {
      console.log('person2');
  });
  person1.emit('call1'); // 输出 'person1'
  person1.emit('call2'); // 没有输出
  person2.emit('call1'); // 没有输出
  person2.emit('call2'); // 输出 'person2'
  var Event = {
      // 通过on接口监听事件eventName
      // 如果事件eventName被触发，则执行callback回调函数
      on: function (eventName, callback) {
          //你的代码
      },
      // 触发事件 eventName
      emit: function (eventName) {
          //你的代码
      }
  };
  ```
  
 5.[附加题2] 用ES6标准的Promise将下面代码中的FileReader部分封装起来，请写出	Promise封装的实现代码（即pro_reader函数的实现代码）。
  封装前的代码为：
  ```js
  var filechooser = document.getElementById("choose");
  filechooser.onchange = function () {
    var fileList = this.files;
    console.log('fileList:', fileList);
    var files = Array.prototype.slice.call(fileList);
    files.forEach(function (file, i) {
      var reader = new FileReader();
      reader.onload = function () {
        $('.img_list').append('<li style="background-image:url('+this.result+')">');
      }
      reader.readAsDataURL(file);
    });
  }
  ```
  封装之后的代码为：
  ```js
  var filechooser = document.getElementById("choose");
  filechooser.onchange = function () {
    var fileList = this.files;
    console.log('fileList:', fileList);
    var files = Array.prototype.slice.call(fileList);
    files.forEach(function (file, i) {
      pro_reader(file)
        .then(function (reader) {
          console.log(reader.result);
          var li = '<li style="background-image:url('+reader.result+')">';
          $('.img_list').append(li);
        })
        .catch(function (error) {
          console.log(error);
        });
    });
  }
  ```
    
  
