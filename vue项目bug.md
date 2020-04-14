## elementUI el-menu

**场景**: 侧导航实现某个图标的显示与隐藏

**bug**: 直接在el-menu-item中通过v-if或v-show判断, vue报错如下` You may have an infinite update loop in a component`

**原因**: v-for中使用了v-if / v-show, 从而触发了vue的报错机制, 导致bug出现

**解决办法**:  将所需要的判断的元素封装成一个组件, 在组件内部进行v-if / v-show 判断

## 多维数组由内层向外层判断

**场景**: 树行结构,分类下面有内容时显示此分类, 分类下面无内容时隐藏此分类

**解决办法**: 将多维数组转为以为数组, 同时每一项均记录其子节点的索引值及父节点的索引值, 同时给每项添加isShow: false属性, 通过递归遍历, 将属于内容的元素isShow设为true,同时根据父节点索引值将其父节点元素isShow属性设为true, 从而可实现上述场景需求 

## VUE中数据已更新,但页面为更新

**解决办法** 

- 通过v-if实现页面更新
- 通过$nextTick()实现更新
- 通过$forceUpdate实现更新, 注: 此方法仅仅影响实例本身和插入插槽内容的子组件，而不是所有子组件
- 通过$set()实现更新

具体业务场景可选用不同的方式去实现

## el-tree异步树(设置了data属性)

**bug**: 通过异步方式去加载, 当拖拽排序时, 会造成拖入到某节点后出现渲染相同元素从而到时key相同错误, 或会造成拖拽失败

**解决办法**

- 如必须设置data属性时, 每次拖拽排序完成时, 通过查找将data中拖拽的此项元素清除
- 如非必须设置data属性, 则取消掉data属性, 亦可解决此问题

## js控制el-popover显示与隐藏

```javascript
this.$refs.popover.showPopover = false
```

## 项目优化

- v-for遍历设置key值, 且避免同时使用v-if
- 无用的事件及时销毁
- 图片资源进行懒加载
- 路由懒加载
- 第三方插件按需引入(可借助**babel-plugin-component**)
- 缓存的合理使用
- 合理使用computed

