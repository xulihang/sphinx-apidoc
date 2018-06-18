用restructuredText自己撰写文档
==================================

自动生成的API文档可能比较简单，我们会需要自己补充一些内容，这时就需要我们用restructuredText进行写作了。

restructuredText是Sphinx默认使用的写作语言，可以让我们像写代码一样来进行文档的创作。

段落
++++++++++++++
段落是rst中的基本单位，每个段落需要有一个空行分割。

行内标记
++++++++++++++

常见的行内标记有以下几个，用法非常简单。

* 一个星号: \*text\* 斜体
* 两个星号: \*\*text\*\* 粗体
* 反引号: \`\`text\`\` 表示等宽代码。


列表
++++++++++

无序列表用星号开头，有序列表可以用数字或者井号开头。

::

    * This is a bulleted list.
    * It has two items, the second
    item uses two lines.

    1. This is a numbered list.
    2. It has two items too.

    #. This is a numbered list.
    #. It has two items too.

定义列表则使用缩进来实现：

::

    term
        Description.

分级
++++++++++

rst使用以下形式表示标题：

::

    =================
    This is a heading
    =================

使用不同的符号表示不同的等级，但不限定每级使用什么符号。推荐使用如下标准：

* \# 用于部分
* \* 用于章节
* \= 一级标题
* \- 二级标题
* \^ 三级标题


代码块
+++++++++++++++

在段落后面加上::，代码需要空一行并缩进后输入在后面。默认支持python代码的高亮显示。我们也可以用code-block指令来引用代码。


代码测试块
+++++++++++

代码测试块不需要像代码块一样进行缩进：

>>> 1 + 1
2    

代码对象
++++++++++

我们可以通过以下方式来记录一个python函数：::

    .. py:function:: enumerate(sequence[, start=0])

        Return an iterator that yields tuples of an index and an item of the
        *sequence*. (And so on.)

结果：

.. py:function:: enumerate(sequence[, start=0])

   Return an iterator that yields tuples of an index and an item of the
   *sequence*. (And so on.)

除了 ``py:function`` ，还可以使用 ``py:class`` 和 ``py:method``。

我们可以用 ``:py:func:`` 角色来进行引用：::

    The :py:func:`enumerate` function can be used for ...

效果：:py:func:`enumerate`


指令
+++++++++++++++++++++++++++

Directives是Roles之外的另一个rst使用的显式标记，用以拓展它的功能。Directive block包含三个部分：参数（arguments），选项（options，一个rst语法表示的列表)，内容（content）。

它的结构通常是这样的：::

    +-------+-------------------------------+
    | ".. " | directive type "::" directive |
    +-------+ block                         |
            |                               |
            +-------------------------------+

比如插入一个图片：::

    .. image:: http://www.w3school.com.cn//i/eg_tulip.jpg

.. image:: http://www.w3school.com.cn//i/eg_tulip.jpg

插入一个危险提示：::

    .. DANGER::
        Beware killer rabbits!

.. DANGER::
    Beware killer rabbits!

插入一个csv表格：::

    .. csv-table:: Frozen Delights!
       :header: "Treat", "Quantity", "Description"
       :widths: 15, 10, 30

       "Albatross", 2.99, "On a stick!"
       "Crunchy Frog", 1.49, "If we took the bones out, it wouldn't be crunchy, now would it?"

.. csv-table:: Frozen Delights!
    :header: "Treat", "Quantity", "Description"
    :widths: 15, 10, 30

    "Albatross", 2.99, "On a stick!"
    "Crunchy Frog", 1.49, "If we took the bones out, it wouldn't be crunchy, now would it?"

sphinx给rst添加了一个toctree指令，用来安排目录。它可以连接不同的文件，使得我们可以把内容写在不同的文件里。::

    .. toctree::
        :maxdepth: 2

        usage/installation
        usage/quickstart
        ...

链接
+++++++++

使用以下代码可以在行内使用链接：::

    `Link text <https://domain.invalid/>`_ 

