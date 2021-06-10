################
前言
################

地图投影是个很复杂的东西,网上和书本上能讲清楚的不多,这块涉及到很多数学原理和制图相关知识,枯燥而且繁复.
以前网络上有一个很好的教程,即 MapProjection_ ,作者是 Carlos A. Furuti,图文并茂,特别详细,
但是从19年开始网站没有维护,已经无法访问了,我最近从 archive.org 上把老版本的介绍下载了下来,准备进行翻译和整理,
实际也就是先机翻在改改,肯定会有部分偏差和翻译错误,全文是第一人称,翻译中没有做修改

机翻用DeepL和搜狗,虽然DeepL吹的很厉害,但是大部分时候搜狗翻译的更通顺些,可能是专有名词多吧

如果只是想了解各种世界地图,可以参考 `世界地图投影 <http://michaelminn.net/tutorials/gis-projections-world/>`_ ,
如果想了解投影基础概念,可以看一下 `这篇介绍 <http://michaelminn.net/tutorials/gis-projections/index.html>`_

翻译时的增补
++++++++++++++++

在进行翻译之前添加了一个WKT的投影说明,为了方便平常的查阅和使用,毕竟日常使用主要是用的WKT格式的投影,有
时间的话会加上一些说明,也加强一些自己的理解,wkt/wkb日常坑人。

因为本文写的比较早,部分技术更新导致部分内容过时(实际作者也在更新,但是18年网站没了),会加上部分译注.

文章中有部分提到历史插图会添加插图说明,不一定全是原文中的图片,会有增加,因为网站已经无法访问,原文中有部分
缺失图片,如果有时间我会想办法加上

翻译不是特别准,毕竟是机翻改的,而且投影这块有些专业词汇我也很久没用了,不是特别熟悉，如果有什么翻译建议可以在issue里提出

.. _MapProjection: http://www.progonos.com/furuti/index.html
