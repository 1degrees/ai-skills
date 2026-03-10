# 表单组件 - TinyForm

## Props

| 属性名称 | 属性类型 | 默认值 | 属性说明 |
| :--- | :--- | :--- | :--- |
| disabled | boolean | false | 是否禁用该表单内的所有表单组件，若设置为 true，则表单内组件上的 disabled 属性不再生效 |
| display-only | boolean | false | 是否开启仅展示模式 |
| hide-required-asterisk | boolean | false | 是否隐藏必填字段的标签旁边的红色星号 |
| inline | boolean | false | 行内布局模式 |
| inline-message | boolean | -- | 当 validate-type 设置为 text 时，是否以行内形式展示校验信息(推荐使用 message-type 设置) |
| label-align | boolean | false | 当出现必填星号时，标签文本是否对齐，当 label-position 为 'right' 时有效 |
| label-position | 'right' \| 'left' \| 'top' | 'right' | 表单中标签的布局位置 |
| label-suffix | string | -- | 表单中标签后缀 |
| label-width | string | '84px' | 表单中标签占位宽度 |
| message-type | 'inline' \| 'block' \| 'absolute' | 'block' | 当 validate-type 设置为 text 时，配置文本类型错误类型，可配置行内或者块级，其他值都为 absolute 定位 |
| model | { [prop: string]: any } | -- | 表单数据对象 |
| overflow-title | boolean | false | 标签超长是否显示提示 |
| popper-options | Popover.IPopperOption | -- | 校验错误提示配置，透传至 Popover 组件 |
| rules | { [prop: string]: IFormRules \| IFormRules[] } | -- | 表单验证规则 |
| show-message | boolean | true | 是否显示校验错误信息 |
| size | 'medium' \| 'small' \| 'mini' | -- | 表单内组件的尺寸，不设置则为默认尺寸 |
| validate-on-rule-change | boolean \| "deep" | true | 是否在 rules 属性改变后立即触发一次验证（"deep"选项新增于3.21.0） |
| validate-position | IFormPosition | 'right' | 指定校验提示框显示的位置 |
| validate-type | 'tip' \| 'text' | 'tip' | 校验类型 |

## Events

| 事件名称 | 事件类型 | 事件说明 |
| :--- | :--- | :--- |
| validate | (prop: string, isValid: boolean, message: string) => void | 任一表单项被校验后触发 |

## Methods

| 方法名称 | 方法类型 | 方法说明 |
| :--- | :--- | :--- |
| clearValidate | (prop: string \| string[]) => void | 移除表单项的校验结果，可传入待移除的表单项的 prop ，或者 prop 组成的数组，如不传则移除整个表单的校验结果 |
| resetFields | () => void | 对整个表单进行重置，将所有字段值重置为初始值并移除校验结果 |
| validate | IFormValidateMethod | 对整个表单进行校验的方法，参数为一个回调函数（该回调函数会在校验结束后被调用，并传入两个参数：1、是否校验成功 2、未通过校验的字段）返回一个 promise |
| validateField | IFormValidateFieldMethod | 对部分表单字段进行校验的方法, 第一个参数为单个 prop 或者 prop 数组，第二个参数是回调函数，每个表单项检验完后会依次调用该回调 |

## Slots

| 插槽名称 | 插槽说明 |
| :--- | :--- |
| default | 默认插槽，自定义表单内容 |

## 表单项组件 - TinyFormItem

### Props(TinyFormItem)

| 属性名称 | 属性类型 | 默认值 | 属性说明 |
| :--- | :--- | :--- | :--- |
| error | string | -- | 表单项错误文本，设置该值会使表单验证状态变为 error |
| extra | string | -- | 表单项额外提示 |
| inline-message | boolean | -- | 是否以行内形式展示校验信息(推荐使用 message-type 设置) |
| label | string | -- | 标签文本 |
| label-width | string | '80px' | 表单域标签的的宽度 |
| message-type | 'inline' \| 'block' | -- | 配置文本类型错误类型，可配置行内或者块级，不配置则为 absolute 定位 |
| prop | string | -- | 对应表单域 model 字段，如需使用表单校验，该属性是必填的 |
| required | boolean | false | 是否必填，如不设置，则会根据校验规则自动生成 |
| rules | IFormRules | -- | 表单项验证规则 |
| show-message | boolean | true | 是否显示校验错误信息 |
| size | 'medium' \| 'small' \| 'mini' | -- | 用于控制该表单域下组件的尺寸，不设置则为默认尺寸 |
| validate-debounce | boolean | false | 是否开启校验防抖，在连续输入的情况下，会在最后一次输入结束时才开始校验 |
| validate-icon | Component | -- | 校验提示框的图标，类型为组件 |
| validate-position | IFormPosition | 'top-end' | 指定校验提示框显示的位置 |
| validate-type | 'text' \| 'tip' | 'tip' | 校验提示显示类型 |

### Methods(TinyFormItem)

| 方法名称 | 方法类型 | 方法说明 |
| :--- | :--- | :--- |
| clearValidate | () => void | 移除该表单项的校验结果 |
| resetField | () => void | 对该表单项进行重置，将其值重置为初始值并移除校验结果 |

### Slots(TinyFormItem)

| 插槽名称 | 插槽说明 |
| :--- | :--- |
| default | 默认插槽 |
| error | 错误提示内容 |
| label | 标签文本的内容 |

## 低代码应用示例

```Json
{
  "componentName": "TinyForm",
  "props": {
    "labelWidth": "80px",
    "labelPosition": "top",
    "validate-type": "text",
    "inline": true,
    "label-position": "left",
    "className": " search-filter"
  },
  "children": [
    {
      "componentName": "TinyFormItem",
      "props": {
        "label": "名称"
      },
      "children": [
        {
          "componentName": "TinyInput",
          "props": {
            "placeholder": "请输入",
            "modelValue": {
              "type": "JSExpression",
              "value": "this.state.inputValue",
              "model": true
            }
          },
          "id": "34428513",
          "show": true
        }
      ],
      "id": "3463df55",
      "show": true
    },
    {
      "componentName": "TinyFormItem",
      "props": {
        "label": "日期"
      },
      "children": [
        {
          "componentName": "TinyDatePicker",
          "props": {
            "type": "daterange",
            "modelValue": {
              "type": "JSExpression",
              "value": "this.state.dateRangeValue",
              "model": true
            },
            "value-format": "yyyy-MM-dd hh:mm:ss"
          },
          "id": "5352ed12",
          "show": true
        }
      ],
      "id": "23a64112",
      "show": true
    },
    {
      "componentName": "TinyFormItem",
      "props": {
        "label": ""
      },
      "children": [
        {
          "componentName": "Icon",
          "props": {
            "name": "wechat-fill"
          },
          "id": "5611c631",
          "condition": {
            "type": "JSExpression",
            "value": "this.state.showIcon"
          },
          "show": true
        },
        {
          "componentName": "TinyButton",
          "props": {
            "text": "查询",
            "type": "primary",
            "icon": {
              "componentName": "Icon",
              "props": {
                "name": "search-2-line"
              }
            },
            "onClick": {
              "type": "JSExpression",
              "value": "this.initData"
            }
          },
          "id": "14265332",
          "show": true
        },
        {
          "componentName": "TinyButton",
          "props": {
            "text": "重置",
            "type": "default",
            "onClick": {
              "type": "JSExpression",
              "value": "this.reset"
            }
          },
          "id": "2132d533",
          "show": true
        }
      ],
      "id": "32d28245",
      "show": true
    }
  ],
  "id": "41323245",
  "show": true
}
```
