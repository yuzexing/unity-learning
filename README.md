# Unity学习笔记


### 一、为什么要用雪碧图(Sprite)?

Unity官方教程的[2D基础](https://learn.unity.com/pathway/unity-essentials/unit/2d-essentials/tutorial/add-an-animated-pet?version=6)中，使用雪碧图制作宠物。

<img width="237" alt="image" src="https://github.com/user-attachments/assets/62b7c3bb-aa9f-409d-b96f-3fdb3b5bbfba" />

在Web开发中使用雪碧图可以减少Http的请求次数，显而易见的节省资源。但在Unity确实是没办法通过直觉想出雪碧图的明显优势。初步猜想在内存分配上有优势，但不论大图还是多个小图都是离散分配物理内存页，从而否定这一想法。

经过查询相关资料，得出以下结论：

- [ ] ** 减少Draw Call次数 **\
      不太懂什么是Draw Call，暂时理解为Web端的重绘重排。
- [x] ** 集中资源管理 **\
      虽然是集中资源管理，但是如果雪碧图其中一个小图需要更改样式，则需要重新生成整张图片，这应该算是一个弊端。
- [x] ** 加载更快 **\
      Unity加载纹理时，可以加载一整张雪碧图，不用分多次从硬盘和内存中加载。
      确实是有一定道理，但是必定会减少首次加载速度，其次该效果等价于多张图片的预加载功能，也并不是显著的优势。但单雪碧图在磁盘中可以是顺序存储，读取时可以大幅减少磁头寻道时间和旋转时间，属于微弱的速度提升。同理还可以减少磁盘碎片。
- [ ] ** 图集压缩优化 **\
      Unity支持对Sprite Atlas进行压缩优化，节省内存。此处不知道什么是Sprite Atlas，学到再补充。
- [ ] ** GPU优化 **\
      减少纹理对象数量，减少GPU内存占用。GPU属于知识盲区，待补充。
      
