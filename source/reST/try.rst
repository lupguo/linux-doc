Sphinx 安装和使用
=================

概述
--------

reStructuredText（reST）是Docutils和Sphinx使用的默认纯文本标记语言。Docutils提供了基本的reStructuredText语法，而Sphinx扩展了它以支持其他功能。

Sphinx是一个工具，它将一组reStructuredText源文件转换为各种输出格式，自动生成交叉引用，索引等。也就是说，如果你有一个目录包含一堆reST格式的文档（可能还有docs的子目录）在那里，Sphinx可以生成一个组织良好的HTML文件排列（在其他目录中），以便于浏览和导航。但是从相同的来源，它也可以使用LaTeX生成PDF文件。

重点是手写文档，而不是自动生成的API文档。虽然也支持这种文档（它可以与手写内容自由混合），如果你需要纯API文档，请查看Epydoc，它也理解reST。

基本介绍
-------------

Sphinx
^^^^^^^^^^^^^^^^^^^^^

* sphinx-quickstart的脚本，设置了一个源目录，根据conf.py询问的几个问题创建了一个具有最有用配置值的默认值。
* ReStructuredText文档源的Sphinx集合的根目录称为源目录，目录还包含Sphinx配置文件conf.py（配置Sphinx如何读取源代码和构建文档）
* sphinx-apidoc的自动“API文档”生成器

reStructuredText指令
^^^^^^^^^^^^^^^^^^^^^

* toctree是一个reStructuredText 指令，一个非常通用的标记。
* 指令可以包含参数，选项和内容。
* 在指令名称后面的双冒号后直接给出参数。
* 每个指令决定它是否可以有参数，以及有多少参数。
* 参数后面的选项以“字段列表”的形式给出。这maxdepth是toctree指令的这种选择。
* 内容在空行后面跟随选项或参数。
* 每个指令决定是否允许内容以及如何处理内容。
* 指令的常见问题是内容的第一行必须缩进到与选项相同的级别。

reST文件扩展
^^^^^^^^^^^^^^^^^^^^^

由于reST源文件可以有不同的扩展名（有些人喜欢 .txt，有些人喜欢.rst- 扩展名可以配置 source_suffix），不同的操作系统有不同的路径分隔符，Sphinx抽象它们：文档名称总是相对于源目录，扩展名被剥离，和路径分隔符转换为斜杠

对于文件名的例子是index，library/zipfile或 reference/datamodel/types。请注意，没有前导或尾随斜杠

安装
-------

安装要求
^^^^^^^^^^^^

Sphinx至少需要运行Python 3.5，以及docutils和 Jinja2库。Sphinx应该使用docutils版本0.12或一些（未损坏的）SVN中继快照。

安装操作
^^^^^^^^^^^^
::

    // python3环境
    yum install python36 python36-pip

    // pip升级到最新版本pip
    pip3.6 install --upgrade pip

    // sphinx前置条件
    yum install python36-docutils.noarch python34-jinja2

    // clone
    git clone https://github.com/sphinx-doc/sphinx
    cd sphinx
    pip3.6 install .
    Successfully installed Jinja2 MarkupSafe Pygments Sphinx….

项目构建
------------

你现在可以填写主文档文件 ``./source/index.rst`` 并创建其他文档源文件了。用 ``Makefile`` 构建文档，像这样::

    make builder

此处的“builder”是支持的构建器名，比如 ``html、latex 或 linkcheck``。

调试部分
-----------

.. glossary::

   environment
      A structure where information about all documents under the root is
      saved, and used for cross-referencing.  The environment is pickled
      after the parsing stage, so that successive runs only need to read
      and parse new and changed documents.

   source directory
      The directory which, including its subdirectories, contains all
      source files for one Sphinx project.

参考
---------

.. [ ] PIP3安装:  https://pip.pypa.io/en/stable/installing/
.. [ ] Sphinx安装: http://www.sphinx-doc.org/en/master/usage/installation.html
.. [#] 入门:  http://www.sphinx-doc.org/en/master/usage/quickstart.html
.. [#] 官方网站: https://sphinx-themes.org/
.. [#] 默认主题: https://sphinx-themes.org/html/default/classic/index.html
.. [#] Sphinx主题: https://sphinx-rtd-theme.readthedocs.io/en/latest/index.html



