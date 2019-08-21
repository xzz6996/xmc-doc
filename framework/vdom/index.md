# vdom是什么?为何存在vdom?

## **dom渲染是最昂贵的**

如果我们使用js来直接操作dom,会影响性能,从而导致浏览器的重绘和重排。


## **解答**
1. vdom(virtual dom,虚拟dom)
2. 用js模拟dom节点
3. dom变化的对比,放在js层来做
4. 提高重绘性能  

# vdom如何应用核心api
 举例snabbdom,h函数 patch函数
 h(标签,属性,...)
 h(标签,属性,子元素)
 patch(container,vnode)
 patch(vnode,newVode)
# 了解一下diff算法
 vdom 中应用 diff 算法是为了找出需要更新的节点(不仅仅是节点的新增与删除,节点的排序,节点的样式,性能.....)


