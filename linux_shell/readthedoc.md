## Read the docs 环境搭建

**托管技术文档**

[quote](https://blog.csdn.net/u010386121/article/details/83274964)

使用python(Sphinx)将reStructuredText(markdown)生成html文件；使用github创建repo上传，使用ReadTheDocs账号，从github导入生成网站；

将文档托管到版本控制系统比如github上面，push源码后自动构建发布到readthedoc上面， 这样既有版本控制好处，又能自动发布到readthedoc；

Sphinx + GitHub + ReadtheDocs 作为文档写作工具，用 Sphinx 生成文档，GitHub 托管文档，再导入到 ReadtheDocs。

Sphinx（斯芬克斯）是一个基于Python的文档生成项目。最早只是用来生成Python的项目文档，但随着这个项目的逐渐完善，很多非Python的知名项目也采用Sphinx作为文档写作工具，甚至完全可以用Sphinx来写书。

```shell
sudo apt-get install python-sphinx tree
#pip install sphinx
pip install sphinx_rtd_theme
pip install recommonmark #支持markdown
pip install sphinx-markdown-tables

cd /home/akingse/Alluser/my-sphinx
sphinx-quickstart #创建工程
tree -C
```

> Separate source and build directories (y/n) [n]:y
> Project name: sp_test
> Author name(s): akingse
> Project version []: 1.0
> Project release [1.0]: 1.0
> Project language [en]: zh_CN

build是生成的文件，source是源码。source文件夹里面conf.py是read the docs的配置文件。 _static是放置一些图片或者其他文件。index.rst是网站首页。

conf.py #修改为经典风格，支持markdown

```python
import sphinx_rtd_theme
html_theme = 'sphinx_rtd_theme'
html_theme_path = [sphinx_rtd_theme.get_html_theme_path()]


from recommonmark.parser import CommonMarkParser
source_parsers = {
    '.md': CommonMarkParser,
}
source_suffix = ['.rst', '.md']
```

```shell
make clear
make html
```





---

## 从入门到放弃

[quote](https://www.oschina.net/p/readthedocs)

[Sphinx 使用手册](https://zh-sphinx-doc.readthedocs.io/en/latest/index.html)

[案例](https://industrial-training-master.readthedocs.io/en/kinetic/#)

[ros-I](https://rosindustrial.org/ric)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201011000659199.jpg#pic_center)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201011000719818.png#pic_center)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201011000814424.png#pic_center)

---

## 我觉得我又行了

[感谢](https://learnblockchain.cn/docs/etherscan/sphinx.html#markdownrest)

sphinx配置文件 conf.py

```python
import recommonmark
from recommonmark.transform import AutoStructify
import sphinx_rtd_theme

project = 'sp_test'
copyright = '2020, akingse'
author = 'akingse'
release = '1.0'
language = 'zh_CN'
html_search_language = 'zh_CN'
# exclude_patterns = ['_build', 'Thumbs.db', '.DS_Store']

extensions = ['recommonmark','sphinx_markdown_tables']
templates_path = ['_templates']
html_static_path = ['_static']

html_theme = 'sphinx_rtd_theme'
html_theme_path = [sphinx_rtd_theme.get_html_theme_path()]

#公式支持
github_doc_root = 'https://github.com/lbc-team/etherscan-docs/tree/master/source/'
def setup(app):
    app.add_config_value('recommonmark_config', {
            'url_resolver': lambda url: github_doc_root + url[:-4],
            'auto_toc_tree_section': 'Contents',
            }, True)
    app.add_transform(AutoStructify)


```

目录索引文件 index.rst

```
.. toctree::
   :maxdepth: 2
   :caption: Contents:

   exmple
   文件夹名/文件
```

`.. toctree::` 声明了一个树状结构（toc 即 Table of Content），

`:maxdepth: 2` 表示目录的级数（页面最多显示两级），

`:caption: Contents:` 用于指定标题文本

[quote](https://blog.csdn.net/lu_embedded/article/details/109006380)

```
    Makefile：可以看作是一个包含指令的文件，在使用 make 命令时，可以使用这些指令来构建文档输出。
    build：生成的文件的输出目录。
    make.bat：Windows 用命令行。
    _static：静态文件目录，比如图片等。
    _templates：模板目录。
    conf.py：存放 Sphinx 的配置，包括在 sphinx-quickstart 时选中的那些值，可以自行定义其他的值。
    index.rst：文档项目起始文件。
```



### 上传项目至github

github新建repo（my-readthedocs）,将 整个项目 下的文件上传至github

github引导

```shell
https
https://github.com/akingse/my-readthedocs.git
#create a new repo 通过命令行
echo "# my-readthedocs" >> README.md
echo "build #" >> .gitignore #表示不跟踪 build 目录，因为我们后面将使用 Read the Docs 进行文档的构建和托管。
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/akingse/my-readthedocs.git
git push -u origin main #账号密码

#push
git remote add origin https://github.com/akingse/my-readthedocs.git
git branch -M main
git push -u origin main

```

添加.gitignore重新push

```shell
git rm -r --cached .
git add .
git commit -m "update .gitignore"
git branch -M main
git push -u origin main
```

###  导入到 ReadtheDocs

在 Read the Docs 网站 https://readthedocs.org/ ,sign in使用 GitHub 账户。

Import a Project （图片验证太难了，火狐验证成功）

修改一个独一无二的项目名

构建失败，github使用main取代了master

git checkout --force master

---

![image-20201115084151480](/home/akingse/.config/Typora/typora-user-images/image-20201115084151480.png)



