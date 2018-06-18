使用Markdown
=========================

Markdown是比restructuredText更加轻量的标记语言。Sphinx支持用Markdown进行写作。

启用Markdown需要如下步骤：

1. 安装recommonmark：::

    pip install recommonmark

2. 添加如下内容到conf.py中：::

    source_parsers = {
    '.md': 'recommonmark.parser.CommonMarkParser',
    }

3. 添加Markdown的文件扩展名到配置文件的source_suffix变量：::

    source_suffix = ['.rst', '.md']