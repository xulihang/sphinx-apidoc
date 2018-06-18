生成中文PDF
=================
Sphinx是将rst文件转为latex文件以生成pdf的，装好latex后，在项目目录下运行make latexpdf就可以生成了。

以下是一些注意事项，主要是conf.py的修改：

* 修改latex_elements里的preamble，添加ctex或者cjk宏包可以支持中文。
* 修改language可以更改默认的语言，在生成的tex文件中会使用renewcommand修改原来的日期等信息为对应语言的。但默认中文的章节名没有得到更改，可以用以下代码不显示英文的Chapter。注意latex里有很多斜杠，在python中需要在引号前加r以避免转义。

::

    'preamble': r'''
    \addto\captionsenglish{\renewcommand{\chaptername}{}}
    \usepackage[UTF8, scheme = plain]{ctex}
    ''',