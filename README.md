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
  width:170px;
}
h2, h3{
  text-align:center;
}
input,select{
  width:100%;
  padding:12px;
  margin-top:10px;
  border-radius:6px;
  border:1px solid #ccc;
}
button{
  width:100%;
  padding:12px;
  margin-top:15px;
  border:none;
  background:#0066cc;
  color:white;
  border-radius:6px;
  cursor:pointer;
}
button:hover{
  background:#004a99;
}
.hidden{
  display:none;
}
.summary{
  background:#f3f6fb;
  padding:12px;
  margin-top:10px;
  border-radius:6px;
}
.details{
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
.flex-row {
  display: flex;
  gap: 10px;
  margin-top: 10px;
}
.box {
  flex: 1;
  display: flex;
  flex-direction: column;
}
.box input, .box select {
  width: 100%;
  padding: 10px;
  margin-top: 5px;
  border-radius: 6px;
  border: 1px solid #ccc;
}
</style>
</head>
<body>
 
<!-- LOGIN PAGE -->
<div class="container" id="loginPage">
<div class="logo">
<img src="https://tse1.mm.bing.net/th/id/OIP.sCJXUPY95pR-3_OfB0lGqwHaE3?rs=1&pid=ImgDetMain&o=7&rm=3">
</div>
<h2>Admin Login</h2>
<input id="loginUser" placeholder="Login ID">
<input id="loginPass" type="password" placeholder="Password">
<button onclick="adminLogin()">Login</button>
</div>
 
<!-- MAIN SYSTEM -->
<div class="container hidden" id="systemPage">
<div class="logo">
<img src="https://tse1.mm.bing.net/th/id/OIP.sCJXUPY95pR-3_OfB0lGqwHaE3?rs=1&pid=ImgDetMain&o=7&rm=3">
</div>
 
<h2>Dubai Retail Gift Card Registration</h2>
 
<select id="orderType" onchange="selectOrder()">
<option value="">Select Order Type</option>
<option value="retail">Retail Order</option>
<option value="online">Online Order</option>
</select>
 
<div id="contactBox" class="hidden flex-row">
<div class="box">
<input id="mobile" placeholder="Mobile Number">
</div>
<div class="box">
<input id="email" placeholder="Email Address">
</div>
</div>
<button id="sendOtpBtn" onclick="sendOTP()" class="hidden">Send OTP</button>
 
<div id="otpBox" class="hidden flex-row">
<div class="box">
<input id="mobileOTP" placeholder="Mobile OTP">
</div>
<div class="box">
<input id="emailOTP" placeholder="Email OTP">
</div>
</div>
<button id="verifyOtpBtn" onclick="verifyOTP()" class="hidden">Verify OTP</button>
 
<div id="retailCustomer" class="hidden flex-row">
<div class="box">
<input id="fname" placeholder="First Name">
</div>
<div class="box">
<input id="lname" placeholder="Last Name">
</div>
</div>
<button id="retailConfirmBtn" onclick="retailProceed()" class="hidden">Confirm Customer</button>
 
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
Service Charge: <span id="service">0</span><br>
VAT (5%): <span id="vat">0</span><br><br>
<b>Total: <span id="total">0</span></b>
</div>
<button onclick="showPayment()">Proceed Payment</button>
</div>
 
<div id="paymentSection" class="hidden">
<input id="posRef" placeholder="Enter POS Reference Number">
<button onclick="paymentSuccess()">Submit Payment</button>
</div>

<!-- Replace Payment Section -->
<div id="replacePayment" class="hidden">
<h3>Replacement Fee Payment</h3>

<!-- Step 1: New Card Proxy Number -->
<div class="summary">
<label>New Proxy/Digital Card Number:</label>
<input type="text" id="newProxy" placeholder="Enter New Proxy/Digital Card Number">
</div>

<!-- Step 2: Fee + VAT -->
<div class="summary">
<label>Replacement Fee (AED):</label>
<input type="number" id="replaceFee" placeholder="Enter Fee">
<p>VAT 5%: <span id="replaceVAT">0</span></p>
<p>Total: <span id="replaceTotal">0</span></p>
</div>

<!-- Step 3: POS Reference -->
<input id="replacePOS" placeholder="Enter POS Reference Number">
<button onclick="replaceConfirmPayment()">Submit Payment</button>
</div>
 
<div id="successMsg" class="hidden">
<p class="success">Payment Successful 🎉</p>
<p style="text-align:center;" id="successText">Gift Card Process Completed</p>
<button onclick="location.reload()">New Transaction</button>
</div>
 
<div id="historySection" class="hidden">
<h3>Gift Card Status & History</h3>
<div class="flex-row">
<div class="box">
<label>Select Proxy/Digital Card</label>
<select id="statusCardRef">
<option value="">Select Card</option>
</select>
</div>
<div class="box">
<label>Action</label>
<select id="cardStatus" onchange="showReplaceSection()">
<option value="Activate">Activate</option>
<option value="deactivate">Deactivate</option>
<option value="">Select Action</option>
<option value="balance">Show Balance</option>
<option value="block">Block</option>
<option value="unblock">Unblock</option>
<option value="disable">Disable</option>
<option value="replace">Replace</option>
</select>
</div>
</div>
<button onclick="showHistory()">Proceed</button>
 
<div id="historyDetails" class="details hidden">
<b>History / Status:</b>
<ul id="historyList"></ul>
<p id="cardActionResult" style="margin-top:10px; font-weight:bold;"></p>
</div>
 
<script>
let orderType="";
let cardHistoryDB = JSON.parse(localStorage.getItem("cardDB")) || {};
function saveDB(){ localStorage.setItem("cardDB", JSON.stringify(cardHistoryDB)); }

function adminLogin(){
let user=document.getElementById("loginUser").value
let pass=document.getElementById("loginPass").value
if(user==="Dubai Retail" && pass==="Dragon2026"){
document.getElementById("loginPage").style.display="none"
document.getElementById("systemPage").style.display="block"
}else{ alert("Invalid Login") }
}

function selectOrder(){
orderType=document.getElementById("orderType").value
document.getElementById("contactBox").style.display="flex"
document.getElementById("sendOtpBtn").style.display="block"
document.getElementById("email").style.display=(orderType==="retail")?"block":"none"
}

function sendOTP(){
if(orderType==="retail"){
alert("Demo OTP\nMobile:1234\nEmail:5678");
document.getElementById("emailOTP").style.display="block";
}else{
alert("Demo OTP\nMobile:1234");
document.getElementById("emailOTP").style.display="none";
}
document.getElementById("otpBox").style.display="flex";
document.getElementById("verifyOtpBtn").style.display="block";
}

function verifyOTP(){
let mobile=document.getElementById("mobileOTP").value
if(mobile!=="1234"){alert("Invalid OTP"); return}
document.getElementById("displayMobile").innerText=document.getElementById("mobile").value;
if(orderType==="retail"){
document.getElementById("retailCustomer").style.display="flex";
document.getElementById("retailConfirmBtn").style.display="block";
document.getElementById("displayEmail").innerText=document.getElementById("email").value;
document.getElementById("giftRef").style.display="none";
}else{
document.getElementById("retailCustomer").style.display="none";
document.getElementById("retailConfirmBtn").style.display="none";
document.getElementById("onlineCustomer").style.display="block";
document.getElementById("displayEmail").innerText="dragonmart@gmail.com";
document.getElementById("giftRef").style.display="block";
}
document.getElementById("otpBox").style.display="none";
}

function retailProceed(){
let fname=document.getElementById("fname").value
let lname=document.getElementById("lname").value
document.getElementById("displayName").innerText=fname+" "+lname
document.getElementById("customerDetails").style.display="block"
document.getElementById("retailCustomer").style.display="none"
document.getElementById("retailConfirmBtn").style.display="none"
document.getElementById("nextProcess").style.display="block"
}

function onlineProceed(){
document.getElementById("displayName").innerText="Dragon Mart"
document.getElementById("customerDetails").style.display="block"
document.getElementById("onlineCustomer").style.display="none"
document.getElementById("nextProcess").style.display="block"
}

/* Online activates card directly */
function proceedLoad(){
let proxy=document.getElementById("proxy").value.trim()
let giftRef=document.getElementById("giftRef").value.trim()
if(!proxy){ alert("Enter Proxy Number"); return; }

if(orderType==="online"){
if(!giftRef){ alert("Enter Gift Card Reference Number"); return; }

cardHistoryDB[proxy]={balance:0,history:[`Card Activated via Online Order on ${new Date().toLocaleDateString()}`],status:"active"}
saveDB()
let select=document.getElementById("statusCardRef")
if (![...select.options].some(o=>o.value===proxy)){
let option=document.createElement("option")
option.value=proxy
option.innerText=proxy
select.appendChild(option)
}
select.value=proxy

alert(`Digital → Physical Card Transfer Success! 🎉
Proxy Number: ${proxy}
Gift Card Ref: ${giftRef}`)

document.getElementById("nextProcess").style.display="none"
document.getElementById("successMsg").style.display="block"
document.getElementById("successText").innerText="Digital to Physical card ready\nGift Card Process Completed"
document.getElementById("historySection").style.display="block"

}else{
document.getElementById("nextProcess").style.display="none"
document.getElementById("loadSection").style.display="block"
}
}

function calculate(){
let amount=Number(document.getElementById("amount").value)
if(amount>=50 && amount<=3500){
let service=(orderType==="retail")?10:0
let vat=amount*0.05
let total=amount+service+vat
document.getElementById("load").innerText=amount
document.getElementById("service").innerText=service
document.getElementById("vat").innerText=vat.toFixed(2)
document.getElementById("total").innerText=total.toFixed(2)
}
}

function showPayment(){
document.getElementById("loadSection").style.display="none"
document.getElementById("paymentSection").style.display="block"
}

function paymentSuccess(){
let pos=document.getElementById("posRef").value
if(!pos){ alert("Enter POS Reference Number"); return; }
let proxy=document.getElementById("proxy").value.trim()
if(!proxy){ alert("Enter Proxy Number"); return; }
let amount=Number(document.getElementById("amount").value) || 0

cardHistoryDB[proxy]={balance:amount,history:[`Loaded AED ${amount} on ${new Date().toLocaleDateString()}`],status:"active"}
saveDB()
let select=document.getElementById("statusCardRef")
if(!([...select.options].some(o=>o.value===proxy))){
let option=document.createElement("option")
option.value=proxy
option.innerText=proxy
select.appendChild(option)
}
select.value=proxy

alert(`Payment Successful 🎉
Proxy Number: ${proxy}
Gift Card Ref: ${document.getElementById("giftRef").value || "N/A"}
Amount Loaded: AED ${amount}`)

document.getElementById("paymentSection").style.display="none"
document.getElementById("successMsg").style.display="block"
document.getElementById("successText").innerText="Gift Card Process Completed"
document.getElementById("historySection").style.display="block"
}

// Replace Section
function showReplaceSection(){
let action=document.getElementById("cardStatus").value
document.getElementById("replacePayment").style.display=(action==="replace")?"block":"none"
document.getElementById("historyDetails").style.display="none"
}

// Calculate VAT and Total dynamically
document.getElementById("replaceFee")?.addEventListener('input', function(){
let fee=Number(this.value)||0
let vat=fee*0.05
document.getElementById("replaceVAT").innerText=vat.toFixed(2)
document.getElementById("replaceTotal").innerText=(fee+vat).toFixed(2)
})

// Replace Confirm
function replaceConfirmPayment(){
let newRef=document.getElementById("newProxy").value.trim()
if(!newRef){ alert("Enter New Proxy/Digital Card Number"); return; }

let fee=Number(document.getElementById("replaceFee").value)
let pos=document.getElementById("replacePOS").value.trim()
if(!fee || fee<=0){ alert("Enter replacement fee"); return; }
if(!pos){ alert("Enter POS Reference Number"); return; }

let ref=document.getElementById("statusCardRef").value
if(!ref){ alert("Select a card to replace"); return; }

let oldCard=cardHistoryDB[ref]
let vat=fee*0.05
let total=fee+vat

cardHistoryDB[newRef]={balance:oldCard.balance,history:[...oldCard.history,`Replaced from ${ref} on ${new Date().toLocaleDateString()} | Fee Paid AED ${total.toFixed(2)}`],status:"active"}
delete cardHistoryDB[ref]
saveDB()

let select=document.getElementById("statusCardRef")
for(let i=0;i<select.options.length;i++){ if(select.options[i].value===ref){ select.remove(i); break; } }
let option=document.createElement("option")
option.value=newRef
option.innerText=newRef
select.appendChild(option)
select.value=newRef

alert(`Payment Successful 🎉
Old Proxy: ${ref}
New Proxy: ${newRef}
Gift Card Ref: ${document.getElementById("giftRef").value || "N/A"}
Fee Paid: AED ${total.toFixed(2)}`)

document.getElementById("replacePayment").style.display="none"
document.getElementById("historyDetails").style.display="block"
document.getElementById("cardActionResult").innerText=`Replaced card ${ref} → ${newRef} | Fee Paid AED ${total.toFixed(2)}`
}

function showHistory(){
let ref=document.getElementById("statusCardRef").value
if(!ref){ alert("Select a card"); return; }
let action=document.getElementById("cardStatus").value
let card=cardHistoryDB[ref]
let list=document.getElementById("historyList")
let result=document.getElementById("cardActionResult")
list.innerHTML=""
result.innerText=""
card.history.forEach(e=>{
let li=document.createElement("li")
li.innerText=e
list.appendChild(li)
})

switch(action){
case "Activate": card.status="active"; result.innerText=`Card ${ref} is ACTIVATED`; break;
case "deactivate": card.status="deactivated"; result.innerText=`Card ${ref} is DEACTIVATED`; break;
case "balance": result.innerText=`Current Balance: AED ${card.balance}`; break;
case "block": card.status="blocked"; result.innerText=`Card ${ref} is BLOCKED`; break;
case "unblock": card.status="active"; result.innerText=`Card ${ref} is UNBLOCKED`; break;
case "disable": card.status="disabled"; result.innerText=`Card ${ref} is DISABLED`; break;
default: result.innerText="No action selected"
}
document.getElementById("historyDetails").style.display="block"
}
</script>
