创建一个sphinx项目
======================

1. 首先，我们运行 **sphinx-quickstart** 来自动创建一个sphinx项目。

你会被问到一些关于项目设置的问题，其中需要注意的是，您需要启用autodoc扩展。

::

    Indicate which of the following Sphinx extensions should be enabled:
    > autodoc: automatically insert docstrings from modules (y/n) [n]: y
    > doctest: automatically test code snippets in doctest blocks (y/n) [n]:
    ...

如果您创建时没有选择启用autodoc，您也可以通过修改conf.py文件实现：需要修改extensions那个列表，加入以下内容：

::
    
    sphinx.ext.autodoc',


2. 运行如上命令后会生成一个文件夹，结构如下

::

    目录
    │  Makefile
    │  make.bat
    │
    ├─source
    │  │  conf.py
    │  │  index.rst
    │  │
    │  ├─_templates
    │  └─_static
    └─build

source文件夹是保存rst源文件的，build是保存生成的html和pdf等文件的，根据之前的设定，两个文件夹可以合并。

index.rst是项目的主文档，我们可以在其中的toctree里添加其它rst文件。

::

    .. toctree::
        :maxdepth: 2

        usage/installation
        usage/quickstart
        ... 

3. 生成文档。

在根目录下运行如下命令，可以选择不同的输出格式，比如以下命令会输出网页。

::

    make html

基本的sphinx项目介绍就是这样，我们下一步讲解如何从含有docstring的源代码文件生成API文档。
