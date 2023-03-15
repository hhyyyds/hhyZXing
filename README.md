hhyZXing
介绍
ZXing可以扫描本地相册的使用 最开始的使用yuzhiqiang1993的时候可能会导致扫描相册内容的时候失败所以我修改了CaptureActivity中的代码 使得可以扫描相册内容了，想要修改扫描的格式的话可以去看yuzhiqiang1993的修改，以下只是实现了扫描相册代码。

首先添加自己的依赖 app文件夹下的build.gradle文件里加上这一条依赖 dependencies { ... implementation 'com.gitee.xuan_xx:hhy-zxing:1.0' } 外面的大文件夹也就是整个项目的build.gradle文件里加上maven这一行 repositories { google() jcenter() maven { url "https://jitpack.io" } }

在自己的MainActivity当中开启CaptureActivity Intent intent = new Intent(MainActivity.this, SonCaptureActivity.class); startActivityForResult(intent, REQUEST_CODE_SCAN); 注意这里的REQUEST_CODE_SCAN是自己定义的一个int类型;

然后继续在MainActivity当中重写一下代码666的resultCode对应的是扫描相册的结果 RESULT_OK对应的是正常扫描的结果

protected void onActivityResult(int requestCode, int resultCode, Intent data) { super.onActivityResult(requestCode, resultCode, data); if (requestCode == REQUEST_CODE_SCAN && resultCode == 666) { if (data != null) { //String content = data.getStringExtra(Constant.CODED_CONTENT); String content = data.getStringExtra("qrcode"); tv.setText(content); } } else if(requestCode == REQUEST_CODE_SCAN && resultCode == RESULT_OK){ if (data != null) { String content = data.getStringExtra(Constant.CODED_CONTENT); tv.setText(content); } }else {} }
