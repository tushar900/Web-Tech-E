<?php

if(isset($_COOKIE["uiid"])){
  $_SESSION["id"]=$_COOKIE["uid"];
  header("location:homepage.php");
}

?>

<!DOCTYPE html>
<html lang="en">
<head>
  <title>User Detil</title>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.16.0/umd/popper.min.js"></script>
  <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
</head>
<body>

<div class="container">
  <h2>Login Form</h2>
  <form action="action.php"  method="post">
    <div class="form-group">
      <label for="email">Email:</label>
      <input type="email" class="form-control" id="email" placeholder="Enter email" name="email">
    </div>
    <div class="form-group">
      <label for="password">Password:</label>
      <input type="password" class="form-control" id="password" placeholder="Enter password" name="password">
    </div>

    <div class="form-check">
    <label class="form-check-label">
      <input class="form-check-input" type="checkbox" name="remember"> Remember me
    </label>
  </div>
    <button type="submit" class="btn btn-primary" name="login_submit">Submit</button>
    
    <button type="REG" class="btn btn-primary" name="reg_click">REG</button>
  </form>

  </form>
</div>


</body>
</html>