|buildstatus| |Latest Version| |Supported Python Versions|

xdis
====

跨版本的python字节码反编译器和Marshal程序


介绍
------------

Python `dis`模块允许从相同版本的python编译文件（pyc或pyo）中反编译出
源码。但是不同版本的字节码呢？ 

这个包就是实现跨版本的反编译工具。它可以从不同版本的Python编译文件中
"marshal load"字节码。命令行例程*pydisasm*将按Python 3.6反汇编语法显
示反编译结果。 

此外，如果您需要修改和编写字节码，这里的例程可能会有所帮助。有一些例
程可以在Python的Code类型中打包和解压缩只读元组。对于Python 2和3之间的
互操作性，我们提供了我们自己的Code类型版本，并且我们提供了例程来降低
编写字节码文件的复杂性。 

此软件包还具有Python字节码幻数的广泛知识，包括Pypy和其他，以及如何从
`sys.sys_info`主版本，次版本和发行版本号转换为相应的魔术值。 

So如果你想编写跨版本的汇编程序或字节码级优化器，这个包也可能有用。除了
dis提供的各种指令分类之外，我们还有其他类别用于在这种字节码优化器中有用
的东西。 

该程序支持从Python 1.3到3.7版的字节码。该代码需要Python 2.4或更高版本
来运行，并且已经在许多Python版本上进行过测试。 

通过egg在python2.6版之前版本上安装时，请使用github上的python-2.4分支。


安装
------------

使用setup.py进行安装，按下列步骤进行：

::

    pip install -r requirements.txt
    pip install -r requirements-dev.txt
    python setup.py install # 可能需要sudo来执行
    # or if you have pyenv:
    python setup.py develop

也提供了GNU makefile文件来快速安装，命令是 :code:`make install` (可能
需要root用户或sudo权限) 。


测试
-------

::

   make check

软件包中也提供了一个GNU makefile来平滑设置运行正确的命令，并且从最快模
式到最慢模式的测试。

如果您已remake_ 安装，您可以看到执行的所有任务，包括通过 :code:`remake --tasks`
进行的测试。



用法
-----

运行

::

     ./bin/pydisasm -h

以获取运行帮助。


作为dis的替代品
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`xdis`还提供了一些作为`dis <https://docs.python.org/3/library/dis.html>`_模块
替代品的支持。当您想要使用Python 3.4或更高版本的改进API时，可能需要这样做。

例如：

>>> # 在Python 2 和 3 下执行
>>> import xdis.std as dis
>>> [x.opname for x in dis.Bytecode('a = 10')]
['LOAD_CONST', 'STORE_NAME', 'LOAD_CONST', 'RETURN_VALUE']

格式化反汇编产生的输出可能存在一些细微差别，或者我们如何显示编译器标志。
您可能会发现`xdis`输出的信息更丰富。


请参考
--------

* https://github.com/rocky/python-uncompyle6 : python字节码反编译器
* https://github.com/rocky/python-xasm : python字节码反编译器

.. _trepan: https://pypi.python.org/pypi/trepan
.. _debuggers: https://pypi.python.org/pypi/trepan3k
.. _remake: http://bashdb.sf.net/remake
.. |buildstatus| image:: https://travis-ci.org/rocky/python-xdis.svg
		 :target: https://travis-ci.org/rocky/python-xdis
.. |Supported Python Versions| image:: https://img.shields.io/pypi/pyversions/xdis.svg
.. |Latest Version| image:: https://badge.fury.io/py/xdis.svg
		 :target: https://badge.fury.io/py/xdis
