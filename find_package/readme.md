## find_package 
用于查找包（通常是使用三方库），并返回关于包的细节（使用包所依赖的头文件、库文件、编译选项、链接选项等）

find_package命令的两种搜索模式：**模块模式（Module mode）**和**配置模式（Config mode）**

### 模块模式（Module mode）
在该模式下，Cmake会搜索一个名为Find<PackageName>.cmake的文件，其中<PackageName>为待搜索包的名称。

搜索路径的顺序依次是：

    从变量CMAKE_MODULE_PATH指定的路径中进行查找
    从Cmake安装路径中查找。Cmake会在其安装路径下提供很多.cmake文件，例如/XXX/cmake/Modules/目录下（不同的系统安装目录可能不一致）

如果找到文件Find<PackageName>.cmake，Cmake会读取并处理该文件，简而言之，它负责检查一些条件（如版本号是否满足等）是否满足，并在找到包后，返回给调用者一些变量，用以获取包的详细信息。

### 配置模式（Config mode）
该模式下，CMake会搜索<lowercasePackageName>-config.cmake文件或<PackageName>Config.cmake文件。如果find_package命令中指定了具体的版本，也会搜索<lowercasePackageName>-config-version.cmake或<PackageName>ConfigVersion.cmake文件，因此配置模式下通常会提供配置文件和版本文件（注意形式上要保持一致），并且作为包的一部分一起提供给使用者

**.cmake后缀文件的作用是什么？**

find_package的两种搜索模式都会按照一定规则从路径下搜索.cmake后缀的文件，两种模式下的.cmake文件作用都是为了给find_package命令的调用方返回有关包的信息（头文件路径、库文件路径、编译连接选项、版本信息等等）

//参考
CMake笔记--find_package 指定路径
https://blog.csdn.net/czwcc/article/details/128466000?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-0-128466000-blog-127473202.235^v35^pc_relevant_anti_vip_base&spm=1001.2101.3001.4242.1&utm_relevant_index=3