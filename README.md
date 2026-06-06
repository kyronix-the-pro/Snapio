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
            min-height: 100vh;
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
            padding: 20px;
        }

        .landing-card{
            background: white;
            padding: 40px 30px;
            width: 100%;
            max-width: 450px;
            border-radius: 20px;
            text-align: center;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }

        .logo{
            font-size: clamp(40px, 8vw, 60px);
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
            width: 100%;
            max-width: 450px;
            padding: 30px 25px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,.15);
        }

        .auth-page{
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
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

        /* DASHBOARD RESPONSIVE LAYOUT */
        #dashboard{
            display: flex;
            flex-direction: row;
            min-height: 100vh;
        }

        .sidebar{
            width: 260px;
            background: #111827;
            color: white;
            padding: 20px;
            flex-shrink: 0;
        }

        .sidebar-logo{
            font-size: 32px;
            font-weight: bold;
            margin-bottom: 30px;
        }

        .sidebar-menu {
            display: flex;
            flex-direction: column;
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
            overflow-y: auto;
        }

        .page-title{
            font-size: 32px;
            margin-bottom: 15px;
            font-weight: bold;
        }

        .friend-card{
            background: #f8fafc;
            border-radius: 15px;
            padding: 20px;
            margin-top: 20px;
        }

        /* FRIENDS GRID */
        .friends-list-container {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin: 15px 0 30px 0;
        }

        .friend-user-node {
            background: white;
            border: 1px solid #e2e8f0;
            padding: 10px 15px;
            border-radius: 50px;
            display: flex;
            align-items: center;
            gap: 10px;
            cursor: pointer;
            transition: 0.2s;
        }

        .friend-user-node:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 10px rgba(0,0,0,0.05);
            border-color: #2563eb;
        }

        .pfp-circle {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            object-fit: cover;
            background: #cbd5e1;
        }

        .pfp-circle-large {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            object-fit: cover;
            background: #cbd5e1;
            margin-bottom: 15px;
        }

        .search-user{
            display: flex;
            gap: 10px;
            margin-top: 15px;
        }

        .search-user .input{
            margin-top: 0;
        }

        .search-user button, .action-btn-styled {
            padding: 14px 20px;
            border: none;
            border-radius: 10px;
            background: #2563eb;
            color: white;
            cursor: pointer;
            white-space: nowrap;
            font-weight: bold;
        }

        .file-upload-btn {
            display: inline-block;
            background: #4b5563;
            color: white;
            padding: 10px 15px;
            border-radius: 8px;
            font-size: 14px;
            font-weight: bold;
            cursor: pointer;
            margin-top: 8px;
        }

        .request-box{
            margin-top: 30px;
            border-top: 2px dashed #e2e8f0;
            padding-top: 20px;
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
            gap: 15px;
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

        /* PROFILE */
        .profile-container {
            max-width: 500px;
            background: #f8fafc;
            border-radius: 20px;
            padding: 30px;
            margin-top: 25px;
            text-align: center;
        }

        .bio-text {
            color: #4b5563;
            margin: 10px 0 20px 0;
            font-style: italic;
        }

        /* MOBILE MEDIA QUERIES */
        @media (max-width: 768px) {
            #dashboard {
                flex-direction: column;
            }

            .sidebar {
                width: 100%;
                padding: 15px;
                display: flex;
                flex-direction: column;
                align-items: center;
                border-bottom: 1px solid #1f2937;
            }

            .sidebar-logo {
                margin-bottom: 15px;
                font-size: 28px;
            }

            .sidebar-menu {
                flex-direction: row;
                flex-wrap: wrap;
                justify-content: center;
                gap: 8px;
                width: 100%;
            }

            .sidebar-item {
                margin-top: 0;
                padding: 10px 15px;
                font-size: 14px;
                background: #1f2937;
            }

            .content {
                padding: 20px 15px;
            }

            .search-user {
                flex-direction: column;
            }

            .search-user button {
                width: 100%;
            }

            .request-item {
                flex-direction: column;
                align-items: flex-start;
            }

            .request-item div {
                width: 100%;
                display: flex;
                justify-content: flex-end;
                margin-top: 5px;
            }
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
        <div id="registerMessage" style="margin-top: 10px; color: red; text-align: center;"></div>
    </div>
</div>

<div id="loginPage" class="auth-page hidden">
    <div class="auth-box">
        <h1 class="auth-title">Sign In</h1>
        <input id="loginUsername" class="input" placeholder="Username">
        <input id="loginPassword" class="input" type="password" placeholder="Password">
        <button class="main-btn login-btn" onclick="login()">Sign In</button>
        <div id="loginMessage" style="margin-top: 10px; color: red; text-align: center;"></div>
    </div>
</div>

<div id="dashboard" class="hidden">
    <div class="sidebar">
        <div class="sidebar-logo">SNAPIO</div>
        <div class="sidebar-menu">
            <div class="sidebar-item" onclick="showFriendsPage()">Friends</div>
            <div class="sidebar-item" onclick="showOwnProfile()">Profile</div>
            <div class="sidebar-item" onclick="alert('Chats coming soon!')">Chats</div>
            <div class="sidebar-item" onclick="alert('For You coming soon!')">For You</div>
            <div class="sidebar-item" onclick="alert('Post Media coming soon!')">Post Media</div>
        </div>
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

const defaultPfp = "https://cdn-icons-png.flaticon.com/512/149/149071.png";

// Temporary placeholder for custom file uploads
let base64ImageStorage = "";

function getUsers() {
    return JSON.parse(localStorage.getItem("snapio_users")) || [];
}

function getCurrentUser() {
    return JSON.parse(localStorage.getItem("snapio_currentUser"));
}

let currentUser = getCurrentUser();

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
    let localUsers = getUsers();

    if(username === "" || password === ""){
        registerMessage.innerHTML = "Fill in all fields";
        return;
    }

    const exists = localUsers.find(user => user.username.toLowerCase() === username.toLowerCase());

    if(exists){
        registerMessage.innerHTML = "Username already taken";
        return;
    }

    localUsers.push({
        username,
        password,
        bio: "Hey there! I am using SNAPIO.",
        pfp: defaultPfp,
        friends: [],
        requests: []
    });

    localStorage.setItem("snapio_users", JSON.stringify(localUsers));
    registerMessage.style.color = "green";
    registerMessage.innerHTML = "Account created! Loading login...";
    setTimeout(() => { showLogin(); }, 1200);
}

