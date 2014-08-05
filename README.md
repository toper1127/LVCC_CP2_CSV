LVCC_CP2_CSV
============
<!doctype html>
<html>
	<head>
		<title>LVCC Computer Programming 2nd Year</title>
		<link rel="stylesheet" href="color.css" />
	</head>

		<body>
			<div id="wrap">
				<h1>LVCC Computer Programming 2nd Year</h1>
				<h6>Code &amp; Design by: Christopher Coronel &trade;</h6>

			<?php

					$names = file ("CP2.csv");

				#firstname, last name, age, email, contact number

					echo '<table border="0" width="100%">';
					echo '<tr>';
					echo '<th width="20%">Last Name</th>';
					echo '<th width="20%">First Name</th>';
					echo '<th width="10%">Age</th>';
					echo '<th width="30%">Email</th>';
					echo '<th width="20%">Contact No.</th>';
				foreach($names as $name) {
					
					list ($firstname, $lastname, $age, $email, $contact) = explode (",", $name);

					
					echo '<tr>';
					echo '<td>';
					echo $firstname;
					echo '</td>';
					echo '<td>';
					echo $lastname;
					echo '</td>';
					echo '<td>';
					echo $age;
					echo '</td>';
					echo '<td>';
					echo $email;
					echo '</td>';
					echo '<td>';
					echo $contact;
					echo '</td>';
					echo '</tr>';
				}
				echo '</table>';

			?>
			<form action = "Register.php">
				<input type = "submit" value = "Register">
			</form>
			</body>
</html>
=============================================================================================================
/*Register.php */
<!DOCTYPE html>
<html>
	<head>
		<title>Sample Form</title>
	</head>
		<body>
			<div class = "wrap">
				<form action = "submit.php" method = "POST">
					Last Name: <input type = "text" size = "15" name = "firstname">
					<br>First Name: <input type = "text" size = "15" name = "lastname">
					<br>Age:
						<select name = "age">
							<?php for ($i = 99; $i > 0; $i--): ?>
							<option value = "<?php echo $i; ?>" >
								<?php echo $i; ?>
							</option>
							<?php endfor; ?>
						</select>
					<br>Email Address: <input type = "text" size = "15" name = "email">
					<br>Contact No.: <input type = "text" size = "15" name = "contact">
					<br><input type = "submit" value = "Submit" >
				</form>
			</div>
		</body>
</html>
==========================================================================================================
/*submit.php */
<?php
	$lastname = $_POST['lastname'];
	$firstname = $_POST['firstname'];
	$age = $_POST['age'];
	$email = $_POST['email'];
	$contact = $_POST['contact'];

	if (isset($_POST) && !empty($_POST)) {

	$info = array ($firstname,$lastname,$age,$email,$contact);

	$fp = fopen('CP2.csv', 'a');
	fputcsv($fp, $info);
	fclose($fp);
	}

	header ("Location:http://localhost/christophercoronel/toper/LVCC_CP2_CSV.php");
?>
=============================================================================================================
