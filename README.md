##  《ASM4 使用指南》| 沉淀、分享、成长，让自己和他人都能有所收获！

> 本文档是作者小傅哥从网上资料获取整理，方便学习使用。ASM 是一个 Java 字节码操控框架。它能被用来动态生成类或者增强既有类的功能。ASM 可以直接产生二进制 class 文件，也可以在类被加载入 Java 虚拟机之前动态改变类行为。如果本文能为您提供帮助，请给予支持(关注、点赞、分享)！

> 小傅哥，Java Developer，[:trophy:CSDN 博客专家](https://bugstack.blog.csdn.net)，[:pencil2:GitChat专栏作者](https://gitbook.cn/gitchat/column/5e5d29ac3fbd2d3f5d05e05f)

<div align="center">
<a href="https://github.com/MyGitBooks/asm"><img src="https://badgen.net/github/stars/MyGitBooks/asm?icon=github&color=4ab8a1"></a>
<a href="https://itstack.org/_media/qrcode.png?x-oss-process=style/may"><img src="https://badgen.net/github/forks/MyGitBooks/asm?icon=github&color=4ab8a1"></a>
<a href="http://asm.itstack.org" target="_blank"><img src="https://asm.itstack.org/_media/onlinebook.svg"></a>
<a href="https://itstack.org/_media/qrcode.png?x-oss-process=style/may"><img src="https://itstack.org/_media/wxbugstack.svg"></a>
</div>
<br/>

<br/>
<div align="center">
    <a href="http://asm.itstack.org" style="text-decoration:none"><img src="http://asm.itstack.org/_media/tree.png" width="128px"></a>
</div>
<br/>  

* :memo: 目录
    * [第 1 章 - 引言](/docs/notes/1引言.md)
    * `第一部分 核心 API`
    * [第 2 章 - 类](notes/2.0类.md) 
        * [2.1 结构](notes/2.1结构.md)    
        * [2.2 接口和组件](notes/2.2接口和组件.md)    
        * [2.3 工具](notes/2.3工具.md)    
    * [第 3 章 - 方法](/docs/notes/3.0方法.md) 
        * [3.1 结构](/docs/notes/3.1结构.md)    
        * [3.2 接口和组件](/docs/notes/3.2接口和组件.md)    
        * [3.3 工具](/docs/notes/3.3工具.md)    
    * [第 4 章 - 元数据](/docs/notes/4.0元数据.md)     
        * [4.1 泛型](/docs/notes/4.1泛型.md)    
        * [4.2 注释](/docs/notes/4.2注释.md)    
        * [4.3 调试](/docs/notes/4.3调试.md)   
    * [第 5 章 - 后向兼容](/docs/notes/5.0后向兼容.md)
        * [5.1 引言](/docs/notes/5.1引言.md)    
        * [5.2 规则](/docs/notes/5.2规则.md)    
    * `第二部分 树 API`   
    * [第 6 章 - 类](/docs/notes/6.0类.md) 
        * [6.1 接口和组件](/docs/notes/6.1接口和组件.md)        
        * [6.2 组件合成](/docs/notes/6.2组件合成.md)        
    * [第 7 章 - 方法](/docs/notes/7.0方法.md)  
        * [7.1 接口和组件](/docs/notes/7.1接口和组件.md)   
        * [7.2 组件合成](/docs/notes/7.2组件合成.md)   
    * [第 8 章 - 方法分析](/docs/notes/8.0方法分析.md) 
        * [8.1 介绍](/docs/notes/8.1介绍.md)   
        * [8.2 组件与接口](/docs/notes/8.2组件与接口.md)   
    * [第 9 章 - 元数据](/docs/notes/9.0元数据.md) 
        * [9.1 泛型](/docs/notes/9.1泛型.md)    
        * [9.2 注释](/docs/notes/9.2注释.md)    
        * [9.2 调试](/docs/notes/9.3调试.md)    
    * [第 10 章 - 后向兼容](/docs/notes/10.0后向兼容.md) 
        * [10.1 介绍](/docs/notes/10.1介绍.md)    
        * [10.2 规则](/docs/notes/10.2规则.md)      
    * [A. 附录](/docs/notes/A.0附录.md) 
        * [A.1 字节代码指令](/docs/notes/A.1字节代码指.md)
        * [A.2 子例程](/docs/notes/A.2子例程.md)
        * [A.3 属性](/docs/notes/A.3属性.md)
        * [A.4 规则](/docs/notes/A.4规则.md)
        * [A.5 性能](/docs/notes/A.5性能.md)

---

##  转载分享

建立本开源项目的初衷是基于个人学习与工作中对 Java 相关技术栈的总结记录，在这里也希望能帮助一些在学习 Java 过程中遇到问题的小伙伴，如果您需要转载本仓库的一些文章到自己的博客，请按照以下格式注明出处，谢谢合作。

```
作者：小傅哥
链接：https://bugstack.cn
来源：bugstack虫洞栈
```

## 与我联系

- **加群交流**
    本群的宗旨是给大家提供一个良好的技术学习交流平台，所以杜绝一切广告！由于微信群人满 100 之后无法加入，请扫描下方二维码先添加作者 “小傅哥” 微信(fustack)，备注：加群。
    
    <img src="https://itstack.org/_media/fustack.png?x-oss-process=style/may" width="180" height="180"/>

- **公众号(bugstack虫洞栈)**
    沉淀、分享、成长，专注于原创专题案例，以最易学习编程的方式分享知识，让自己和他人都能有所收获。目前已完成的专题有；Netty4.x实战专题案例、用Java实现JVM、基于JavaAgent的全链路监控、手写RPC框架、DDD专题案例、源码分析等。
    
    <img src="https://itstack.org/_media/qrcode.png?x-oss-process=style/may" width="180" height="180"/>

## 参与贡献

1. 如果您对本项目有任何建议或发现文中内容有误的，欢迎提交 issues 进行指正。
2. 对于文中我没有涉及到知识点，欢迎提交 PR。

## 致谢

感谢以下人员对本仓库做出的贡献，当然不仅仅只有这些贡献者，这里就不一一列举了。如果你希望被添加到这个名单中，并且提交过 Issue 或者 PR，请与我联系。

<a href="https://github.com/linw7">
    <img src="https://avatars0.githubusercontent.com/u/3761578?s=460&v=4" style="border-radius:5px" width="50px">
</a> 
<a href="https://github.com/g10guang">
    <img src="https://avatars0.githubusercontent.com/u/30902679?s=400&v=4" style="border-radius:5px" width="50px">
</a> 
<a href="https://github.com/g10guang">
    <img src="https://avatars1.githubusercontent.com/u/15908832?s=180&v=4" style="border-radius:5px" width="50px">
</a>
