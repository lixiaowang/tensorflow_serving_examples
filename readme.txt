补充说明

1、Java和Python一样，可以选择自己编译proto文件，也可以使用第三方库，我是用的是这个http://mvnrepository.com/artifact/com.yesup.oss/tensorflow-client/1.4-2，在pom.xml下加入依赖：

        <dependency>
            <groupId>com.yesup.oss</groupId>
            <artifactId>tensorflow-client</artifactId>
            <version>1.4-2</version>
        </dependency>

参考链接：http://blog.csdn.net/shin627077/article/details/78592729

2、解压mnist(.gz)文件会导致文件名不匹配，需要纠正，mnist_data_test文件夹应与src文件夹平行：
MNISTJavaClientTest中部分代码调整：

        client.predict("mnist_data_test/t10k-images.idx3-ubyte",
                "mnist_data_test/t10k-labels.idx1-ubyte");

3、输入的MNIST测试集需要做归一化：
MNISTJavaClient.java中private TensorProto createImageTensor(int[][] image)，部分代码调整：

            for (int i = 0; i < image.length; ++i) {
                for (int j = 0; j < image.length; ++j) {
//                    归一化：[0~255] -> [0.0~1.0]
                    float normImage = (float)(image[i][j] / 255.0);
                    imageTensorBuilder.addFloatVal(normImage);
                }
            }
