<!DOCTYPE html>
<html>
<head>
<title>Dragon Mart Gift Card System</title>

<style>
body{
font-family:Segoe UI;
background:#eef2f7;
padding:40px;
}
.container{
width:500px;
margin:auto;
background:white;
padding:30px;
border-radius:12px;
box-shadow:0 5px 20px rgba(0,0,0,0.1);
}
.logo{
text-align:center;
margin-bottom:15px;
}
.logo img{
width:160px;
}
h2{
text-align:center;
margin-bottom:20px;
}
input,select{
width:100%;
padding:12px;
margin-top:10px;
border-radius:6px;
border:1px solid #ccc;
font-size:14px;
}
button{
width:100%;
padding:12px;
margin-top:15px;
border:none;
background:#0066cc;
color:white;
font-size:15px;
border-radius:6px;
cursor:pointer;
}
button:hover{
background:#004a99;
}
.hidden{
display:none;
}
.details{
background:#f3f6fb;
padding:12px;
margin-top:10px;
border-radius:6px;
}
.summary{
background:#f3f6fb;
padding:12px;
margin-top:10px;
border-radius:6px;
}
.success{
text-align:center;
color:green;
font-size:20px;
}
</style>
</head>

<body>

<div class="container">

<!-- Logo -->
<div class="logo">
<img src="https://tse1.mm.bing.net/th/id/OIP.sCJXUPY95pR-3_OfB0lGqwHaE3?rs=1&pid=ImgDetMain&o=7&rm=3" alt="Logo">
</div>

<h2> Dubai Retail Gift Card Registration</h2>

<select id="orderType" onchange="selectOrder()">
<option value="">Select Order Type</option>
<option value="retail">Retail Order</option>
<option value="online">Online Order</option>
</select>

<div id="contactBox" class="hidden">
<input id="mobile" placeholder="Mobile Number">
<input id="email" placeholder="Email Address">
<button onclick="sendOTP()">Send OTP</button>
</div>

<div id="otpBox" class="hidden">
<input id="mobileOTP" placeholder="Mobile OTP">
<input id="emailOTP" placeholder="Email OTP">
<button onclick="verifyOTP()">Verify OTP</button>
</div>

<div id="retailCustomer" class="hidden">
<input id="fname" placeholder="First Name">
<input id="lname" placeholder="Last Name">
<button onclick="retailProceed()">Confirm Customer</button>
</div>

<div id="onlineCustomer" class="hidden">
<div class="details">
Name: <b>Dragon Mart</b>
</div>
<button onclick="onlineProceed()">Confirm Customer</button>
</div>

<div id="customerDetails" class="details hidden">
<b>Customer Details</b><br><br>
Name: <span id="displayName"></span><br>
Mobile: <span id="displayMobile"></span><br>
Email: <span id="displayEmail"></span>
</div>

<div id="nextProcess" class="hidden">
<input id="giftRef" placeholder="Gift Card Reference Number">
<input id="proxy" placeholder="Proxy Number">
<button onclick="proceedLoad()">Continue</button>
</div>

<div id="loadSection" class="hidden">
<input type="number" id="amount" placeholder="Load Amount (50 - 3500)" oninput="calculate()">
<div class="summary">
Load Amount: <span id="load">0</span><br>
Card Fee: 10<br>
VAT (5%): <span id="vat">0</span><br><br>
<b>Total: <span id="total">0</span></b>
</div>
<button onclick="showPayment()">Proceed Payment</button>
</div>

<div id="paymentSection" class="hidden">
<select>
<option>Select Card Type</option>
<option>Debit Card</option>
<option>Credit Card</option>
</select>
<input placeholder="Card Number">
<button onclick="paymentSuccess()">Pay Now</button>
</div>

<div id="successMsg" class="hidden">
<p class="success">Payment Successful 🎉</p>
<p style="text-align:center;">Gift Card Loaded Successfully</p>
<button onclick="location.reload()">New Transaction</button>
</div>

</div>

