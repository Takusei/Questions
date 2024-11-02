# Vue Basic

### $route 和 $router 的区别？
```
$route 是“路由信息对象”，包括 path，params，hash，query，fullPath，matched，name 等路由信息参数。
而 $router 是“路由实例”对象包括了路由的跳转方法，钩子函数等。

$route 提供当前路由的信息，主要用于获取路由状态。$route 是一个只读对象，包含当前激活路由的信息。
$router 提供导航功能，主要用于编程式地控制路由。$router 是 Vue Router 的实例，包含了路由的导航方法和钩子。
```

### keep-alive 组件有什么作用？
```
如果你需要在组件切换的时候，保存一些组件的状态防止多次渲染，就可以使用 keep-alive 组件包裹需要保存的组件。

<keep-alive>
  <component :is="currentComponent"></component>
</keep-alive>

```

### vue 中 mixin 和 mixins 区别？
```
mixin 用于全局混入，会影响到每个组件实例。

// 定义一个 mixin 对象
const myMixin = {
  data() {
    return {
      sharedData: '这是共享的数据'
    };
  },
  methods: {
    sharedMethod() {
      console.log('这是共享的方法');
    }
  }
};


mixins 应该是我们最常使用的扩展组件的方式了。如果多个组件中有相同的业务逻辑，就可以将这些逻辑剥离出来，
通过 mixins 混入代码，比如上拉下拉加载数据这种逻辑等等。另外需要注意的是 mixins 混入的钩子函数会先于组件内的钩子函数执行，
并且在遇到同名选项的时候也会有选择性的进行合并

// 在组件中使用 mixins 属性引入 mixin
export default {
  mixins: [myMixin],
  data() {
    return {
      componentData: '这是组件自身的数据'
    };
  },
  created() {
    this.sharedMethod(); // 调用 mixin 中的方法
  }
};

```