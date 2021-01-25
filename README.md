# prettier-demo

## Install

```bash
npm i -D prettier
# or
yarn add -D prettier
```

## Configure

```yaml
tabs: 2 # 缩进的空格数量
useTabs: false # 使用tab缩进
semi: false # 分号结尾
singleQuote: true # 单引号
quoteProps: as-needed # 属性用引号, e.g. background: url('//s.png')
jsxSingleQuote: true # jsx使用单引号
trailingComma: none # 逗号结尾
bracketSpacing: true # 大括号的前后空格 { foo: 'bar' } or {foo: 'bar'}
jsxBracketSameLine: false # jsx标签的最后一个属性后面的'>'是否需要换行
arrowParens: avoid # 箭头函数的入参使用括号
htmlWhitespaceSensitivity: css # html的空格检测
vueIndentScriptAndStyle: true # script和style标签里的内容缩进
endOfLine: crlf # 文本文件结束的换行符风格, (like unix)lf:\n (ms)crlf:\r\n
embeddedLanguageFormatting: auto # 尝试检测语言并启用格式化
```

## VSCode Integration

需要安装扩展程序 [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

```bash
mkdir .vscode && touch .vscode/settings.json
```

配置 vscode 工作区的默认格式化工具以及保存立即格式化

```JSON
{
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true
}
```