<script>
let orderType=""
let mobileOTPdemo="1234"
let emailOTPdemo="5678"

// Order Type Selection
function selectOrder(){
    orderType = document.getElementById("orderType").value;
    document.getElementById("contactBox").style.display = "block";

    // Show email input only for retail
    if(orderType === "retail"){
        document.getElementById("email").style.display = "block";
    } else {
        document.getElementById("email").style.display = "none";
    }
}

// Send OTP
function sendOTP(){
    let mobile = document.getElementById("mobile").value;
    let email = document.getElementById("email").value;

    if(!mobile){ alert("Enter mobile number"); return; }
    if(orderType === "retail" && !email){ alert("Enter email"); return; }

    // OTP popup: show based on order type
    if(orderType === "retail"){
        alert("Demo OTP\nMobile:1234\nEmail:5678");
    } else { // online
        alert("Demo OTP\nMobile:1234");
    }

    document.getElementById("otpBox").style.display = "block";

    // Show email OTP input only for retail
    document.getElementById("emailOTP").style.display = (orderType === "retail") ? "block" : "none";
}

// Verify OTP
function verifyOTP(){
    let mobile = document.getElementById("mobileOTP").value;
    let email = document.getElementById("emailOTP").value;

    if(orderType === "retail"){
        if(mobile !== mobileOTPdemo || email !== emailOTPdemo){
            alert("Invalid OTP"); 
            return;
        }
        document.getElementById("retailCustomer").style.display = "block";
    } else { // online
        if(mobile !== mobileOTPdemo){
            alert("Invalid OTP");
            return;
        }
        document.getElementById("onlineCustomer").style.display = "block";
    }

    document.getElementById("displayMobile").innerText = document.getElementById("mobile").value;
    document.getElementById("displayEmail").innerText = document.getElementById("email").value || "-";
    document.getElementById("otpBox").style.display = "none";
}

// Retail Name Proceed
function retailProceed(){
    let fname=document.getElementById("fname").value;
    let lname=document.getElementById("lname").value;
    if(!fname||!lname){alert("Enter name");return;}
    document.getElementById("displayName").innerText=fname+" "+lname;
    document.getElementById("customerDetails").style.display="block";
    document.getElementById("retailCustomer").style.display="none";
    document.getElementById("nextProcess").style.display="block";
    document.getElementById("giftRef").style.display="none";
}

// Online Proceed
function onlineProceed(){
    document.getElementById("displayName").innerText="Dragon Mart";
    document.getElementById("customerDetails").style.display="block";
    document.getElementById("onlineCustomer").style.display="none";
    document.getElementById("nextProcess").style.display="block";
    document.getElementById("giftRef").style.display="block";
}

// Proceed to Load Amount
function proceedLoad(){
    let proxy=document.getElementById("proxy").value;
    if(!proxy){alert("Enter Proxy Number");return;}
    document.getElementById("nextProcess").style.display="none";
    document.getElementById("loadSection").style.display="block";
}

// Load Amount Calculation
function calculate(){
    let amount=Number(document.getElementById("amount").value);
    if(amount>=50 && amount<=3500){
        let fee=10;
        let vat=amount*0.05;
        let total=amount+fee+vat;
        document.getElementById("load").innerText=amount;
        document.getElementById("vat").innerText=vat.toFixed(2);
        document.getElementById("total").innerText=total.toFixed(2);
    } else {
        document.getElementById("load").innerText="0";
        document.getElementById("vat").innerText="0";
        document.getElementById("total").innerText="0";
    }
}

// Show Payment
function showPayment(){
    document.getElementById("loadSection").style.display="none";
    document.getElementById("paymentSection").style.display="block";
}

// Payment Success with Random Reference Popup
function paymentSuccess(){
    let refNumber = "GM-" + Math.floor(10000000 + Math.random() * 90000000);
    alert("Payment Successful 🎉\nYour Reference Number: " + refNumber);
    document.getElementById("paymentSection").style.display="none";
    document.getElementById("successMsg").style.display="block";
}
</script>

</body>
</html>
