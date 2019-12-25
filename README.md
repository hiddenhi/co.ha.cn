# co.ha.cn
## PHP连接Access查询Hash
<?php 
$hash=$_GET['hash'];
$dsn = "DRIVER={Microsoft Access Driver (*.mdb)}; DBQ=". realpath("db.mdb");
$conn = odbc_connect($dsn,"","") or die("error");
$sqlquery = "select * from name where hash='".$hash."'";
$exec = odbc_exec($conn,$sqlquery);
$row = odbc_fetch_array($exec);
echo $row['value'];
odbc_close($conn);
?> 

## PHP连接Access写入Hash
<?php 
$dsn = "DRIVER={Microsoft Access Driver (*.mdb)}; DBQ=". realpath("db.mdb");
$conn = odbc_connect($dsn,"","") or die("error");
$sqlquery = "select * from name where hash='".$hash."'";
$tit=md5(date('Y-m-d h:i:s', time()));
$sql="insert into name values ('{$tit}','{$tit}')";
$exec = odbc_exec($conn,$sql);
echo $tit;
odbc_close($conn);
exit();
?> 
