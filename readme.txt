补充说明

1、Java和Python一样，可以选择自己编译proto文件，也可以使用第三方库，我是用的是这个http://mvnrepository.com/artifact/com.yesup.oss/tensorflow-client/1.4-2 
在pom.xml下加入依赖：

        <dependency>
            <groupId>com.yesup.oss</groupId>
            <artifactId>tensorflow-client</artifactId>
            <version>1.4-2</version>
        </dependency>
        
2、解压mnist(.gz)文件会导致文件名不匹配，需要纠正，mnist_data_test文件夹应与src文件夹平行。
