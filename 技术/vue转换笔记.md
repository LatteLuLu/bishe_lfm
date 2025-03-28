# HTML转VUE

## 问题统计

```
1.获取url中的参数，监听params值变化
2.html转vue都需改哪些部分，css如何引入？js库如何引入？jquery如何引入？
3.如何引入router
```

### vue引入css代码方法

```vue
<style lang="scss" scoped>
	@import "../assets/css/amazeui.css";
	@import "../assets/css/admin.css";
	@import "../assets/css/demo.css";
	@import "../assets/css/seastyle.css";
</style>
```

### 百度地图无法创建BMapGL()对象

```js
//在BMapGL对象前加上window
new window.BMapGL.map()
```

### html页面转vue页面流程

```vue
# 假如把search.html转为search.vue

1. 在src/assets/css下创建search.css,把html中的css代码复制到search.css中
2. 在src/components下创建search.vue,写出vue的基本框架
    <template>

    </template>

    <script>
    export default {

    }
    </script>

    <style>

    </style>
3. 在style中引用css代码
    <style>
        @import "../assets/css/search.css";
    </style>
4. 在search.html的body中，把与页面有关的代码复制到<template></template>中
	<template>
		<div>
            search.html中与页面有关的代码。。。。。。。。
        </div>
	</template>
5. 构建<script></script>中的基本结构
    <script>
    export default {
        name:"XxxSearch",//驼峰命名法
        data() {
            return {
            }
        },
        methods: {
        },
        mounted() {
        },
    }
    </script>
若search.html中没有js，jquery代码到这里就结束了，以下是将js，jquery代码引入vue页面
引入js，jquery详见https。。。。。。。

6. 将自定义的js变量(var xxx)引入到 vue的script的data的return 中
    data() {
        return {
            //热搜榜展示区
            div_show : $(".search"),
            //标签类别存储
            lc_categories:"",
        }
    },
7. 将jquery代码复制到 vue的script的mounted 生命周期函数中
    mounted() {
       loadJs("aa.js").then(()=>{
           $(function () {
               jquery代码。。。。。。。。。
           })
       })
	},
8. 将自定义的js函数复制到 vue的script的methods 中
————复制后，删除代码中的function，并在每一个函数的 } 后加 ,
    methods: {
        //获取标签类别
        getlcg_num() {
            函数代码。。。。
        },
    }
9. ctrl+F 将vue页面中所有的onclick替换为@click
```

