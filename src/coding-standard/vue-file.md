# Vue 文件书写规范

在我们的开发中，接触最多就是：xxx.vue 的文件，所以我们应该制定一些规则来规范我们的代码。
按照一般的习惯组织代码，从上到下，依次是：template, script 和 style 标签。然后依次说明每个部分在编程时应该注意的问题。

## template

> 在模版文件中，你应该遵守 HTML 的书写规范

**1、标签语义化，切忌清一色的 div 元素**。列表可以使用 ul li，文字使用 p 标签，标题使用 h* 标签，等等。虽然 HTML5 推出了语义化的标签，但是它们还有很多兼容性问题，在不支持的浏览器导致布局错乱。所以，不建议在生产环境中使用：section，aside，header，footer，article，等 HTML5 布局标签。

**2、样式 class 的命名：以小写字母开头，小写字母、中划线和数字组成**。不建议使用驼峰法命名 class 的属性。以下是一些常用到的 class的名字。
> 包裹层: .xx-wrap; 列表: .xx-list; 列表项: .xx-list-item; 左边内容: .xx-left; 中间内容: .xx-middle; 右边内容: .xx-right; 某个页面: .xx-page;

**3、自定义标签：使用自闭标签的写法**。例如：```<my-owner-components/>```。[参考这里](https://cn.vuejs.org/v2/style-guide/#%E8%87%AA%E9%97%AD%E5%90%88%E7%BB%84%E4%BB%B6-%E5%BC%BA%E7%83%88%E6%8E%A8%E8%8D%90)

**4、多特性，分行写，提高可读性**。示例代码如下，具体原因 [看这里](https://cn.vuejs.org/v2/style-guide/#%E5%A4%9A%E4%B8%AA%E7%89%B9%E6%80%A7%E7%9A%84%E5%85%83%E7%B4%A0-%E5%BC%BA%E7%83%88%E6%8E%A8%E8%8D%90)

```html
<scroll
    ref="scrollWrap"
    :data="homeData"
    :pullDownRefresh="true"
    :pullUpLoad="true"
    class="home-scroll-warp"
    @pullingDown="pullingDownGetNewData"
    @pullingUp="pullingUpGetMore"
/>
```

**5、模版中使用表达式，复杂情况使用计算属性或函数**。[参考这里](https://cn.vuejs.org/v2/style-guide/#%E6%A8%A1%E6%9D%BF%E4%B8%AD%E7%AE%80%E5%8D%95%E7%9A%84%E8%A1%A8%E8%BE%BE%E5%BC%8F-%E5%BC%BA%E7%83%88%E6%8E%A8%E8%8D%90)

## script

> 在 script 标签中，你应该遵守 Js 的规范

**1、在 script 标签的最顶部，应该是引入文件的定义**。

**2、vue/cli 脚手架自带的 '@' 问题**。你可以使用绝对或相对路径引入你自定义的文件，也可以使用脚手架自带的指向 src 开发目录的 '@' 符号。
**前者**可能在写法上可能不是很美观，有一长串的地址，而且日后文件的关系变动，必须手动维护地址；**后者**牺牲了可读性，获得了更简洁的绝对地址。日后
文件的关系变动，只要文件名不变，则不需维护路径，维护成本要小很多。但是使用 '@' 符号对编辑器不友好，点击方法，并不会直接跳转到方法定义，带来了调试和阅读的成本。权衡两者，各有利弊，使用哪种方式，可以根据个人喜好。**但不要混用两种方法。**

**3、引入组件，命名使用：首字母大写的驼峰法命名**。推荐使用 ES6 的方式引入。如果它们有依赖关系，最好体现在命名上，比如：

```javascript
import Article from 'xxx'
import ArticleDetail from 'xxx'
```

**4、组件的选项，根据官方的推荐按照以下定义**。[原文出处](https://cn.vuejs.org/v2/style-guide/#%E7%BB%84%E4%BB%B6-%E5%AE%9E%E4%BE%8B%E7%9A%84%E9%80%89%E9%A1%B9%E7%9A%84%E9%A1%BA%E5%BA%8F-%E6%8E%A8%E8%8D%90)

```javascript
<script>
  export default {
    name: 'ExampleName',  // 这个名字推荐：大写字母开头驼峰法命名。
    props: {},            // Props 定义。
    components: {},       // 组件定义。
    directives: {},       // 指令定义。
    mixins: [],           // 混入 Mixin 定义。
    data () {              // Data 定义。
      return {
        dataProps: ''     // Data 属性的每一个变量都需要在后面写注释说明用途，就像这样
      }
    },
    computed: {},         // 计算属性定义。
    created () {},         // 生命钩子函数，按照他们调用的顺序。
    mounted () {},         // 挂载到元素。
    activated () {},       // 使用 keep-alive 包裹的组件激活触发的钩子函数。
    deactivated () {},     // 使用 keep-alive 包裹的组件离开时触发的钩子函数。
    watch: {},            // 属性变化监听器。
    methods: {            // 组件方法定义。
      publicbFunction () {}  // 公共方法的定义，可以提供外面使用
      _privateFunction () {} // 私有方法，下划线定义，仅供组件内使用。多单词，注意与系统名字冲突！
    }
  }
</script>
```

**5、Data 必须是一个函数**。[参考这里](https://cn.vuejs.org/v2/style-guide/#%E7%BB%84%E4%BB%B6%E6%95%B0%E6%8D%AE-%E5%BF%85%E8%A6%81)

**6、Props 定义细则**。[参考这里](https://cn.vuejs.org/v2/style-guide/#Prop-%E5%AE%9A%E4%B9%89-%E5%BF%85%E8%A6%81)

**7、为 v-for 设置 key 值**。[参考这里](https://cn.vuejs.org/v2/style-guide/#%E4%B8%BA-v-for-%E8%AE%BE%E7%BD%AE%E9%94%AE%E5%80%BC-%E5%BF%85%E8%A6%81)

**8、使用计算属性规避 v-if 和 v-for 用在一起**。[参考这里](https://cn.vuejs.org/v2/style-guide/#%E9%81%BF%E5%85%8D-v-if-%E5%92%8C-v-for-%E7%94%A8%E5%9C%A8%E4%B8%80%E8%B5%B7-%E5%BF%85%E8%A6%81)

## style

> 样式部分，因为样式有原生的 CSS 写法，也有使用预处理语言：Sass, Less，Stylus。所以情况比较多，也比较复杂。在我实际的工作中用的最多的是：Stylus 和 CSS 的混合。为啥呢？第一：感觉项目只使用一种样式语言可能比较少，每种样式语言都是有缺陷的。所以会使用 Stylus 来弥补 CSS 上的不足。第二：为啥是 Stylus 呢？ 因为 Stylus 是 node.js 社区推处出来的，可能在打包构建等方面更有优势吧。最后退一步说，其实 CSS 的预处理语言的语法大多数情况下都是差不多的，用哪个问题都不大。

**1、使用 scorpe 关键字，约束样式生效的范围**。[参考这里](https://cn.vuejs.org/v2/style-guide/#%E4%B8%BA%E7%BB%84%E4%BB%B6%E6%A0%B7%E5%BC%8F%E8%AE%BE%E7%BD%AE%E4%BD%9C%E7%94%A8%E5%9F%9F-%E5%BF%85%E8%A6%81)

**2、引入 .styl 文件：使用 ```@import '../xx/xxx.styl'``` 相对路径的形式**。逗号结尾，并且在最后一个引入，加一个换行。

**3、避免使用标签选择器**。因为这个在 Vue 中，特别是在局部组件，效率特别低，损耗性能，建议需要的情况，直接定义 class。[参考这里](https://cn.vuejs.org/v2/style-guide/#scoped-%E4%B8%AD%E7%9A%84%E5%85%83%E7%B4%A0%E9%80%89%E6%8B%A9%E5%99%A8-%E8%B0%A8%E6%85%8E%E4%BD%BF%E7%94%A8)

**4、非特殊情况下，禁止使用 ID 选择器定义样式**。有 JS 逻辑的情况除外。

**5、CSS 属性书写顺序：先决定定位宽高显示大小，再做局部细节修饰**！推荐顺序：定位属性(或显示属性，display)->宽高属性->边距属性(margin, padding)->字体，背景，颜色等，修饰属性的定义。

> 这样定义为了更好的可读性，让别人只要看一眼就能在脑海中浮现最终显示的效果。以下给出常用的定义示例：

```CSS
.class-name {
    position: fixed;
    top: 100px;
    left: 0;
    right: 0;
    bottom: 0;
    display: block;
    width: 100%;
    height: 100%;
    margin: 10px;
    padding: 10px;
    font-size: 14px;
    color: #000;
    background-color: red;
    border-radius: 2px;
    line-height: 1.42;
}
```
