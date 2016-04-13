# volley-parser
重新封装volley,增加volley管理器，增加访问数据的方法
项目中直接引用jar包使用

1、在主 build.gradle中添加

allprojects {

repositories {
#
    jcenter()
    #
    maven{url 'https://raw.githubusercontent.com/ryan-sun/volley-parser/master/Repository'}
    #
}
#
}

2、在项目build.gradle中添加

dependencies {

compile 'com.ivolley:parser:1.0'

}

3、添加library支持core.jar

将jar包安装到maven目录下

mvn install:install-file -DgroupId=com.ione -DartifactId=demo -Dversion=1.0 -Dfile=生成的jar包路径 -Dpackaging=jar -DgeneratePom=true -DlocalRepositoryPath=要安装的maven路径 -DcreateChecksum=true
