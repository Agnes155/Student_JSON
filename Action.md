<?php
    class Student
    {
        /* Member Variables*/
         var $sname;
         var $sadmission;
         var $DOB;
         var $address;
         var $progra;
         var $gender;
         var $fname;
         var $foccu;
         var $mname;
         var $moccu;
         var $number;
         var $email;
        /*Member Functions*/
        //constructor
        public function __construct()
        {
            $this->sname       =    $_POST['name'];
            $this->sadmission  =    $_POST['admission'];
            $this->DOB         =    $_POST['DOB'];
            $this->address     =    $_POST['address'];
            $this->progra     =    $_POST['program'];
            $this->gender      =    $_POST['gender'];
            $this->fname       =    $_POST['fname'];
            $this->foccu       =    $_POST['foccu'];
            $this->mname       =    $_POST['mname'];
            $this->moccu       =    $_POST['moccu'];
            $this->number      =    $_POST['number'];
            $this->email       =    $_POST['email'];  
        }
    }
    $S = new Student;
    $T= new Student;
       $jsnobj=json_encode($S);
       echo $jsnobj;
       echo "<br>";
       echo "<br>";
	var_dump(json_decode($jsnobj));
    $T=json_decode($jsnobj);
	$nam=$T->sname;
	$adm=$T->sadmission;
	$date=$T->DOB;
	$addr=$T->address;
	$prog=$T->progra;
	$gend=$T->gender;
	$fn=$T->fname;
	$fo=$T->foccu;
	$mn=$T->mname;
	$mo=$T->moccu;
	$num=$T->number;
	$em=$T->email;
	$link=mysqli_connect("localhost","root","","student");
    if($link==false)
    {
        die("ERROR: Could not connect. " . mysqli_connect_error());
    }
    $sql="INSERT INTO studententry(SName,AdmissionNo,DOB,SAddress,Program,Gender,FathersName,OccupationF,MothersName,OccupationM,Contact,Email) 
    VALUES ('$nam','$adm','$date','$addr','$prog','$gend','$fn','$fo','$mn','$mo','$num','$em')";
    echo "<br>";
    $result=mysqli_query($link,$sql);
    if($result)
    {
        echo "Records inserted successfully.";
    }
    else
    {
        echo "ERROR: Could not able to execute $sql. " . mysqli_error($link);
    }
    echo "<br>";
?>
      