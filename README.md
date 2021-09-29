# 使用 Typescript + Vue3.0 从零到一测试到上线 高仿知乎专栏

## 课程亮点

- Vue3 + Typescript 全网首发，2020 年最火技术双剑合璧，Vue3 配合 Typescript ，使用新版 Vuex 和 Vue-Router 全家桶完成前后端分离复杂项目

- 组件库为脉络 实现一系列由易到难的通用组件开发，可谓学会一个基本的组件库的开发。

- 提供真实后端 API 告别 mock 数据，并提供 swagger 在线调试查询。

## 课程与服务

- **项目演示站点：[http://zhihu.vikingship.xyz/](http://zhihu.vikingship.xyz/)**
- 在线后端 API 查询和使用站点：[http://api.vikingship.xyz/](http://api.vikingship.xyz/)
- 项目在线文档：[http://docs.vikingship.xyz/](http://docs.vikingship.xyz/)
- 完成的组件库展示：[http://showcase.vikingship.xyz/](http://showcase.vikingship.xyz/)
- 流程图和原型图
- 购买后直接可以接入使用的真实后端 API
- **如果您想学习本课程，请支持正版，谢谢！ [https://coding.imooc.com/class/449.html](https://coding.imooc.com/class/449.html)**

## 演示信息

账号密码: 111@test.com / 111111

## 组件设计

### Input

- 设计

```ts
<validate-input :rules=""/>
interface RuleProp {
  type: "required" | "email"| 'range' | ...;
  message: string;
}
export type RulesProp = RuleProp[];
```

- 支持`v-model`

```ts
  props: {
    modelValue: String,
  },
  const updateValue = (e: KeyboardEvent) => {
    const targetValue = (e.target as HTMLInputElement).value;
    inputRef.val = targetValue;
    emit("update:modelValue", targetValue);
  };
```

- 使用`$attrs` 支持默认属性

1. 在模板中使用 `v-bind="$attrs"`
2. 禁用根元素 Attribute 继承 `inheritAttrs: false`

### Form

- 设计

```ts
<validate-form form-submit="onFormSubmit"/>
  <validate-input />
</validate-form>
const onFormSubmit(isValid)=>{
  if(isValid){
      // 验证通过
  }
}
```

- 使用`slot`插槽

```html
<!-- 默认插槽 -->
<slot name="default" />
<!-- 具名插槽 -->
<div class="submit-area" @click.prevent="submitForm">
  <slot name="submit">
    <button type="submit" class="btn btn-primary">提交</button>
  </slot>
</div>
```
