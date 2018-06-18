自动生成API文档
====================

我们需要使用sphinx-apidoc来代码文件生成对应rst文件，使用方法如下：

::

    $ sphinx-apidoc [options] -o outputdir packagedir [pathnames]

比如我们把源代码放在source文件夹的getYiyi文件夹里，要在source文件夹下生成rst文件，则需要运行如下命令：

::

    $ sphinx-apidoc -o ./ getYiyi

运行后会生成modules.rst和对应每个代码文件名rst文件。我们在index.rst里引用生成的modules文件即可以将生成的文档集成进来。



除此以外，我们还需要进行一些设置。

* 修改conf.py文件，将以下内容：

::

    #import os
    #import sys
    #sys.path.insert(0, os.path.abspath(''))

修改为：::

    import os
    import sys
    sys.path.insert(0, os.path.abspath('./getYiyi'))

这是为sphinx指定了保存Python代码的路径。

.. WARNING::
    Sphinx需要导入python模块来提取docstring，所以一定要记着加上 if __name__ == '__main__' 这一条件。

如果你还想添加查看源代码的功能，需要在extension里加入 ``'sphinx.ext.viewcode',``。

最后生成的结果如下：

.. image:: /images/source.JPG

文档内容可以在Indices and tables中进行检索。

.. image:: /images/index.JPG