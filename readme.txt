1、JDBC中的预处理语句：
	Class.forName("com.mysql.jdbc.Driver");
	String url="jdbc:mysql://localhost:3308/hzyc92";
	Connection conn=DriverManager.getConnection(url,"root","mysql");
	String sql="insert into student values (?,?,?)";
	PreparedStatement pstmt = conn.PreparedStatement(sql);
	------------预处理语句，特殊的载体
	pstmt.setString(2,"清明上河图");
	pstmt.setInt(1,101);
	---------文件处理
	File source=new File("D:/temp20200108/a.png");
	FileInput input=new FileInput(source);
	pstmt.setBinaryStream(3,input,input.available());
	
	pstmt.execute();
	
	cnn.close();
	pstmt.close();
	input.close();
2、从数据库中读取：
	
	Class.forName("com.mysql.jdbc.Driver");
	String url="jdbc:mysql://localhost:3308/hzyc92";
	Connection conn=DriverManager.getConnection(url,"root","mysql");
	Statement stmt=conn.CreatStatement();
	String sql="select * from student";
	ResultSet rs=stmt.executeQuery(sql);
	rs.next();
	FileOutputStream output = new FileOutputStream("D:/temp20200108/"+new java.uitl.Date().getTime()+".png");
	int code = rs.get("code");
	String name = rs.get("name");
	InputStream input = rs.getBinaryStream("myImg");
	System.out.print(code+","+name);
	
	byte[] buffer = new byte[1024];
	int cnt=0;
	while((cnt=input.read(buffer))>0){
		output.write(buffer,0,cnt);
	}
	
	conn.close();
	stmt.close();
	output.close();
	input.close();
	rs.close();
	
3、文件操作：
	input/output
	输入/输出（目标方向：当前正在操作的缓存）
		进入缓存：input
		离开缓存：output
	字节型(1 byte)：
		byte[] buffer = new byte[1024];
		InputStream: 输入流(字符型);
		OutputStream：输出流(字符型);
	
	字符型(1 char)：
		char[] buffer = new char[10];
		Reader: 输入流;（字符型）;
		Writer：输出流;（字符型）;
4、上传：
	upload    ---上传：
	本地（local）----服务器(server)
	需要相应的jar包：apache---commons---upload的jar包
	上传的表单：
	<form action="doUpload" method="post" enctype="multipart/form-data">
		<input type="file" name="myFile123" id="first" value="---上传的文件---">
	</form>
	使用enctype="multipart/form-data"上传的数据是以字节型传送的
		【1】磁盘项文件“项（item）”工厂Factory
		【2】服务应用文件上传（工具）
		【3】request去获取数据流
	DiskFileItemFactory 文件项工厂=new DiskFileItemFactory();
	SeverletFileUpload 上传工具 = new SeverletFileUpload(文件向工厂);
	FileItemIterator iter = 上传工具.getItemIterator(request);
	while(iter.hasNext()){
		FileItemStream 闭合的流 = iter.next();
		String 上传的文件名 = 闭合的流.getName();
		if(上传的文件名 = null){
			//此时上传的数据原来不是文件，但是也会被看成文件
			InputStream input=闭合的流.open();
			InputStreamReader 转化后的 = new InputStreamReader(input,"utf-8");
			BufferReader reader = new BufferReader(转化后的);
			String info = reader.readline();
			System.out.print(info);
		}else{
			InputStream input = 闭合的流.open();
			String tomcatPath = request.getSession().getSeverletContext().getRealPath();
			FileInputStream input= new FileInputStream(tomcatPath+"/files/"+new java.uitl.Date().getTime()+上传的文件名);
		}
	}