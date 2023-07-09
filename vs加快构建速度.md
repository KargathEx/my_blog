leetcode的本地工具每次编译都要一两秒太慢了，搜了一下加速的办法，因为印象笔记的markdown模式与普通笔记不通用，所以记录在这。  

### 提高编译速度
#### 设置
1.C/C++/代码生成，把启动最小生成选为“否”  
2.C/C++/常规，然后把多处理器编译选为“是”  
原因:
```
默认情况下“启用最小重建”处于启用状态，并且它与多处理器编译不兼容。我们需要将其关闭。再次强调，在进行此更改之前，请务必选择“所有配置”和“所有平台”。  

禁用最小重建的另一个原因是因为它没有（恕我直言）正确实施。如果您在 Linux 上使用 ccache，那么当缓存检测到可以跳过编译时，它仍然会发出相同的警告。VC++ 最小重建不会执行此操作，这使得消除警告变得更加困难。
```
[from](https://randomascii.wordpress.com/2014/03/22/make-vc-compiles-fast-through-parallel-compilation/)  

3.启用增量链接 :Linker/gen debug info/Generate Debug Information optimized for faster links (/DEBUG:FASTLINK)  
(缩短 Visual Studio 内增量开发人员循环的链接时间)  
4.关闭 CodeLens(for c++,用于单元测试)  


#### 代码优化
移动语义替代复制语义  
改成运行时读入，不让它重新编译。  
删掉无用的中间函数。  




#### 易用性插件
1.vs_buildtimer 检测性能瓶颈，已star.  
```
构建计时器记录构建每个项目所花费的时间，并创建以条形图显示的时间线。时间线让您可以看到：

建设时间较长的项目
项目之间的依赖关系，即一个项目在开始构建之前等待另一个项目。
颜色编码条指示哪些项目构建成功、失败或正在进行。
```
显示的是项目之间的关系，与 `msdn diagsession`这种精确到函数的东西不同，所以对我没用。  

2.Project System Tools 2022 同上，但不支持c++  
3.输出窗口:  
VSOutputEnhancer[1]不支持自定义output窗口，所以选中的行高亮会导致红色报错看着不舒服。  
VSColorOutput支持修改样式(我用的第一个)，但是即使有了64支持，依然根本安装不了。  


#### bitbucket
star:  单击右上角“克隆”按钮附近的省略号 (...) 按钮并选择“通知设置”，您将获得一个观看存储库的选项。  
查看自己的star: 右上角settings -> Personal settings -> Notifications -> You are watching -> Repository -> Manage  

加快编译速度的[分析文章](https://randomascii.wordpress.com/2014/03/22/make-vc-compiles-fast-through-parallel-compilation/
)，提到了一些`cl.exe`的内部机制。  
