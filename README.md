<html>
    <head>
<link rel="stylesheet" href="calcy.css">
<meta name="viewport" content="widht=device-width ,initial scale=1">
        <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
        <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css">
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
        <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/js/bootstrap.min.js"></script>
    </head>
    <style>
        body{
    background-color: cadetblue;
}
    </style>
    <body>
        <div class="main">
            <center>
               <div class="row">
                       <div class="col-md-3">
                           <div class="vl">
                          <p id="cal">Student Grad Calcy</p>
                          </div>
                       </div>

                       <div class="col-md-9">
                        <form method="POST">
                            <div class="app-form-group">
                            <input type="number" pattern="[0-10]{3}"  class="form-group" name="sub1" id="one" placeholder="subject1" required oninput="enableButton()">
                             </div>
                        <div class="app-form-group">
                         <input type="number" pattern="[0-10]{3}" class="form-group" name="sub2"  id="two" placeholder="subject2" required oninput="enableButton()">
                               </div>
                            <div class="app-form-group">
<input type="number" pattern="[0-9]{3}" class="form-group" name="sub3" id="three" placeholder="subject3" required oninput="enableButton()">
                                   </div>
                           <div class="app-form-group">
<input type="number" class="form-group" name="sub4" id="four" pattern="[0-10]{3}" placeholder="subject4" required oninput="enableButton()">
                                       </div>
                            <div class="app-form-group">
<input type="number" class="form-group" name="sub5" id="five" pattern="[0-10]{3}" placeholder="subject5" required oninput="enableButton()">
                                 </div>
      <input type="button" name="submit" id="btnSubmit" value="SHOWPERCENTAGE" style="background-color: rgb(37, 37, 37);
            color: cadetblue;border: none;" onclick="calc()" disabled>
                         </form>
                       </div>
        <div class="app from-group showdata">
            <p id="showdata"></p>
        </div>
               </div>

</center>
        </div>
          <script>
function enableButton(){
    let inputs = document.querySelectorAll('[type="number"]');
    button = document.querySelector('#btnSubmit');
    button.disabled = true

for (i = 0; i < inputs.length; i++) {
  inputs[i].addEventListener('input',() => {
    let values = []
    inputs.forEach(v => values.push(v.value))
    button.disabled = values.includes('')
  })
}
}

 const calc = () =>{
     let sub1=document.getElementById('one').value;
     let sub2=document.getElementById('two').value;
     let sub3=document.getElementById('three').value;
     let sub4=document.getElementById('four').value;
     let sub5=document.getElementById('five').value;
     let grades="";
     let totalGrades = parseFloat(sub1) + parseFloat(sub2) + parseFloat(sub3) + parseFloat(sub4) + parseFloat(sub5);

  let perc = (totalGrades/500)*100;

  if(perc <= 100 && perc >= 90)
  {
    grades = "A+";
  }
  else if(perc <= 89 && perc >= 70 ){
    grades = "A";
      }else if(perc <= 69 && perc >= 50 ){
        grades = "B";
      }else if(perc <= 49 && perc >= 30 ){
        grades = "C";
      }else{
        grades = "F";
      }
      if(perc >=30){
    document.getElementById('showdata').innerHTML = `Out of 500 you Total is ${totalGrades}
     and percentage is ${perc}%. <br> Your Grade is ${grades}.You are Pass.`;
      }else{
        document.getElementById("showdata").innerHTML = `Out of 500 you Total is ${totalGrades}
     and percentage is ${perc}%. <br> Your Grade is ${grades}.You are Fail.`;

      }
 
    }
          </script>
    </body>
</html>
