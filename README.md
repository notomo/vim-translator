# vim-translate-me

[@English Readme@](./README_en.md)

Vim/Neovim 翻译插件

支持弹窗(floating & popup)和异步特性

## 预览

<div align="center">
	<img src="https://user-images.githubusercontent.com/20282795/60756783-78fb7600-a034-11e9-8e3c-e9d098910077.gif">
</div>
<div align="center">
	<img src="https://user-images.githubusercontent.com/20282795/60756784-79940c80-a034-11e9-8eec-401eab18a23a.gif">
</div>


## 安装

确保已经安装了 Python(2或3)

```vim
Plug 'voldikss/vim-translate-me'
```

## 特性

- 浮窗支持(floating & popup)
- 不会阻塞当前编辑
- 多种可选翻译引擎
- 保存和导出查询记录
- 支持代理(http, socks4, socks5)
- 不再需要 appid/appkey


## 配置

#### **`g:vtm_default_mapping`**

> 是否使用默认快捷键

- 默认：`1`

#### **`g:vtm_default_to_lang`**
 
> 默认翻译的目标语言

- 可选：参考[各 engine 支持语言列表](https://github.com/voldikss/vim-translate-me/wiki)

- 默认：`'zh'`

#### **`g:vtm_default_engines`**
 
> 默认翻译接口

- 可选：`'bing'`, `'ciba'`, `'google'`(可直连), `youdao`。可选多个

- 默认：`['ciba', 'youdao']`

#### g:vtm_proxy_url

> 代理地址，如 `let g:vtm_proxy_url = 'socks5://127.0.0.1:1080'`

- 默认：`''`

#### **`g:vtm_enable_history`**
 
> 是否保存查询历史记录

- 默认：1

#### **`g:vtm_max_history_count`**
 
> 保存查询记录的数目

- 默认：5000

#### **`g:vtm_history_dir`**

> 历史记录文件的目录

- 默认：插件根目录

## 快捷键

- 默认快捷键
    ```vim
    " <Leader>t 翻译光标下的文本，在命令行回显
    nmap <silent> <Leader>t <Plug>Translate
    vmap <silent> <Leader>t <Plug>TranslateV
    " Leader>w 翻译光标下的文本，在窗口中显示
    nmap <silent> <Leader>w <Plug>TranslateW
    vmap <silent> <Leader>w <Plug>TranslateWV
    " Leader>r 替换光标下的文本为翻译内容
    nmap <silent> <Leader>r <Plug>TranslateR
    vmap <silent> <Leader>r <Plug>TranslateRV
    ```

- 再次使用`<Leader>w`，光标跳到翻译窗口

- 按 `q` 键关闭翻译窗口

## 命令

#### `:Translate [[engine] {word}]`

使用 `engine` 翻译单词 `word `并在命令行回显

如果未指定 `engine`，使用 `g:vtm_default_engines`

#### `:TranslateW [[engine] [word]]`

用法同上，但在窗口中显示

#### `:TranslateR [[engine] [word]]`

用法同上，但会用翻译内容替换光标下单词

#### `:TranslateH`

导出历史记录

## 颜色高亮

下面是默认高亮配置，使用 `hi link` 配置自己喜欢的高亮

```vim
hi def link vtmQuery             Identifier
hi def link vtmParaphrase        Statement
hi def link vtmPhonetic          Special
hi def link vtmExplain           Comment
hi def link vtmPopupNormal       NormalFloat
```

## Change log

- 1.2.0 (2019-07-06): add multi-engine translation, change `g:vtm_default_engine` to `vtm_default_engines`
- 1.1.0 (2019-07-02): add popup support on vim81
- 1.0.0 (2019-07-01): refactor
    - support proxy(http, socks4, socks5)
    - doesn't need app key/secret anymore, remove `g:vtm_...app_key/app_secret`
    - remove `'baidu'` and `'yandex'`
    - remove `g:vtm_popup_window`, use `'floating'` as default, otherwise `'preview'`
    - rename `g:vtm_default_api` to `g:vtm_default_engine`
    - remove `g:vtm_preview_position`
    - new option: `g:vtm_enable_history`
    - new option: `g:vtm_max_history_count`
    - new option: `g:vtm_history_dir`
    - new command: `:TranslateH` to export translation history
    - change default engine to `'ciba'` or `'google'`
    - change default syntax highlight

## References

- [dict.vim](https://github.com/iamcco/dict.vim)
- [translator](https://github.com/skywind3000/translator)


## License

MIT
