###为什么存在这项目
---
和《OpenGL ES 3.0编程指南(原书第2版)》配套，方便初学者在Windows平台构建学习OpenGL/OpenGL ES的开发环境。

* opengles3：sln工程。
* opengles3-book：《OpenGL ES 3.0编程指南》附带的源码，Git自https://github.com/danginsburg/opengles3-book。

###Git后如何使用
---
* 安装Visual Studio。opengles3中的sln是用Visual Studio 2015 + Update3生成，比它低版本的打开可能会失败，那需要自个新建sln，如何新建见底下的“新建sln”。
* 下载OpenGL ES SDK。opengles3.sln设置的是adreno：https://developer.qualcomm.com/download/adrenosdk。
* 打开opengles3/opengles3.sln
* 确保配置管理器中的Configuration选择Debug，Platform选Win32。如果想用其它配置，像Debug、x64，那需要自个去设头文件、库文件这些。
* 根据自个Adreno SDK安装路径修改项目中的lib路径。方法：“Linker”——“General”，“Additional Library Directories”，把“C:\Users\ancientcc\Desktop\AdrenoSDK\Development\Lib\Win32”改为您PC上的路径。
* 编译。成功后“Debug”——“Start Debuging”，就能看到执行结果。
* 如果其想换为其它章节源码，只要把那一源码对应的“.c”加入Source Files，把之前的“.c”移除或“Excluded From Build”设为“Yes”。

###新建sln
---
* 运行Visual Studio，“New”——“Project”，选择“Win32 Console Application”。假设工程名是opengles3。
* “Add”——“New Filter”，命名为“common”。把opengles3-book/Common/Source下的esShader.c、esShapes.c、esTransorm.c、esUtils.c，以及win32/esUtil_win32.c加入“common”。
* “C/C++”——“General”，“Additional Include Directories”增加“../opengles3-book/Common/Include”，“../opengles3-book/External/Include”。
* “Linker”——“General”，“Additional Library Directories”增加Adreno的lib路径“C:\Users\ancientcc\Desktop\AdrenoSDK\Development\Lib\Win32”。
* “Linker”——“Input”，“Additional Dependencies”增加“libEGL.lib、libGLESv2.lib”
* 编译。为让直接在Visua Studio运行，需要复制两部分文件。1）Adreno下的“libEGL.dll、libGLESv2.dll、TextureConverter.dll”复制到opengles3.exe同级目录。2）Adreno下的driver目录复制到opengles3.exe同级目录。