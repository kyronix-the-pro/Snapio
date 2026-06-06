<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SNAPIO</title>
    <style>
        *{
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, Helvetica, sans-serif;
        }

        body{
            background: #f5f7fb;
            height: 100vh;
        }

        .hidden{
            display: none !important;
        }

        /* LANDING PAGE */
        #landingPage{
            width: 100%;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: linear-gradient(135deg, #2563eb, #1e3a8a);
        }

        .landing-card{
            background: white;
            padding: 50px;
            width: 450px;
            border-radius: 20px;
            text-align: center;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }

        .logo{
            font-size: 60px;
            font-weight: bold;
            color: #2563eb;
            margin-bottom: 10px;
        }

        .subtitle{
            color: #666;
            margin-bottom: 30px;
        }

        .main-btn{
            width: 100%;
            padding: 15px;
            margin-top: 10px;
            border: none;
            border-radius: 12px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            transition: .2s;
        }

        .create-btn{
            background: #2563eb;
            color: white;
        }

        .login-btn{
            background: #111827;
            color: white;
        }

        .main-btn:hover{
            transform: translateY(-2px);
        }

        /* AUTH */
        .auth-box{
            background: white;
            width: 450px;
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,.15);
        }

        .auth-page{
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .auth-title{
            text-align: center;
            margin-bottom: 25px;
        }

        .input{
            width: 100%;
            padding: 14px;
            margin-top: 10px;
            border: 1px solid #ddd;
            border-radius: 10px;
            font-size: 15px;
        }

        .message{
            margin-top: 15px;
            text-align: center;
            font-weight: bold;
        }

        /* DASHBOARD */
        #dashboard{
            display: flex;
            height: 100vh;
        }

        .sidebar{
            width: 260px;
            background: #111827;
            color: white;
            padding: 20px;
        }

        .sidebar-logo{
            font-size: 32px;
            font-weight: bold;
            margin-bottom: 30px;
        }

        .sidebar-item{
            padding: 15px;
            margin-top: 8px;
            border-radius: 10px;
            cursor: pointer;
            transition: .2s;
        }

        .sidebar-item:hover{
            background: #1f2937;
        }

        .content{
            flex: 1;
            background: white;
            padding: 30px;
        }

        .page-title{
            font-size: 32px;
            margin-bottom: 15px;
        }

        .friend-card{
            background: #f8fafc;
            border-radius: 15px;
            padding: 20px;
            margin-top: 20px;
        }

        .search-user{
            display: flex;
            gap: 10px;
            margin-top: 15px;
        }

        .search-user button{
            padding: 14px 20px;
            border: none;
            border-radius: 10px;
            background: #2563eb;
            color: white;
            cursor: pointer;
        }

        .search-user button:hover {
            background: #1d4ed8;
        }

        .request-box{
            margin-top: 30px;
        }

        .request-item{
            background: white;
            border: 1px solid #ddd;
            padding: 15px;
            border-radius: 10px;
            margin-top: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .request-item button {
            padding: 8px 15px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            margin-left: 5px;
            font-weight: bold;
        }

        .request-item .action-btn {
            background: #2563eb;
            color: white;
        }

        .request-item .decline-btn {
            background: #ef4444;
            color: white;
        }
    </style>
</head>
<body>

<div id="landingPage">
    <div class="landing-card">
        <div class="logo">SNAPIO</div>
        <div class="subtitle">Connect with friends.</div>
        <button class="main-btn create-btn" onclick="showRegister()">Create Account</button>
        <button class="main-btn login-btn" onclick="showLogin()">Sign In</button>
    </div>
</div>

<div id="registerPage" class="auth-page hidden">
    <div class="auth-box">
        <h1 class="auth-title">Create Account</h1>
        <input id="registerUsername" class="input" placeholder="Username">
        <input id="registerPassword" class="input" type="password" placeholder="Password">
        <button class="main-btn create-btn" onclick="register()">Create Account</button>
        <div id="registerMessage" class="message"></div>
    </div>
</div>

<div id="loginPage" class="auth-page hidden">
    <div class="auth-box">
        <h1 class="auth-title">Sign In</h1>
        <input id="loginUsername" class="input" placeholder="Username">
        <input id="loginPassword" class="input" type="password" placeholder="Password">
        <button class="main-btn login-btn" onclick="login()">Sign In</button>
        <div id="loginMessage" class="message"></div>
    </div>
</div>

<div id="dashboard" class="hidden">
    <div class="sidebar">
        <div class="sidebar-logo">SNAPIO</div>
        <div class="sidebar-item" onclick="showFriendsPage()">Friends</div>
        <div class="sidebar-item">Profile</div>
        <div class="sidebar-item">Chats</div>
        <div class="sidebar-item">For You</div>
        <div class="sidebar-item">Post Media</div>
    </div>
    <div class="content" id="contentArea">
        <h1>Welcome to SNAPIO</h1>
    </div>
</div>

<script>
// DOM Bindings
const landingPage = document.getElementById("landingPage");
const registerPage = document.getElementById("registerPage");
const loginPage = document.getElementById("loginPage");
const dashboard = document.getElementById("dashboard");
const contentArea = document.getElementById("contentArea");
const registerMessage = document.getElementById("registerMessage");
const loginMessage = document.getElementById("loginMessage");

let users = JSON.parse(localStorage.getItem("snapio_users")) || [];
let currentUser = JSON.parse(localStorage.getItem("snapio_currentUser"));

if(currentUser){
    openDashboard();
}

function showRegister(){
    landingPage.classList.add("hidden");
    registerPage.classList.remove("hidden");
}

function showLogin(){
    landingPage.classList.add("hidden");
    loginPage.classList.remove("hidden");
}

function register(){
    const username = document.getElementById("registerUsername").value.trim();
    const password = document.getElementById("registerPassword").value;

    if(username === "" || password === ""){
        registerMessage.innerHTML = "Fill in all fields";
        return;
    }

    const exists = users.find(user => user.username.toLowerCase() === username.toLowerCase());

    if(exists){
        registerMessage.innerHTML = "Username already taken";
        return;
    }

    users.push({
        username,
        password,
        friends: [],
        requests: []
    });

    localStorage.setItem("snapio_users", JSON.stringify(users));
    registerMessage.innerHTML = "Account created! You can now sign in.";
}

function login(){
    const username = document.getElementById("loginUsername").value.trim();
    const password = document.getElementById("loginPassword").value;

    const user = users.find(u => u.username === username && u.password === password);

    if(!user){
        loginMessage.innerHTML = "Invalid username or password";
        return;
    }

    localStorage.setItem("snapio_currentUser", JSON.stringify(user));
    currentUser = user;
    openDashboard();
}

function openDashboard(){
    landingPage.classList.add("hidden");
    registerPage.classList.add("hidden");
    loginPage.classList.add("hidden");
    dashboard.classList.remove("hidden");
    contentArea.innerHTML = `<h1>Welcome ${currentUser.username}</h1>`;
}

function showFriendsPage(){
    const latestUsers = JSON.parse(localStorage.getItem("snapio_users")) || [];
    const me = latestUsers.find(u => u.username === currentUser.username);

    contentArea.innerHTML = `
        <div class="page-title">Friends</div>
        <div class="friend-card">
            <h3>Friends Count: ${me.friends ? me.friends.length : 0}</h3>
            <div class="search-user">
                <input id="friendSearch" class="input" placeholder="Type username">
                <button onclick="searchUser()">Search User</button>
            </div>
            <div id="searchResult" style="margin-top: 15px;"></div>
            
            <div class="request-box">
                <h3>Incoming Friend Requests (${me.requests ? me.requests.length : 0}):</h3>
                <div id="requestList"></div>
            </div>
        </div>
    `;
    renderRequests();
}

function searchUser(){
    const username = document.getElementById("friendSearch").value.trim();
    const latestUsers = JSON.parse(localStorage.getItem("snapio_users")) || [];
    const searchResult = document.getElementById("searchResult");

    if(!username) {
        searchResult.innerHTML = "<p style='color: red;'>Please enter a name</p>";
        return;
    }

    const foundUser = latestUsers.find(u => u.username.toLowerCase() === username.toLowerCase());

    if(!foundUser){
        searchResult.innerHTML = "<p style='color: red;'>User not found</p>";
        return;
    }

    if(foundUser.username === currentUser.username){
        searchResult.innerHTML = "<p style='color: orange;'>You cannot add yourself</p>";
        return;
    }

    // Safety check if arrays aren't loaded properly
    if(!foundUser.requests) foundUser.requests = [];
    if(!foundUser.friends) foundUser.friends = [];

    if(foundUser.friends.includes(currentUser.username)) {
        searchResult.innerHTML = `<p style='color: green;'>You are already friends with ${foundUser.username}!</p>`;
        return;
    }

    searchResult.innerHTML = `
        <div class="request-item">
            <span>Found User: <b>${foundUser.username}</b></span>
            <button class="action-btn" onclick="sendRequest('${foundUser.username}')">Send Request</button>
        </div>
    `;
}

function sendRequest(targetUsername){
    let latestUsers = JSON.parse(localStorage.getItem("snapio_users")) || [];
    const searchResult = document.getElementById("searchResult");
    
    const targetUser = latestUsers.find(u => u.username === targetUsername);

    if(!targetUser){
        searchResult.innerHTML = "<p style='color: red;'>Error sending request.</p>";
        return;
    }

    if(!targetUser.requests) targetUser.requests = [];

    const alreadySent = targetUser.requests.includes(currentUser.username);

    if(alreadySent){
        searchResult.innerHTML = `<p style='color: orange;'>Request already pending with ${targetUsername}.</p>`;
        return;
    }

    targetUser.requests.push(currentUser.username);
    localStorage.setItem("snapio_users", JSON.stringify(latestUsers));
    
    searchResult.innerHTML = `<p style='color: green;'>Friend request sent to ${targetUsername}!</p>`;
}

function renderRequests(){
    let latestUsers = JSON.parse(localStorage.getItem("snapio_users")) || [];
    const me = latestUsers.find(u => u.username === currentUser.username);
    const requestList = document.getElementById("requestList");

    if(!requestList) return;
    requestList.innerHTML = "";

    if(!me.requests || me.requests.length === 0){
        requestList.innerHTML = `<p style='color: #888; margin-top: 10px;'>No incoming requests.</p>`;
        return;
    }

    me.requests.forEach(sender => {
        requestList.innerHTML += `
            <div class="request-item">
                <span><b>${sender}</b> wants to be your friend</span>
                <div>
                    <button class="action-btn" onclick="acceptRequest('${sender}')">Accept</button>
                    <button class="decline-btn" onclick="declineRequest('${sender}')">Decline</button>
                </div>
            </div>
        `;
    });
}

function acceptRequest(sender){
    let latestUsers = JSON.parse(localStorage.getItem("snapio_users")) || [];
    const me = latestUsers.find(u => u.username === currentUser.username);
    const senderUser = latestUsers.find(u => u.username === sender);

    if(!me || !senderUser) return;

    if(!me.friends) me.friends = [];
    if(!senderUser.friends) senderUser.friends = [];

    if(!me.friends.includes(sender)){
        me.friends.push(sender);
    }

    if(!senderUser.friends.includes(currentUser.username)){
        senderUser.friends.push(currentUser.username);
    }

    me.requests = me.requests.filter(req => req !== sender);

    localStorage.setItem("snapio_users", JSON.stringify(latestUsers));
    currentUser = me;
    localStorage.setItem("snapio_currentUser", JSON.stringify(me));

    showFriendsPage();
}

function declineRequest(sender){
    let latestUsers = JSON.parse(localStorage.getItem("snapio_users")) || [];
    const me = latestUsers.find(u => u.username === currentUser.username);

    if(!me) return;

    me.requests = me.requests.filter(req => req !== sender);

    localStorage.setItem("snapio_users", JSON.stringify(latestUsers));
    currentUser = me;
    localStorage.setItem("snapio_currentUser", JSON.stringify(me));

    showFriendsPage();
}
</script>

</body>
</html>
