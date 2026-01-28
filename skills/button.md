# 按钮组件 - TinyButton

## props

| 属性名称 | 属性类型 | 默认值 | 属性说明 |
| :--- | :--- | :--- | :--- |
| autofocus | boolean | `false` | 是否默认聚焦 |
| circle | boolean | `false` | 是否圆形按钮 |
| disabled | boolean | `false` | 是否被禁用按钮 |
| ghost | boolean | `false` | 是否幽灵按钮 |
| icon | Component | `--` | 按钮左侧展示的图标，接收为 `Icon` 组件 |
| loading | boolean | `false` | 是否加载中状态 |
| native-type | `'button' \| 'submit' \| 'reset'` | `'button'` | 对应按钮原生 `type` 属性 |
| plain | boolean | `false` | 是否朴素按钮 |
| reset-time | number | `1000` | 设置按钮禁用时间，防止重复提交，单位毫秒 |
| round | boolean | `false` | 是否圆角按钮 |
| size | `'large' \| 'medium' \| 'small' \| 'mini'` | `--` | 定义按钮尺寸 |
| text | string | `--` | 按钮显示的文本 |
| type | `IButtonType` | `'default'` | 展示按钮不同的状态，设置为 `text` 则展示为文本按钮 |

## Events

| 事件名称 | 事件类型 | 事件说明 |
| :--- | :--- | :--- |
| click | `(event: MouseEvent) => void` | 点击按钮时触发 |

## Slots

| 插槽名称 | 插槽说明 |
| :--- | :--- |
| default | 默认插槽，自定义按钮展示内容 |

## 低代码应用示例

```Json
{
  "componentName": "TinyButton",
  "props": {
    "text": "登录",
    "className": "login-button",
    "onClick": {
        "type": "JSExpression",
        "value": "this.onLogin"
    }
  },
  "id": "8"
},
```
