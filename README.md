# hhyZXing
扫描本地相册ok
   protected void onActivityResult(int requestCode, int resultCode, Intent data) {
       super.onActivityResult(requestCode, resultCode, data);
       if (requestCode == REQUEST_CODE_SCAN && resultCode == 666) {
           if (data != null) {
               //String content = data.getStringExtra(Constant.CODED_CONTENT);
               String content = data.getStringExtra("qrcode");
               tv.setText(content);
           }

       }   else if(requestCode == REQUEST_CODE_SCAN && resultCode == RESULT_OK){
           if (data != null) {

               String content = data.getStringExtra(Constant.CODED_CONTENT);
               tv.setText(content);
           }
       }else {}
       // 扫描二维码/条码回传
     /*  if (requestCode == REQUEST_CODE_SCAN && resultCode == RESULT_OK) {
           if (data != null) {

               String content = data.getStringExtra(Constant.CODED_CONTENT);
               tv.setText("扫描结果为：" + content);
           }
       }*/
   }
