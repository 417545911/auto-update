
## 配置husky
> 虽然上面已经配置好了`eslint`、`preitter`与`stylelint`，但是还是存在以下问题  

  对于不使用`vscode`的，或者没有安装`eslint`、`preitter`与`styleline`插件的同学来说，就不能实现在保存的时候自动的去修复与格式化代码。

 这样提交到git仓库的代码还是不符合要求的。因此需要引入强制的手段来保证提交到`git`仓库的代码是符合我们要求的。
 
 `husky` 是一个用来管理`git hook`的工具，`git hook`即在我们使用`git`提交代码的过程中会触发的钩子。

### 安装依赖
```bash
pnpm add husky -D
pnpm set-script prepare "husky install" # 在package.json中添加脚本
pnpm prepare # 初始化husky,将 git hooks 钩子交由husky执行
```
> 注意：执行 pnpm install 时，没有额外参数，会自动执行 pnpm prepare脚本，npm和yarn这些管理器同理

- 然后使用`husky`命令添加`pre-commit`钩子，运行
```bash
pnpm husky add .husky/pre-commit "pnpm lint && pnpm format && pnpm lint:style"
```

