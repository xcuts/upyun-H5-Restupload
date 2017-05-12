### upyun-H5-Restupload
1. 基于rest API的PUT方法对又拍云进行异步上传请求
2. rest.html中注释的4处改为需要的信息即可使用

<pre><code>
  $(document).ready(function () {
	  $("#fileupload").change(function () {
		  bucket_name="bucket_name";              //服务名称
		  opename="opename";                      //操作员账号
		  opepass="opename";                      //操作员密码
		  save_as="/rest.jpg";                    //保存路径
		  acc_point="http://v0.api.upyun.com/";
		  date=(new Date()).toUTCString();
		  file=$(this).get(0).files[0];
		  sign=SparkMD5.hash("PUT&/"+bucket_name+save_as+"&"+date+"&"+file.size+"&"+SparkMD5.hash(opepass));
		  infoHtml = "文件名称:" + file.name + "<br/>";
		  infoHtml+= "文件大小:" + file.size + "<br/>";
		  infoHtml+= "文件类型:" + file.type + "<br/>";
		  $("#info").html(infoHtml);
	  });
  </code></pre>
* 注意:最好从后端签名传递到前端，如果前端一定要使用这种方法，可以后台创建一个仅有写入权限的操作员来使用。
