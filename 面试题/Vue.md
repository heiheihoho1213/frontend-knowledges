Vue 面试题通常围绕「基础概念 → 响应式 → 组件 → 路由 → 状态管理 → 性能优化 → Vue3 新特性」逐层深入。下面按高频考点整理，并给出一句话提示，方便你快速回忆或展开回答。  

一、基础与核心概念  
1. Vue 的核心特征？  
   答：响应式数据绑定 + 组件化 + 虚拟 DOM。  
2. MVVM 含义？  
   答：Model-View-ViewModel，数据变视图自动变，反之亦然，Vue 通过 Observer/Watcher 实现。  
3. computed 和 watch 区别？  
   答：computed 有缓存，仅依赖变才重新求值；watch 无缓存，可异步，常做副作用。  
4. v-if vs v-show？  
   答：v-if 真正的条件渲染；v-show 只是 CSS 切换 display。  
5. v-if 与 v-for 优先级？  
   答：v-for 优先；同一节点同时用会浪费渲染，建议外层 template 包 v-if。  

二、响应式原理  
6. Vue2 响应式如何实现？  
   答：递归 Object.defineProperty 劫持 getter / setter，Dep + Watcher 收集依赖、派发更新。  
7. Vue2 为什么不能检测数组下标变化？怎么解决？  
   答：defineProperty 只能劫持已存在属性；用 Vue.set / this.$set 或替换整个数组。  
8. Vue3 为什么改用 Proxy？优点？  
   答：Proxy 能一次性监听整对象、数组索引、新增/删除属性，且性能更好。  

三、组件与通信  
9. 父子、兄弟、跨级通信方式？  
   答：props / $emit、$parent/$children、ref、eventBus、provide/inject、Vuex。  
10. 单向数据流怎么理解？  
    答：父 → 子 props 向下，子想改需 $emit 事件，避免直接改 props。  
11. slot 有哪些？  
    答：默认插槽、具名插槽、作用域插槽；Vue3 引入 v-slot 缩写 #。  

四、Vue Router  
12. hash 与 history 模式差异？  
    答：hash 带 # 不请求后端；history 需服务器配置回退到 index.html。  
13. 全局路由守卫写法？  
    答：router.beforeEach((to, from, next) => { ... })；Vue3 用 return 代替 next()。  

五、Vuex  
14. 五大核心及流向？  
    答：state → getters → mutations（同步） → actions（异步） → modules；流程：dispatch → commit → 修改 state。  
15. 为什么 mutations 必须同步？  
    答：devtools 需记录状态快照，异步会导致不可追踪。  

六、性能优化  
16. keep-alive 原理？  
    答：缓存 vnode，命中时直接取缓存不重新渲染；通过 include/exclude 精准控制。  
17. nextTick 干嘛用？  
    答：DOM 更新队列完成后执行回调，常用于获取更新后的 DOM 或避免重复计算。  
18. 首屏加载优化手段？  
    答：路由懒加载、组件异步 import、webpack 分包、SSR/Nuxt、CDN 外链、开启 gzip。  

七、Vue3 新特性  
19. Composition API 解决了什么问题？  
    答：Options API 碎片化 → 按逻辑聚合；复用逻辑抽成 hook；更好 TS 支持。  
20. setup 执行时机？  
    答：在 beforeCreate 之前，组件实例尚未创建，因此 this 为 undefined。  
21. Proxy 响应式与 Reactivity API？  
    答：reactive / ref / readonly / computed / watchEffect；可脱离组件独立使用。  
22. Fragment、Teleport、Suspense 作用？  
    答：多根节点、传送 DOM、异步依赖占位。  

八、手写 / 代码题  
23. 手写自定义 v-focus 指令。  
24. 手写简易 Vuex（实现 commit、dispatch）。  
25. 手写响应式（defineProperty 或 Proxy 版）。  

以上题目覆盖 90% 的 Vue 面试场景，回答时先“一句话定位”，再视面试官追问深度扩展即可。祝你面试顺利！