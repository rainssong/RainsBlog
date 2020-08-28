# Unity解压Zip

.net 自带Zip工具System.IO.Compression.ZipFile，但是默认没有导入Unity。解决步骤：

1. Assets目录下新建csc.rsp
2. 粘贴

    ```
    -r:System.IO.Compression.dll
    -r:System.IO.Compression.FileSystem.dll
    ```

3. PlayerSetting里Api修改为 .net 4.x

但实际上这个工具有**巨大问题**

1. 没有覆盖选项，冲突就报错。
2. 在安卓下有Bug，解压一个文件后直接报错。

连微软里面都有混子程序员？

解决方案：改用SharpZipLib。不用nuget安装也没事，解压后dll拖到工程里。
