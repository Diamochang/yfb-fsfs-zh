# 如何构建《自由软件，自由社会》（有改动）

这里给出如何在自己的机器上构建此书的简单介绍。~~因作者经验有限，此文仅列出 GNU/Linux 发行版下的构建，~~ 欢迎各位增补。

## 在线 HTML 整站

这里使用的是`mkdocs`工具。直接使用 

```
sudo pip3 install mkdocs
```

安装即可，如果使用 Python 2.7，只需要替换成`pip`命令。

`mkdocs build --clean`

运行以上命令会在当前目录下生成`site`目录，里面就是生成的 HTML 文档了。

## 单个 HTML 页面

使用的是 Pandoc 工具。可以在 GNU/Linux 发行版的包管理器搜索并安装`pandoc`即可（Fedora 还需要安装`pandoc-pdf`）。

然后运行`make html`即可，此命令会调用 mkdocs 和 pandoc 来生成 HTML 整站和单页 HTML。

## EPUB 文件

如上文安装好 pandoc 之后，直接运行`make epub`即可，会在当前目录下生成`yfb-fsfs-zh.epub`文件。

如何在 Amazon Swindle（RMS 对 Kindle 的蔑称）上阅读？通过包管理器安装 [Calibre](https://calibre-ebook.com/) 这款软件（此软件亦支持 M$ Windows 和 macO$ 系统），然后将 epub 文件生成 mobi 文件导入阅读器即可。我们并不推荐在 Swindle 上阅读此书，但兼容 Swindle 格式可以让你看完此书后抛弃这个产品。~~编者：其实大陆读者已经不需要 Swindle 了，商城都关了那还用个蛋，最多盖泡面~~

## PDF 文件

这里使用了 TeX Live 2018 工具集，越新越好。Debian 和 Ubuntu 需要安装的包有 `texlive-xetex texlive-lang-chinese texlive-fonts-recommended lmodern texlive-fonts-extra fonts-liberation fonts-noto fonts-noto-cjk fonts-noto-unhinted fonts-noto-hinted librsvg2-binpdf2svg` Fedora 可以运行如下命令：

`sudo dnf -y install @"Authoring and Publishing" pandoc pandoc-pdf pandoc-citeproc texlive-textpos texlive-tocbibind texlive-framed  texlive-appendix texlive-tabulary texlive-fandol google-noto-cjk-fonts texlive-bigfoot`

这样可以安装必须的包。~~低于 Fedora 23（含）或 Debian 9 或 Ubuntu 16.04 的版本以及其他发行版可能需要安装 Fandol 系列字体，可以运行`install.fandol.sh`脚本安装。~~（编辑本已弃用 Fandol，详见 [Issue #1](https://github.com/Diamochang/yfb-fsfs-zh/issues/1)）

安装好后执行`make pdf`即可，会在当前目录下生成`yfb-fsfs-zh.pdf`文件。

## 在M$ Windows 和 macO$ 上构建

（以下部分完全由编者撰写）

在 Windows 和 macOS 上，Pandoc 的二进制安装文件可以在它的 GitHub 仓库[发行版页面](https://github.com/jgm/pandoc/releases)找到。可以下载 ZIP 压缩包，解压到指定目录并配置好环境变量，也可以使用 MSI 或 PKG 安装包便捷完成安装。

Windows 上的 Python 安装程序可以在 python.org 找到，不过在大陆建议挑一个你值得信赖的镜像站，如[清华大学 TUNA 协会的镜像站](https://mirrors.tuna.tsinghua.edu.cn/python/)。网络上有许多安装和配置 Python 环境的教程。

TeX Live 最新版本的下载在[这里](https://tug.org/texlive/acquire-netinstall.html)，Windows 直接下 exe 打开安装或者下载 ZIP 压缩包解压安装就行，macOS 须改用同一社区的另一个项目：[MacTeX](https://tug.org/mactex/)。
