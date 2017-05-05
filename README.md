# eslint-config-presets

这是数云的 eslint 配置。如需以此模板定制自己的配置请参考[创建个人的 eslint 配置](#创建个人的-eslint-配置)。

## 安装

### 根据不同的项目类型安装对应的包

```bash
## 推荐使用 yarn 来安装包
## 如果使用 npm 的话：npm install --save-dev ...

## 所有的规则包都定义在 packages/ 中，每个规则包都有对应的规则入口
## 例如，对于 eslint-config-shuyun-react，package.json 中 `main` 指定的文件 index.yml:
##   extends: presets/react
## 那么，它的规则入口为 eslint-config-presets/react，即项目根目录的 react 文件

## 对于前端项目，如果其它几个包都不合适，就选择这个
yarn add -D eslint-config-shuyun

## nodejs 项目
yarn add -D eslint-config-shuyun-nodejs

## 使用 angular 的项目
yarn add -D eslint-config-shuyun-angular

## 使用 react 的项目
yarn add -D eslint-config-shuyun-react

## 使用 react-native 的项目
yarn add -D eslint-config-shuyun-react-native

## chrome 应用、扩展
yarn add -D eslint-config-shuyun-chrome
```

### 使用

安装的 preset 有两种使用方式：

假如你已经为使用 react 的项目安装了 `eslint-config-shuyun-react`（其中 `shuyun-react` 就是这个 preset 的名字），然后：

方式 1) 在 `package.json` 中添加 `eslintConfig` 属性：

```json
{
  "eslintConfig": {
    "extends": "shuyun-react"
  }
}
```

如有必要，也可以使用 `eslintConfig` 的 `rules` 属性来覆写 `shuyun-react` 中的某些规则，像这样：

```json
{
  "eslintConfig": {
    "extends": "shuyun-react",
    "rules": {
      "no-console": "off"
    }
  }
}
```

可以参考 <http://eslint.org/docs/rules/> 了解更多的规则。

方式 2) 在项目的根目录创建一个 eslint 的配置文件（例如 `.eslintrc.yml`）：

```yaml
extends: shuyun-react
```

这样就可以使用 `shuyun-react` 中的规则了。

## 创建个人的 eslint 配置

依照以下步骤即可以此为模板创建新的配置：

1. Fork 并 clone 到你本地，然后进入项目目录
2. 运行 `yarn` 安装本项目的依赖
3. 运行 `./scripts/rename-packages-after-fork.sh` 给你的包重新起名
4. 删减不需要的包及对应的文件，编辑 `rules/` 中的规则
5. 使用 git 提交所有的变更
6. 运行 `yarn run release -- major` 发布你的包，除了 `major` 以外，还可以选择 `minor` 或 `patch`，另外，在发布包之前请先 `npm login` 登录你的 npmjs.com 的帐号

任何相关的问题或讨论都可以在 issues 页提出，请不要犹豫或害羞。