function login(){
    const username = document.getElementById("loginUsername").value.trim();
    const password = document.getElementById("loginPassword").value;
    let localUsers = getUsers();

    const user = localUsers.find(u => u.username.toLowerCase() === username.toLowerCase() && u.password === password);

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
    contentArea.innerHTML = `<h1>Welcome ${currentUser.username}</h1><p style='color: #666; margin-top:10px;'>Select an option from the menu to navigate.</p>`;
}

/* FRIENDS SECTION */
function showFriendsPage(){
    let localUsers = getUsers();
    let me = localUsers.find(u => u.username.toLowerCase() === currentUser.username.toLowerCase());

    contentArea.innerHTML = `
        <div class="page-title">Friends</div>
        <h3>Friends: ${me.friends ? me.friends.length : 0}</h3>
        
        <div class="friends-list-container" id="friendsVisualContainer"></div>

        <div class="friend-card">
            <h4>Search Username</h4>
            <div class="search-user">
                <input id="friendSearch" class="input" placeholder="Type username">
                <button onclick="searchUser()">Search User</button>
            </div>
            <div id="searchResult" style="margin-top: 15px;"></div>
            
            <div class="request-box">
                <h3>Requests: ${me.requests ? me.requests.length : 0}</h3>
                <div id="requestList"></div>
            </div>
        </div>
    `;

    renderVisualFriends(me, localUsers);
    renderRequests();
}

function renderVisualFriends(me, localUsers) {
    const container = document.getElementById("friendsVisualContainer");
    if (!container) return;
    container.innerHTML = "";

    if (!me.friends || me.friends.length === 0) {
        container.innerHTML = "<p style='color: #888;'>You haven't added any friends yet.</p>";
        return;
    }

    me.friends.forEach(friendName => {
        const targetFriendObj = localUsers.find(u => u.username.toLowerCase() === friendName.toLowerCase());
        const pfpSrc = (targetFriendObj && targetFriendObj.pfp) ? targetFriendObj.pfp : defaultPfp;

        const friendNode = document.createElement("div");
        friendNode.className = "friend-user-node";
        friendNode.onclick = () => { showTargetUserProfile(targetFriendObj ? targetFriendObj.username : friendName); };
        friendNode.innerHTML = `
            <img class="pfp-circle" src="${pfpSrc}" alt="pfp">
            <span><b>${targetFriendObj ? targetFriendObj.username : friendName}</b></span>
        `;
        container.appendChild(friendNode);
    });
}

