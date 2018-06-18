ApiDoc使用的指令
====================

打开生成的代码的rst文件，可以看到如下内容：

::

    getYiyi
    ==============

    .. automodule:: getYiyi
        :members:
        :undoc-members:
        :show-inheritance:

automodule指令会自动生成所有的class、function和exception等内容。可以在它下面的members里指定要生成的对象。 使用 ``:undoc-members:`` 后，没有docstirng的部分也会得到处理。 ``:show-inheritance:`` 用来显示基类的信息。

使用如下的autoclass ::

    .. autoclass:: Noodle
        :members:

则不会对私有的方法（以_开始和结束）做处理。如果要记录私有的方法和属性，可以使用 ``:private-members:``。要记录特殊对象（以__开始和结束），可以使用 ``:special-members:``。

更多参见sphinx官网：http://www.sphinx-doc.org/en/master/ext/autodoc.html
