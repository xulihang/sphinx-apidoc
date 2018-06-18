Docstring——将文档写在代码中
===========================

文档字符串（docstring）是书写在源代码中的文档，类似于注释。但它和注释及javadoc不一样，会在运行时中保留，这样在程序运行时也可以查看文档信息。

Python，Lisp和Julia等语言都支持这一功能。

在Python的交互式界面下，我们可以通过help()函数显示docstring。

::

    >>> import requests
    >>> help(requests.get)
    Help on function get in module requests.api:
    get(url, params=None, **kwargs)
        Sends a GET request.
        :param url: URL for the new :class:`Request` object.
        :param params: (optional) Dictionary or bytes to be sent in the query string for the :class:`Request`.
        :param \*\*kwargs: Optional arguments that ``request`` takes.
        :return: :class:`Response <Response>` object
        :rtype: requests.Response

Python中，docstring用三个引号引起来。位于文件开头则是对整个文件的说明。位于类或者函数下方则是对这两者的说明。

例如上面的代码显示的requests的get函数的说明在源代码中是这样保存的：


::

    def get(url, params=None, **kwargs):
        r"""Sends a GET request.
        :param url: URL for the new :class:`Request` object.
        :param params: (optional) Dictionary or bytes to be sent in the query string for the :class:`Request`.
        :param \*\*kwargs: Optional arguments that ``request`` takes.
        :return: :class:`Response <Response>` object
        :rtype: requests.Response
        """
        kwargs.setdefault('allow_redirects', True)
        return request('get', url, params=params, **kwargs)


我们可以分析一下docstring都由哪几部分组成。比如一个函数，一般由简介、参数、返回值和返回类型构成docstring的内容。

根据Python的\ `PEP 257 <https://www.python.org/dev/peps/pep-0257/>`_\ 标准，python文件一般都要求有docstring。Docstring作为注释，可以使代码更容易被别人读懂。同时它也能方便的在Python终端中被调用。

