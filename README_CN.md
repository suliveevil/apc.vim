# Vim 补全自动弹窗

这是一个给类似`YouCompleteMe` 浏览 `buffer`, `dictionary` , `tags` 提供服务的简短的脚本。

## 作用

语义补全是很好的，但有时当你正在费劲的敲一段没有 LSP 支持的代码, 或者你正在一个临时系统上工作。
你不会想把时间浪费在安装笨重的补全引擎、配置后端服务器上。

这种场景下，Vim 自带的补全就很适合你,。它从 Buffer 和 ctags 文件读取关键词，你只需要按 `<c-n>` or `<c-x><c-k>` 即可。

这脚本会在你输入一两个字符之后就帮你触发一个补全菜单，就像 `YouCompleteMe`一样:

![](https://skywind3000.github.io/images/p/auto-popmenu/demo.gif)

## 功能

- 自动弹出补全菜单.
- `Tab` 或者 `shift`+`TAB` 浏览选项, `<c-e>` 撤销.
- 体验上和 `YouCompleteMe` 对 `buffer`, `dict` 和 `tags` 所做的一样.
- 绿色, 只对当前 buffer 有效, 不会污染你的 vim 设置或者其他插件.
- 可以和其他补全插件一起使用.
- 没有笨重的引擎，不需要搭建后端服务器.
- 比 `AutoComplPop`更快更易上手.
- 便携, 只有一个`apc.vim` 脚本.
- 只有 **169 行代码**, 你甚至可以直接放进你的 `vimrc` 里.
- 是大型补全插件的简易备用方案.

## 使用

你只需要:

```VimL
Plug 'skywind3000/vim-auto-popmenu'

" 设置支持的文件类型, '*' 设置全部.
let g:apc_enable_ft = {'text':1, 'markdown':1, 'php':1}

" source for dictionary, current or other loaded buffers, see ':help cpt'
set cpt=.,k,w,b

" don't select the first item.
set completeopt=menu,menuone,noselect

" suppress annoy messages.
set shortmess+=c
```

还可以添加字典库:

```
Plug 'skywind3000/vim-dict'
```

完成！

## 命令

### ApcEnable

如果你还没设置 `g:apc_enable_ft` 的话，可以用这条命令手动对当前 buffer 开启脚本功能.

### ApcDisable

对当前 buffer 关闭脚本功能.

## 协作

如果你正在用 `YouCompleteMe`, 关闭 ycm 的以下文件类型:

```VimL
let g:ycm_filetype_blacklist = {'text':1, 'markdown':1, 'php':1}
```

打开 apc 的这些文件类型:

```VimL
let g:apc_enable_ft = {'text':1, 'markdown':1, 'php':1}
```


## Credit

- https://github.com/othree/vim-autocomplpop.