function searchUser(){
    const username = document.getElementById("friendSearch").value.trim().toLowerCase();
    let localUsers = getUsers();
    const searchResult = document.getElementById("searchResult");

    if(!username) {
        searchResult.innerHTML = "<p style='color: red;'>Please enter a name</p>";
        return;
    }

    const foundUser = localUsers.find(u => u.username.toLowerCase() === username);

    if(!foundUser){
        searchResult.innerHTML = "<p style='color: red;'>User not found</p>";
        return;
    }

    if(foundUser.username.toLowerCase() === currentUser.username.toLowerCase()){
        searchResult.innerHTML = "<p style='color: orange;'>You cannot add yourself</p>";
        return;
    }

    if(!foundUser.requests) foundUser.requests = [];
    if(!foundUser.friends) foundUser.friends = [];

    if(foundUser.friends.some(f => f.toLowerCase() === currentUser.username.toLowerCase())) {
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
    let localUsers = getUsers();
    const searchResult = document.getElementById("searchResult");
    
    const targetUser = localUsers.find(u => u.username.toLowerCase() === targetUsername.toLowerCase());

    if(!targetUser){
        searchResult.innerHTML = "<p style='color: red;'>Error sending request.</p>";
        return;
    }

    if(!targetUser.requests) targetUser.requests = [];

    const alreadySent = targetUser.requests.some(r => r.toLowerCase() === currentUser.username.toLowerCase());

    if(alreadySent){
        searchResult.innerHTML = `<p style='color: orange;'>Request already pending with ${targetUser.username}.</p>`;
        return;
    }

    targetUser.requests.push(currentUser.username);
    localStorage.setItem("snapio_users", JSON.stringify(localUsers));
    
    searchResult.innerHTML = `<p style='color: green;'>Friend request sent to ${targetUser.username}!</p>`;
}

function renderRequests(){
    let localUsers = getUsers();
    const me = localUsers.find(u => u.username.toLowerCase() === currentUser.username.toLowerCase());
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
    let localUsers = getUsers();
    const me = localUsers.find(u => u.username.toLowerCase() === currentUser.username.toLowerCase());
    const senderUser = localUsers.find(u => u.username.toLowerCase() === sender.toLowerCase());

    if(!me || !senderUser) return;

    if(!me.friends) me.friends = [];
    if(!senderUser.friends) senderUser.friends = [];

    if(!me.friends.some(f => f.toLowerCase() === sender.toLowerCase())){
        me.friends.push(senderUser.username);
    }

    if(!senderUser.friends.some(f => f.toLowerCase() === me.username.toLowerCase())){
        senderUser.friends.push(me.username);
    }

    me.requests = me.requests.filter(req => req.toLowerCase() !== sender.toLowerCase());

    localStorage.setItem("snapio_users", JSON.stringify(localUsers));
    localStorage.setItem("snapio_currentUser", JSON.stringify(me));
    currentUser = me;

    showFriendsPage();
}

function declineRequest(sender){
    let localUsers = getUsers();
    const me = localUsers.find(u => u.username.toLowerCase() === currentUser.username.toLowerCase());

    if(!me) return;

    me.requests = me.requests.filter(req => req.toLowerCase() !== sender.toLowerCase());

    localStorage.setItem("snapio_users", JSON.stringify(localUsers));
    localStorage.setItem("snapio_currentUser", JSON.stringify(me));
    currentUser = me;

    showFriendsPage();
}

/* PROFILE SECTION */
function showOwnProfile() {
    let localUsers = getUsers();
    const me = localUsers.find(u => u.username.toLowerCase() === currentUser.username.toLowerCase());

    const currentPfp = me.pfp || defaultPfp;
    const currentBio = me.bio || "No bio set yet.";
    const totalFriends = me.friends ? me.friends.length : 0;

    contentArea.innerHTML = `
        <div class="page-title">My Profile</div>
        <div class="profile-container">
            <img class="pfp-circle-large" src="${currentPfp}" alt="Profile Picture">
            <h2>${me.username}</h2>
            <p class="bio-text">"${currentBio}"</p>
            <p style="margin-bottom: 20px; font-weight: bold; color:#2563eb;">Friends count: ${totalFriends}</p>
            <button class="action-btn-styled" onclick="showCustomizeInterface()">Customize Profile</button>
        </div>
    `;
}

function showCustomizeInterface() {
    let localUsers = getUsers();
    const me = localUsers.find(u => u.username.toLowerCase() === currentUser.username.toLowerCase());
    base64ImageStorage = me.pfp || defaultPfp;

    contentArea.innerHTML = `
        <div class="page-title">Apply Changes</div>
        <div class="profile-container" style="text-align: left;">
            <p style="margin-bottom: 15px; color: #555;">Update your information below, then tap Apply Updates.</p>
            
            <label><b>Profile Picture</b></label><br>
            <div style="display:flex; align-items:center; gap: 15px; margin-top:8px;">
                <img id="previewPfp" class="pfp-circle" src="${base64ImageStorage}" alt="preview">
                <label class="file-upload-btn">
                    Choose Photo File
                    <input type="file" id="fileInput" accept="image/*" style="display:none;" onchange="processFilePfp(this)">
                </label>
            </div>
            
            <label style="display:inline-block; margin-top:20px;"><b>Username</b></label>
            <input id="editName" class="input" value="${me.username}" placeholder="Change username">
            
            <label style="display:inline-block; margin-top:15px;"><b>Bio Description</b></label>
            <input id="editBio" class="input" value="${me.bio || ''}" placeholder="Tell us about yourself">
            
            <div style="margin-top: 25px; display:flex; gap: 10px;">
                <button class="action-btn-styled" style="background:#10b981; flex: 1;" onclick="applyProfileChanges()">Apply Updates</button>
                <button class="action-btn-styled" style="background:#6b7280;" onclick="showOwnProfile()">Cancel</button>
            </div>
            <div id="editError" style="margin-top:10px; color:red; text-align:center;"></div>
        </div>
    `;
}

function processFilePfp(input) {
    const file = input.files[0];
    if (file) {
        const reader = new FileReader();
        reader.onload = function(e) {
            base64ImageStorage = e.target.result;
            document.getElementById("previewPfp").src = base64ImageStorage;
        };
        reader.readAsDataURL(file);
    }
}

function applyProfileChanges() {
    const updatedName = document.getElementById("editName").value.trim();
    const updatedBio = document.getElementById("editBio").value.trim();
    const errorDiv = document.getElementById("editError");

    if(!updatedName) {
        errorDiv.innerHTML = "Username cannot be empty!";
        return;
    }

    let localUsers = getUsers();
    
    if (updatedName.toLowerCase() !== currentUser.username.toLowerCase()) {
        const nameExists = localUsers.find(u => u.username.toLowerCase() === updatedName.toLowerCase());
        if(nameExists) {
            errorDiv.innerHTML = "This username is already taken!";
            return;
        }

        // Rename across other profiles' databases
        localUsers.forEach(u => {
            if(u.friends) u.friends = u.friends.map(f => f.toLowerCase() === currentUser.username.toLowerCase() ? updatedName : f);
            if(u.requests) u.requests = u.requests.map(r => r.toLowerCase() === currentUser.username.toLowerCase() ? updatedName : r);
        });
    }

    const userIndex = localUsers.findIndex(u => u.username.toLowerCase() === currentUser.username.toLowerCase());
    if(userIndex !== -1) {
        localUsers[userIndex].username = updatedName;
        localUsers[userIndex].pfp = base64ImageStorage;
        localUsers[userIndex].bio = updatedBio;

        localStorage.setItem("snapio_users", JSON.stringify(localUsers));
        
        currentUser = localUsers[userIndex];
        localStorage.setItem("snapio_currentUser", JSON.stringify(currentUser));
        
        showOwnProfile();
    }
}

/* EXTERNAL PROFILES */
function showTargetUserProfile(targetUsername) {
    let localUsers = getUsers();
    const matchedUser = localUsers.find(u => u.username.toLowerCase() === targetUsername.toLowerCase());

    if(!matchedUser) {
        alert("Could not load user profile.");
        return;
    }

    const currentPfp = matchedUser.pfp || defaultPfp;
    const currentBio = matchedUser.bio || "No description set.";
    const totalFriends = matchedUser.friends ? matchedUser.friends.length : 0;

    contentArea.innerHTML = `
        <div class="page-title">${matchedUser.username}'s Profile</div>
        <div class="profile-container">
            <img class="pfp-circle-large" src="${currentPfp}" alt="Profile Image">
            <h2>${matchedUser.username}</h2>
            <p class="bio-text">"${currentBio}"</p>
            <p style="margin-bottom: 20px; font-weight: bold; color:#2563eb;">Friends count: ${totalFriends}</p>
            <button class="action-btn-styled" style="background:#4b5563;" onclick="showFriendsPage()">Back to Friends</button>
        </div>
    `;
}
</script>

</body>
</html>
