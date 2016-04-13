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

在sdk 22以上的版本如果出现错误，在build.gradle的android中添加

android{
useLibrary 'org.apache.http.legacy'
}


使用方法：
    1.首先生成参数对象 VolleyRequestSupport
    #
        VolleyRequestSupport requestSupport = new VolleyRequestSupport();
    2.参数对象添加所需的元素内容
        requestSupport.setUrl("访问地址");
        //post请求时传递的访问参数集合
        Map<String,String> params = new HashMap<String,String>();
        requestSupport.setParams(params);
        //可选项，添加访问队列的标示TAG
        requestSupport.setRequestQueueTag("tag标示");
        //这里添加访问方式（get或post），参数对象默认get请求方式
        requestSupport.setMethod(Request.Method.POST);
        //参数对象赋值回调接口
        requestSupport.setVolleyInterface(new VolleyInterface() {
            @Override
            public void onError(VolleyError error) {
                //错误处理
            }

            @Override
            public void onSuccess(VolleyResultSupport volleySupport) {
                //请求成功，根据自己的请求方式，从数据对象中获取自己所需的内容

            }
        });
    3.请求队列添加到volley的请求队列中
        VolleyParser.jsonObjectRequest(mVolleySingleton, requestSupport);


3、添加library支持core.jar

将jar包安装到maven目录下

mvn install:install-file -DgroupId=com.ione -DartifactId=demo -Dversion=1.0 -Dfile=生成的jar包路径 -Dpackaging=jar -DgeneratePom=true -DlocalRepositoryPath=要安装的maven路径 -DcreateChecksum=true
