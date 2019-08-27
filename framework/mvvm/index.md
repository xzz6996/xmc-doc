# mvc

用户操作--> view(视图/界面) -->controller(控制器) -->model(数据模型) -->vie

# mvvm

view -->  vm(DomListeners)  -->model
model --> vm(DataBindings)  --> view

# 三要素
## 1响应式:vue如何监听到data的每个属性变化
 1. Object.defineProperty()
 2. 将data属性代理到vm上
## 2模板引擎:vue模板如何被解析,指令如何被处理
 1. 模板是什么？
   本质:字符串。逻辑:v-for v-if。与html格式很像,区别很大。最终还是要转换为html来显示。
   模板最终要转换为js代码。
   因为: 有逻辑(v-for),必须用js来实现
        转换为html渲染页面,必须用js来实现
        模板最终转换为一个js函数(render)   
        
## 3渲染:vue模板如何被渲染成html,以及渲染过程

  render函数和dom
    updateComponent 中实现了 vdom 的 patch。
    页面首次渲染执行 updateComponent。
    data 中每次修改属性，执行 updateComponent。
    render函数的执行 是返回vnode

#  vue实现的整体流程
 1. 解析模板成render函数 

   + with的用法  
   + 模板中的所有信息都被render包含
   + 模板中的data的属性，都变成了js变量
   + 模板中的 v-for v-on 都变成了js逻辑
   + render返回vnode

 2. 响应式开始监听
   + Object.definePropoty()
   + 将data的属性代理到vm上 

 3. 首次渲染,显示页面,并且绑定依赖  
  + 初次渲染,执行updateComponent,执行vm._render函数
  + 执行vm._render函数,访问到vm.list vm.loading
  + 会被响应式的get方法监听到(为什么监听get,不监听set呢?避免不必要的渲染)
  + 执行updateComponent,走到vdom的patch
  + patch将vnode渲染成vdom,首次渲染成功  

 4. data属性的变化,触发rerender  
  + 修改属性,被set监听到
  + 执行updateComponent,重新执行vm._render
  + 生成的vnode和preVnode,通过patch对比
  + 渲染到html


