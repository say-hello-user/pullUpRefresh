# pullUpRefresh
手机端实现上拉动态加载以后下拉刷新的功能

### 截屏效果

#### 1.拉起来动态加载
![image](https://github.com/say-hello-user/pullUpRefresh/blob/master/img/1.png)


#### 2.正在加载
![image](https://github.com/say-hello-user/pullUpRefresh/blob/master/img/2.png)

#### 3.加载完成，动态添加了两个节点
![image](https://github.com/say-hello-user/pullUpRefresh/blob/master/img/3.png)

### 部分代码注释

```javascript
        for (var i = 0; i < document.querySelectorAll("#wrapper ul li").length; i++) {
            document.querySelectorAll("#wrapper ul li")[i].colorfulBg();
        }
        refresher.init({
            id: "wrapper",//容器
            pullDownAction: Refresh,//下拉加载内容
            pullUpAction: Load//上拉加载内容
        });
        var generatedCount = 0;
        function Refresh() {
            setTimeout(function () {	
               console.log("下拉加载内容");
                wrapper.refresh();//每次都调用插件的refresh函数，用来更新最新加载元素的位置
            }, 1000);

        }

        function Load() {
            setTimeout(function () {
                 console.log("上拉加载内容");
                var el, li, i;
                el = document.querySelector("#wrapper ul");
                for (i = 0; i < 2; i++) {//动态添加两个节点
                    li = document.createElement('li');
                    li.appendChild(document.createTextNode('async row ' + (++generatedCount)));
                    el.appendChild(li, el.childNodes[0]);
                }
                 for (var i = 0; i < document.querySelectorAll("#wrapper ul li").length; i++) {//随机为元素添加背景颜色
                    document.querySelectorAll("#wrapper ul li")[i].colorfulBg();
                }
                wrapper.refresh();//每次都调用插件的refresh函数，用来更新最新加载元素的位置
            }, 1000);
        }
```

