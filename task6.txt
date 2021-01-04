<?php
include "connection.php";

if(isset($_POST["login_submit"])){

    $email=$_POST["email"];
    $pass=$_POST["password"];

   
    $sql="SELECT * FROM `users` WHERE `email`='$email' AND `password`='$pass'";
    $q = $db->query($sql);
    $row=$q -> fetch_assoc();
    $_SESSION["id"]=$row["id"];

    if(isset($_POST["remember"])){
      $cookie_name = "uiid";
      $cookie_value = $row["id"];
     setcookie($cookie_name, $cookie_value, time() + (86400 * 30), "/");
    }
    header("location:homepage.php");
}

if(isset($_POST["reg_submit"])){

  $name=$_POST["name"];
  $email=$_POST["email"];
  $pass=$_POST["password"];

  INSERT INTO Customers (name, email, password)
  VALUES ('$name', '$email', '$pass');

  $sql=INSERT INTO Customers (name, email, password)
  VALUES ('$name', '$email', '$pass');
  $q = $db->query($sql);
  if($q){

    echo "Reg Success...";
  }



}
if(isset($_POST["reg_click"]){

  header("location:reg.php");
}

if(isset($_POST["change_pass"])){

    $cr_pass=$_POST["cr_password"];
    $nw_pass=$_POST["nw_password"];
    $id=$_SESSION['id'];
  
    $sql="UPDATE users SET password=$nw_pass where id=$id";
    $q = $db->query($sql);
    if($q)
          {
          echo "Congratulations You have successfully changed your password";
          }
  
  }


  if(isset($_POST["createProduct"])){

    // I'm using here a different Database..
    $dbinsert=new mysqli("localhost","root","","product_db") or die("Database Connection Fail...");
    

    $name = $_POST['name'];
	$price= $_POST['bprice'];
	$sprice = $_POST['sprice'];
    $display = $_POST['display'];

       $selectQuery = "INSERT into products (name, buying_price,selling_price, visiablity)
       VALUES (:$name, :$price, :$sprice, :$display)";

      $q = $db->query($selectQuery);
      if($q)
      {
      echo "Data Added";
      }
  }

  if(isset($_GET["logout"])){

    session_destroy();
    header("location:index.php");
  }
?>

