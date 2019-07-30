vimcdoc
=======

Vim 中文文件計劃



# 補 充

2019-07-30:

參考這些網頁，把最新版本的手冊台灣中文化

[1]: https://playubuntu.blogspot.com/2013/10/vim.html	"Vim 中文用戶手冊（繁體字）"
[2]: http://jdev.tw/blog/5656/opencc-introduction	"用OpenCC快速、準確的簡繁互轉"
[3]: https://www.opencli.com/linux/linux-batch-rename-files	"Linux 批次修改大量檔案名稱"
[4]: https://github.com/chusiang/vimcdoc-tw





# 關 於

Vim (http://www.vim.org) 是一個功能非常強大，且具有很強擴充套件性的編輯器。而且 Vim
本身帶有一個完備的幫助系統。本專案的目的就是將 Vim 的這些文件翻譯成中文，以便更
多的人認識及更好地使用這個非常強大的編輯器。文件分成使用者手冊和參考手冊兩部分，
你既可以象使用教程那樣循序漸進，也可以快速地查閱來獲取幫助。

# 下 載

https://github.com/yianwillis/vimcdoc/releases 提供釋出版本的下載。

* PDF 使用者手冊和參考手冊
* tar.gz 包
* Win32 GB2312 版本和 UTF8 版本的中文自動安裝程式

# 安裝

## Vim 8.0 自帶軟體包支援

```shell
$ mkdir -p ~/.vim/pack/foo/start
$ cd ~/.vim/pack/foo/start
$ git clone git://github.com/yianwillis/vimcdoc.git
```

重啟 Vim。

其中 foo 可以是任何你自選的名字。

當然，如果不想用 git，也可用解壓下載的 tar.gz 包到 `~/.vim/pack/foo/start`。git
方式的好處可以隨時進行更新。

## Vundle

.vimrc 中加入：

```
Plugin "yianwillis/vimcdoc"
```

重啟 Vim 後執行 `:PluginInstall`。

## NeoBundle

.vimrc 中加入：

```
NeoBundle 'yianwillis/vimcdoc"
```

重啟 Vim 後執行命令 `:NeoBundleInstall`。

## Pathogen

```shell
$ cd ~/.vim/bundle
$ git clone git://github.com/yianwillis/vimcdoc.git
```

重啟 Vim。

## vim-plug

.vimrc 中加入:

```
Plug 'yianwillis/vimcdoc'
```

重啟 Vim 後執行命令 `:PlugInstall`。

## Linux 程式安裝

下載的 tar.gz 包括所有翻譯過的 vim 文件 (.cnx 檔案) 和相關的語法檔案和外掛。
先將其解壓縮：

```shell
$ tar zxvf vimcdoc-<version>.tar.gz
```

然後進入 vimcdoc-<version> 目錄並執行

```shell
$ ./vimcdoc.sh -i
```

就可以了。該安裝程式會自動識別 Vim 的安裝路徑，將中文的文件拷貝到相應的地方。原
有的英文文件不受影響。

預設安裝 vimcdoc.vim 外掛，設定預設幫助語言為中文。如果你不希望如此，可用

```shell
$ ./vimcdoc.sh -I
```

來代替。

這種方法對 root 和非 root 使用者都適用。但建議以 root 身份安裝。當以 root 身份安
裝時，檔案會被拷貝至 /usr/share/vim/vimfiles/doc 下。因此所有系統的使用者都可以使
用中文文件。如果你的 vim 是安裝在 /usr/local 下的話，你需要這樣設定 vim 的
runtimepath 選項：

```vim
:set rtp+=/usr/share/vim/vimfiles
```

你可以將上面的設定加入到你的 vimrc 檔案中以便每次啟動 vim 都生效。當以普通使用者
安裝時，所有檔案會被拷貝至 ~/.vim/doc 下，所以僅對該使用者有效。

## Win32 程式安裝

建議使用已經做好的自動安裝程式。該程式不寫登錄檔，不建立程式組，不覆蓋任何 Vim
原有檔案。所以可以放心使用。

## 手動安裝

你也可以自己動手來安裝：只要把所有的中文文件以及 tags-cn 檔案拷貝到 runtimepath
之一的 doc 子目錄下就行了。runtimepath 可用在 vim 內用 `:set rtp?` 命令來得到。比
如在 `vimcdoc-<version>` 目錄中，可以執行以下命令：

```shell
$ cp -R doc /usr/share/vim/vimfiles/doc
```

這種方法對 Linux 和 Win32 都有效。

現在啟動 vim/gvim, 鍵入 :help 看看吧！


# 卸 載

## Linux 程式安裝
如果你是使用的自動安裝指令碼安裝的話，只要執行：

```shell
$ ./vimcdoc.sh -u
```

即可。但必須用與安裝時同樣的使用者名稱 (root 使用者安裝程式會在
/usr/share/doc/vimcdoc 下安裝該檔案)。

## Win32 程式安裝

假定你的 Vim 安裝在 c:\vim 下，在 c:\vim\vimfiles\doc\ 目錄內會有一個
vimcdoc-Uninst.exe，只要執行它就可以了。

## 設 置

你的 'encoding' 設定及字型必須支援中文顯示。對於使用非 utf-8 中文環境的使用者，在
瀏覽某些幫助檔案的時候可能會遇到麻煩。這是因為那些檔案包含無法在 gbk, gb2312 等
編碼方式下顯示的字元。遇到這種情況，有以下幾種解決方案：

1. 使用 utf-8 中文環境。例如，將 `LC_ALL` 設定為 `zh_CN.UTF-8`
2. 強制 vim 使用 utf-8 編碼。做法是 `:set enc=utf-8`
3. 如果你的系統有 GB18030 支援，可以讓 vim 使用 GB18030 編碼，因為 GB18030 對非
   中文字元也能進行適當的處理。方法是

   ```vim
   :set enc=2byte-gb18030
   ```

   這時，Vim 會正確地進行轉換。注意這裡不能通過設定 `LC_ALL` 來完成。

如果使用 2 或 3，建議把 vim 設定寫入你的個人 .vimrc 設定檔案，避免每次都要輸入
命令的麻煩。

備註：如果 `set enc=utf-8` 時，使用的中文訊息出現亂碼，可以同時設定

```vim
:language message zh_CN.UTF-8
```

# 在 線 閱 讀

可線上閱讀幫助文件的 HTML 版。

http://yianwillis.github.io/vimcdoc/

為了最佳閱讀效果，請確保你的系統安裝了 NSimsun 字型，否則可能有字型不能完全對齊
的情況。

# 加 入

我們歡迎各種各樣的幫助，翻譯，測試，等等等等。如果你也想加入本專案的話，請直接
與我們聯絡 (見下)，同時請先行閱讀 guides.txt。

AUTHORS 列出了翻譯人員。

LICENSE 包括版權資訊。

# 信 息

歡迎訪問我們的主頁以獲取更多的資訊和最新的版本:

https://github.com/yianwillis/vimcdoc

這將是我們的新主頁。原版本 http://vimcdoc.sf.net (English) 的內容已經完整匯入。
以後的更新也只會在 github 進行。


# 聯 系

任何建議、問題等等，請送往 yianwillis@gmail.com。
