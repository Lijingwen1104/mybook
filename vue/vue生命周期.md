
### vue生命周期

![图片](https://cn.vuejs.org/images/lifecycle.png) 

```js
	<!DOCTYPE html>
	<html>
	<head>
			<title></title>
			<script type="text/javascript" src="https://cdn.jsdelivr.net/vue/2.1.3/vue.js"></script>
	</head>
	<body>

	<div id="app">
			<p>{{ message }}</p>
	</div>

	<script type="text/javascript">

	var app = new Vue({
		el: '#app',
		data: {
			message : "123" 
		},
		beforeCreate: function () {
			console.group('创建前状态===============》');
			console.log(this.$el); //undefined
			console.log(this.$data); //undefined 
			console.log(this.message)  
		},
		created: function () {
			console.group('创建完毕状态===============》');
			console.log(this.$el); //undefined
			console.log(this.$data); //已被初始化 
			console.log(this.message); //已被初始化
		},
		beforeMount: function () {
			console.group('挂载前状态===============》');
			console.log((this.$el)); //已被初始化
			console.log(this.$data); //已被初始化  
			console.log(this.message); //已被初始化  
		},
		mounted: function () {
			console.group('挂载结束状态===============》');
			console.log(this.$el); //已被初始化
			console.log(this.$data); //已被初始化
			console.log(this.message); //已被初始化 
		},
		beforeUpdate: function () {
			console.group('更新前状态===============》');
			console.log(this.$el);
			console.log(this.$data); 
			console.log(this.message); 
		},
		updated: function () {
			console.group('更新完成状态===============》');
			console.log(this.$el);
			console.log(this.$data); 
			console.log(this.message); 
		},
		beforeDestroy: function () {
			console.group('销毁前状态===============》');
			console.log(this.$el);
			console.log(this.$data); 
			console.log(this.message); 
		},
		destroyed: function () {
			console.group('销毁完成状态===============》');
			console.log(this.$el);
			console.log(this.$data); 
			console.log(this.message)
		}
	})
	</script>
	</body>
	</html>

```