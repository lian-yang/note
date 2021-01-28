### vue组件通信方式

![](https://user-gold-cdn.xitu.io/2019/7/11/16bde5b613802d6b?w=499&h=566&f=png&s=133668)

```js
// 如果层级很深那么就会出现$parent.$parent.....我们可以封装一个$dispatch方法向上进行派发
Vue.prototype.$dispatch = function $dispatch(eventName, data) {
  let parent = this.$parent;
  while (parent) {
    parent.$emit(eventName, data);
    parent = parent.$parent;
  }
};

// 相同的道理，如果既然能够向上寻找父亲，就能向下寻找儿子，也可以封装一个向下派发的方法$broadcast
Vue.prototype.$broadcast = function $broadcast(eventName, data) {
  const broadcast = function () {
    this.$children.forEach((child) => {
      child.$emit(eventName, data);
      if (child.$children) {
        $broadcast.call(child, eventName, data);
      }
    });
  };
  broadcast.call(this, eventName, data);
};
```

