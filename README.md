# frontendCodeStyleLint

- [frontendCodeStyleLint](#frontendcodestylelint)
  - [总览](#总览)
  - [技术比较](#技术比较)
  - [技术选择](#技术选择)
  - [技术细节](#技术细节)
## 总览

这是一个为了检查JavaScript,TypeScript以及其框架所写的代码质量，最终成果以网页和electron展现，提交代码或者提供仓库url获得检查报告。

## 技术比较

统计了几个比较常见的代码质量审查工具

1. `SonarQube`

+ 优点: 老牌，多语言，社区完善，支持CI和cli

+ 缺点：原罪Java编写，docker没有arm64版本，一键Pass

2. `Kritika`

+ 无cli一键pass

3. `CodeSonar`，JArchitect，Bandit

+ 没有JavaScript支持

4. `Codecov`

+ 在GitHub Action中最常见的代码质量检查工具(个人观点)，但是没有找到cli，难以做有效封装📦

5. `deepScan`

+ 缺点是支持JavaScript和TypeScript，but whatever，本来就只打算做前端的代码检查，正好合适，而且拿自己的项目实际使用了一下，效果还算不错，提供了一定的动态分析功能。

6. `ESlint`

+ 算是最常用的前端代码检查工具🔧了，`vue-cli`，`CRA`这些模版工具都会使用到，能有效的保证代码书写风格的统一，缺点是只能进行静态分析。

## 技术选择

+ 网页选择`vue-cli`提供的`Vue`模版构建
+ 代码质量检查工具使用`ESlint`+`deepScan`结合
+ 桌面版使用`electron`+`vue-cli-plugin-electron-builder`在原有基础上构建
+ 因为遇上cli可能不可避免的需要一定程度的后端，如果有，使用`docker`容器化

## 技术细节

1. 首先封装`ESlint`的cli，提供一套可视化的配置
2. 其次封装`deepScan`的cli