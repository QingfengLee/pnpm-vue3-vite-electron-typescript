在很多应用场景中，我们同一套逻辑应用，但是需要适配不同的端，例如web端、electron客户端，以及各种设备等，该项目针对该需求，创建脚手架，方便开始一个新的项目
## 安装pnpm
```
npm install -g pnpm
```
## 开始创建目录
目录的创建尽量使用脚手架，减少配置工作项
```
pnpm create vite
```
按照步骤创建相关脚手架，同时删除无用的代码文件，添加monorepo配置文件`pnpm-workspace.yaml`
```yaml
packages:
  - 'apps/*'
```

## 创建各个枝干
创建apps目录，在目录执行下面指令，创建vue3-web-demo项目
```
pnpm create vite
```
在目录中执行下面指令，创建vue3-electron-demo项目
```
pnpm create electron-vite
```
# 修改根目录`package.json`
修改`package.json`文件，方便在根目录中执行相关指令
```json
{
  "name": "pnpm-vue3-vite-electron-typescript",
  "private": true,
  "version": "0.0.0",
  "scripts": {
    "dev:vue3-web-demo": "vite apps/vue3-web-demo",
    "dev:vue3-electron-demo": "cd apps/vue3-electron-demo && vite",    
    "build:vue3-web-demo": "vite build apps/vue3-web-demo",
    "build:vue3-electron-demo": "cd apps/vue3-electron-demo && vite build"
  },
  "dependencies": {
    "vue": "^3.2.47"
  },
  "devDependencies": {
    "@vitejs/plugin-vue": "^4.1.0",
    "typescript": "^4.9.3",
    "vite": "^4.2.0",
    "vue-tsc": "^1.2.0"
  }
}
```
## 抽取公共组件库
可以在外层抽取相关共同逻辑，放到common文件夹中。
## 运行指令
安装相关依赖库
```
pnpm install
```
启动web demo
```
pnpm dev:vue3-web-demo
```
启动electron demo
```
pnpm dev:vue3-electron-demo
```