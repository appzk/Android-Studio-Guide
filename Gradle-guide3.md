接续： Gradle（一） | Gradle（二）

通用任务

        将一个plugin运用到build file中时，会自动创建一系列的构建任务（build task）去运行。Java plugin和Android Plugin也都会如此。

我们对于任务的约定有以下四个：

        assemble任务，汇集所有项目输出     
        check任务，运行所有校验
        build任务，既汇集又校验        
        clean任务，清除所有项目输出
        assemble, check and build任务自己本身不做任何事情，它们只是plugin锚点，真正任务的是由plugin来添加执行。

这样做的好处是，不管你在什么项目中，你都可以调用同样的命令来执行。

        通过命令行，你可以得到更高级别的任务，命令如下：

gradle tasks
列出当前运行的所有任务，以及查看他们之间的依赖关系：

gradle tasks --all
注: Gradle会自动地检测一个任务中申明的输入和输出。当重复执行两次build任务时，Gradle会报告当前所有任务是UP-TO-DATE的状态。

 

Java项目的任务

        Java plugin会创建两个任务，分别挂到锚任务中，如下：

        assemble
                jar  This task creates the output.
        check
                test This task runs the tests.


jar任务是编译执行Java源代码。
test任务是运行unit test
 

通常，java项目中的任务只会用到assemble和check这两个,更多的其他task详见此处。



Android 任务

   Android的任务比通用的四大任务多了“connectedCheck”和“deviceCheck”，这是想要让项目忽视设备是否连接，正常执行check任务。

        assemble任务，  汇集所有项目输出
        check任务，运行所有校验
        connectedCheck任务，运行所有需要链接设备或模拟器的校验, 并行运行
        deviceCheck任务，运行调用远程设备的校验，运用于CI Servers
        build任务，既汇集又校验
        clean任务，清除所有项目输出
注：build任务不依赖与deviceCheck或connectedCheck

一个安卓的项目至少有两个输出，一是debug apk，二是release apk.这两个输出都有自己对应的锚任务，来实现它们各自的构建调用assemble任务时会同时调用assembleDebug和assembleRelease来保证有两个输出。

assemble
        - assembleDebug
        - assemblRelease
        Tip: Gradle 支持Camel命名方式的简写，比如在输命令行时，可以用aR代替assembleRelease，如果没有其他别的任务也是aR简写的话：

gradle  aR =  gradle assembleRelease
Check任务也有它们自己的依赖关系：

        check
                ---lint (目前还没实现，汗一个)

        connectedCheck
                ---connectedInstrumentTest
                ---connectedUiAutomatorTest (这个也还没实现……)

        deviceCheck
                依赖于任务创建时，其他插件实现测试的扩展点

最后, 为了能够安装卸载，Android plugin 为所有的build类型（debug,release,test）都创建了install/uninstall 任务，但需要signing。
