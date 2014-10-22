项目结构

两大组件（source sets）： main source code 和 test code. 它们分别在以下两个目录中：

src/main/
src/instrumentTest/
这两个目录里面，又分别有各自的代码源文件和资源文件。

java/
resources/
对于 Android plugin, 又有以下额外的目录：

AndroidManifest.xml
res/
assets/
aidl/
rs/
jni/
配置项目结构

根据Gradle文档说明，可以通过以下两个方法来重新配置项目结构。

sourceSets {
    main {
        java {
            srcDir 'src/java'
        }

        resources {
            srcDir 'src/resources'
        }
    }
}
或者：

sourceSets {
    main.java.srcDirs = ['src/java']
    main.resources.srcDirs = ['src/resources']
}
而Android的项目也类似，如下列所示：

android {
    sourceSets {
        main {
            manifest.srcFile 'AndroidManifest.xml'
            java.srcDirs = ['src']
            resources.srcDirs = ['src']
            aidl.srcDirs = ['src']
            renderscript.srcDirs = ['src']
            res.srcDirs = ['res']
            assets.srcDirs = ['assets']
        }
        instrumentTest.setRoot('tests')
    }
}
 

注：setRoot这个方法将所有src/instrumentTest目录下的文件及文件夹移到了tests/目录下。
