# prettier-demo

## Install

### install [prettier](https://prettier.io/docs/en/index.html)

```bash
npm i -D prettier
# or
yarn add -D prettier
```

## Configure

### [configure prettierrc](https://prettier.io/docs/en/configuration.html)

.prettierrc.yml

```yaml
# .prettierrc.yml
tabWidth: 2 # 缩进的空格数量
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

[.prettierignore](https://prettier.io/docs/en/ignore.html)

```conf
# npm
package-lock.json

# yarn
yarn.lock

# husky
.husky

# ignore files
*ignore

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

## Husky Integration

what is githooks ?[githooks - Hooks used by Git](https://git-scm.com/docs/githooks)  
[what is husky?](https://github.com/typicode/husky#readme)

## install husky v5

```bash
npm i -D husky@next
# or
yarn add -D husky@next
```

## initialize husky

package.json

```JSON
{
  // ...
  "scripts": {
    "postinstall": "husky install"
  },
  // ...
}

```

npx husky install

```bash
npm run postinstall
# or
yarn postinstall
```

tips: If the command runs successfully, you should see the following:  
husky - installing git hooks...
husky - done

and then the .husky folder is created in root as follow:

+.husky  
+&emsp;.gitignore

## add pre-commit hook

```bash
npx husky add .husky/pre-commit "npx prettier --write ."
# or
yarn husky add .husky/pre-commit "yarn prettier --write ."
```

if you are using window OS:

```bash
npx husky add .husky/pre-commit
```

and then you will see as follow:  
.husky  
&emsp;+.pre-commit

open the .pre-commit file and modify:

```
#!/bin/sh
. "$(dirname $0)/_/husky.sh"

npx prettier --write .
```

Try to make a commit:

```bash
git add .
git commit -m "Keep calm and commit"
```

# Lint-Staged Integration

安装 lint-staged

```bash
npm i -D lint-staged
# or
yarn add -D lint-staged
```

创建 lint-staged 配置文件

```bash
touch .lintstagedrc.yml
```

所有文件都使用 prettier 格式化

```yaml
# .lintstagedrc.yml
'*': 'prettier --write'
```

挂载 pre-commit 钩子

```bash
# .husky/pre-commit

#!/bin/sh
. "$(dirname $0)/_/husky.sh"

yarn lint-staged
```
