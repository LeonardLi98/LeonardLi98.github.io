# LENKE Blog

> 博客的搭建教程，来自 [Hux](https://github.com/Huxpro/huxpro.github.io)，以及[qiubaiying](https://github.com/qiubaiying/qiubaiying.github.io)

### [我的博客在这里 &rarr;](https://RongfanLi98.github.io/)

### 配置问题

#### Gitalk

主要问题在于如何写配置。  

在`_layouts\post.html`中，约85行，就是gitalk的配置内容。具体的配置见[gitalk](https://github.com/gitalk/gitalk#install)。这里主要是因为Jekyll的缘故，需要再多加配置。Jekyll会自动解析每篇文章的yaml部分，转换成[各种变量](http://jekyllcn.com/docs/variables/)，而这些变量将在解析HTML的时候被替换。  

然后是gitalk，配置过程中需要填写一些信息，因为评论是以issue的形式储存在GitHub上的，gittalk首先需要在GitHub上申请clientID，clientSecret，然后是仓库地址和拥有者之类的信息，都是储存在`_config`里面的。最后有个关键的问题是评论无法发表的问题，这个问题常见于`_layouts\post.html`下面的`new Gitalk`配置中的id，也就是会转变成GitHub的label的字段。由于GitHub的label长度不能超过50个字符，所以这里当标题太长时，就无法使用原blog里的`window.location.pathname`，而经过测试，发现issue的名字是博文的标题，所以实际上是没有必要label中再确认标题的。  

这里采用的解决方案是用`page.date`，在某一时间，发表的文章**应该**是唯一的，基于这种想法，可以用时间来唯一确定一个文章，这和label来筛选某一文章下的所有评论的作用是相同的。而这些issue的标题都是文章标题，非常显然。

还有其他办法，此处就不一一列举了。只要能将一个文章唯一确定下来，就是好的办法。

### 致谢

1. 这个模板是从 [Hux](https://github.com/Huxpro/huxpro.github.io) 和[qiubaiying](https://github.com/qiubaiying/qiubaiying.github.io)fork 的, 感谢这个他们。 
2. 感谢 Jekyll、Github Pages 和 Bootstrap!

### License

遵循 MIT 许可证。有关详细,请参阅 [LICENSE](https://github.com/qiubaiying/qiubaiying.github.io/blob/master/LICENSE)。

