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
            background: #10b981;
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

        .input, .select{
            width: 100%;
            padding: 14px;
            margin-top: 10px;
            border: 1px solid #ddd;
            border-radius: 10px;
            font-size: 15px;
            background: white;
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
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        .sidebar-logo{
            font-size: 32px;
            font-weight: bold;
            margin-bottom: 30px;
        }

        .sidebar-menu {
            display: flex;
            flex-direction: column;
            flex: 1;
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

        .logout-sidebar-btn {
            background: #ef4444;
            color: white;
            text-align: center;
            font-weight: bold;
        }

        .logout-sidebar-btn:hover {
            background: #dc2626;
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

        /* REGION TOGGLE TABS */
        .feed-filter-tabs {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
            background: #e2e8f0;
            padding: 5px;
            border-radius: 10px;
            max-width: 500px;
        }

        .filter-tab-btn {
            flex: 1;
            padding: 10px;
            border: none;
            background: transparent;
            font-weight: bold;
            color: #4b5563;
            cursor: pointer;
            border-radius: 8px;
            transition: 0.2s;
            font-size: 14px;
        }

        .filter-tab-btn.active {
            background: white;
            color: #2563eb;
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
        }

        /* POST MEDIA STYLES */
        .media-upload-box {
            max-width: 500px;
            background: #f8fafc;
            border: 2px dashed #cbd5e1;
            border-radius: 15px;
            padding: 30px;
            text-align: center;
            margin-top: 15px;
        }

        .preview-container-box {
            max-width: 100%;
            margin-top: 15px;
            border-radius: 10px;
            overflow: hidden;
            background: #e2e8f0;
        }

        .preview-container-box img, .preview-container-box video {
            max-width: 100%;
            max-height: 300px;
            display: block;
            margin: 0 auto;
        }

        /* FEED / FEED POST STYLES */
        .feed-container {
            max-width: 600px;
            margin: 0 auto;
        }

        .post-card {
            background: white;
            border: 1px solid #e2e8f0;
            border-radius: 16px;
            padding: 20px;
            margin-bottom: 25px;
            box-shadow: 0 4px 6px -1px rgba(0,0,0,0.05);
        }

        .post-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 15px;
        }

        .post-user-details {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .post-media-display {
            width: 100%;
            border-radius: 12px;
            background: #000;
            max-height: 400px;
            object-fit: contain;
            margin-bottom: 12px;
        }

        .post-actions {
            display: flex;
            gap: 15px;
            margin-bottom: 15px;
        }

        .post-btn {
            background: #f1f5f9;
            border: none;
            padding: 8px 16px;
            border-radius: 20px;
            font-weight: bold;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 6px;
            transition: 0.2s;
        }

        .post-btn:hover {
            background: #e2e8f0;
        }

        .post-btn.liked {
            background: #ef4444;
            color: white;
        }

        .comment-section {
            border-top: 1px solid #f1f5f9;
            padding-top: 12px;
        }

        .comment-item {
            font-size: 14px;
            margin-bottom: 6px;
            color: #374151;
        }

        /* PROFILE SCREEN CONTROLS */
        .profile-container {
            max-width: 500px;
            background: #f8fafc;
            border-radius: 20px;
            padding: 30px;
            margin: 25px auto 30px auto;
            text-align: center;
        }

        .action-btn-styled {
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

        @media (max-width: 768px) {
            #dashboard { flex-direction: column; }
            .sidebar { width: 100%; padding: 15px; align-items: center; border-bottom: 1px solid #1f2937; }
            .sidebar-logo { margin-bottom: 15px; font-size: 28px; }
            .sidebar-menu { flex-direction: row; flex-wrap: wrap; justify-content: center; gap: 8px; width: 100%; margin-bottom: 10px; }
            .sidebar-item { margin-top: 0; padding: 10px 15px; font-size: 14px; background: #1f2937; }
            .content { padding: 20px 15px; }
        }
    </style>

    <script src="https://www.gstatic.com/firebasejs/10.8.0/firebase-app-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/10.8.0/firebase-firestore-compat.js"></script>
</head>
<body>

<div id="landingPage">
    <div class="landing-card">
        <div class="logo">SNAPIO</div>
        <div class="subtitle">Connect regionally with phone integration.</div>
        <button class="main-btn create-btn" onclick="showRegister()">Create Account</button>
        <button class="main-btn login-btn" onclick="showLogin()">Sign In</button>
    </div>
</div>

<div id="registerPage" class="auth-page hidden">
    <div class="auth-box">
        <h1 class="auth-title">Create Account</h1>
        <input id="registerPhone" class="input" type="tel" placeholder="Phone Number (e.g., +31612345678)">
        <input id="registerUsername" class="input" placeholder="Display Name / Username">
        <input id="registerPassword" class="input" type="password" placeholder="Password">
        <button class="main-btn create-btn" onclick="register()">Create Account</button>
        <div id="registerMessage" style="margin-top: 10px; color: red; text-align: center;"></div>
    </div>
</div>

<div id="loginPage" class="auth-page hidden">
    <div class="auth-box">
        <h1 class="auth-title">Sign In</h1>
        <input id="loginPhone" class="input" type="tel" placeholder="Phone Number (e.g., +31612345678)">
        <input id="loginPassword" class="input" type="password" placeholder="Password">
        <button class="main-btn login-btn" onclick="login()">Sign In</button>
        <div id="loginMessage" style="margin-top: 10px; color: red; text-align: center;"></div>
    </div>
</div>

<div id="dashboard" class="hidden">
    <div class="sidebar">
        <div>
            <div class="sidebar-logo">SNAPIO</div>
            <div class="sidebar-menu">
                <div class="sidebar-item" onclick="showForYouPage()">For You</div>
                <div class="sidebar-item" onclick="showPostMediaPage()">Post Media</div>
                <div class="sidebar-item" onclick="showOwnProfile()">Profile</div>
            </div>
        </div>
        <div class="sidebar-item logout-sidebar-btn" onclick="logoutUser()">Switch Account</div>
    </div>
    <div class="content" id="contentArea">
        <h1>Loading Content Hub...</h1>
    </div>
</div>

<script>
// --- PASTE YOUR FIREBASE WEB APP CONFIG CONFIGURATION BOX LOGISTICS HERE ---
const firebaseConfig = {
    apiKey: "YOUR_API_KEY",
    authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
    projectId: "YOUR_PROJECT_ID",
    storageBucket: "YOUR_PROJECT_ID.appspot.com",
    messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
    appId: "YOUR_APP_ID"
};

// Initialize Firebase Real-Time Ecosystem Connections
firebase.initializeApp(firebaseConfig);
const db = firebase.firestore();

// DOM Bindings
const landingPage = document.getElementById("landingPage");
const registerPage = document.getElementById("registerPage");
const loginPage = document.getElementById("loginPage");
const dashboard = document.getElementById("dashboard");
const contentArea = document.getElementById("contentArea");
const registerMessage = document.getElementById("registerMessage");
const loginMessage = document.getElementById("loginMessage");

const defaultPfp = "https://cdn-icons-png.flaticon.com/512/149/149071.png";
let base64PostMediaStorage = "";
let postFileTypeStorage = ""; 
let currentFeedScope = "allPhoneUsers"; // Options: "allPhoneUsers" or "myCountryCode"
let currentUser = JSON.parse(sessionStorage.getItem("snapio_active_user")) || null;

if (currentUser) {
    openDashboard();
}

function showRegister(){
    document.getElementById("registerPhone").value = "";
    document.getElementById("registerUsername").value = "";
    document.getElementById("registerPassword").value = "";
    registerMessage.innerHTML = "";
    landingPage.classList.add("hidden");
    loginPage.classList.add("hidden");
    registerPage.classList.remove("hidden");
}

function showLogin(){
    document.getElementById("loginPhone").value = "";
    document.getElementById("loginPassword").value = "";
    loginMessage.innerHTML = "";
    landingPage.classList.add("hidden");
    registerPage.classList.add("hidden");
    loginPage.classList.remove("hidden");
}

function logoutUser() {
    sessionStorage.removeItem("snapio_active_user");
    currentUser = null;
    dashboard.classList.add("hidden");
    landingPage.classList.remove("hidden");
}

function register(){
    const phone = document.getElementById("registerPhone").value.trim();
    const username = document.getElementById("registerUsername").value.trim();
    const password = document.getElementById("registerPassword").value;

    if(!phone || !username || !password){
        registerMessage.style.color = "red";
        registerMessage.innerHTML = "Fill in all fields";
        return;
    }

    // Verify if phone is already inside database collection infrastructure
    db.collection("users").doc(phone).get().then((doc) => {
        if (doc.exists) {
            registerMessage.style.color = "red";
            registerMessage.innerHTML = "Phone number already registered!";
        } else {
            const newUserObj = { phone, username, password, pfp: defaultPfp };
            db.collection("users").doc(phone).set(newUserObj).then(() => {
                registerMessage.style.color = "green";
                registerMessage.innerHTML = "Account created! Loading login...";
                setTimeout(() => { showLogin(); }, 1200);
            });
        }
    });
}

function login(){
    const phone = document.getElementById("loginPhone").value.trim();
    const password = document.getElementById("loginPassword").value;

    if(!phone || !password) {
        loginMessage.innerHTML = "Please type values.";
        return;
    }

    db.collection("users").doc(phone).get().then((doc) => {
        if(doc.exists && doc.data().password === password) {
            currentUser = doc.data();
            sessionStorage.setItem("snapio_active_user", JSON.stringify(currentUser));
            openDashboard();
        } else {
            loginMessage.style.color = "red";
            loginMessage.innerHTML = "Invalid phone structure profile configuration credentials.";
        }
    }).catch(() => {
        loginMessage.innerHTML = "Authentication cloud connectivity failure.";
    });
}

function openDashboard(){
    landingPage.classList.add("hidden");
    registerPage.classList.add("hidden");
    loginPage.classList.add("hidden");
    dashboard.classList.remove("hidden");
    showForYouPage();
}

function showPostMediaPage() {
    base64PostMediaStorage = "";
    postFileTypeStorage = "";

    contentArea.innerHTML = `
        <div class="page-title">Publish Media</div>
        <div style="max-width: 500px;">
            <p style="color:#555; margin-bottom: 15px;">Broadcast media out to all verification systems securely tagged under account metadata.</p>
            
            <div class="media-upload-box">
                <label class="file-upload-btn" style="background:#2563eb;">
                    Select Photo or Video File
                    <input type="file" id="postFileInput" accept="image/*,video/*" style="display:none;" onchange="processPostFile(this)">
                </label>
                <div id="postMediaPreviewContainer" class="preview-container-box hidden"></div>
            </div>

            <label style="display:inline-block; margin-top:20px;"><b>Post Headline Caption</b></label>
            <input id="postTitleInput" class="input" placeholder="Say something about this media asset...">

            <button class="action-btn-styled" style="width: 100%; margin-top:25px; background:#10b981;" onclick="submitNewPost()">Publish to Network</button>
            <div id="uploadError" style="margin-top:10px; color:red; text-align:center; font-weight:bold;"></div>
        </div>
    `;
}

function processPostFile(input) {
    const file = input.files[0];
    const previewContainer = document.getElementById("postMediaPreviewContainer");
    if (!file || !previewContainer) return;

    postFileTypeStorage = file.type.startsWith("image/") ? "image" : "video";

    const reader = new FileReader();
    reader.onload = function(e) {
        base64PostMediaStorage = e.target.result;
        previewContainer.classList.remove("hidden");
        previewContainer.innerHTML = postFileTypeStorage === "image" 
            ? `<img src="${base64PostMediaStorage}">` 
            : `<video src="${base64PostMediaStorage}" controls muted></video>`;
    };
    reader.readAsDataURL(file);
}

function submitNewPost() {
    const title = document.getElementById("postTitleInput").value.trim();
    const errorDiv = document.getElementById("uploadError");

    if (!base64PostMediaStorage || !title) {
        errorDiv.innerHTML = "Please include missing form submission values!";
        return;
    }

    const newPost = {
        author: currentUser.username,
        authorPhone: currentUser.phone, 
        title: title,
        media: base64PostMediaStorage,
        type: postFileTypeStorage,
        likes: [],
        timestamp: Date.now()
    };

    db.collection("posts").add(newPost).then(() => {
        showForYouPage();
    }).catch(err => {
        errorDiv.innerHTML = "Upload failure matrix: " + err;
    });
}

function showForYouPage() {
    // Dynamically calculate Country Code Prefix (e.g., first 3 characters "+31")
    const structuralPrefix = currentUser.phone.startsWith("+") 
        ? currentUser.phone.substring(0, 3) 
        : currentUser.phone.substring(0, 2);

    contentArea.innerHTML = `
        <div class="page-title">Community Feed</div>
        
        <div class="feed-filter-tabs">
            <button id="tabBtnGlobal" class="filter-tab-btn ${currentFeedScope === 'allPhoneUsers' ? 'active' : ''}" onclick="changeFeedScope('allPhoneUsers')">All Phone Accounts</button>
            <button id="tabBtnRegional" class="filter-tab-btn ${currentFeedScope === 'myCountryCode' ? 'active' : ''}" onclick="changeFeedScope('myCountryCode')">📍 Area Prefix (${structuralPrefix})</button>
        </div>

        <div class="feed-container" id="feedPostsStream">Loading Live Stream...</div>
    `;
    renderFeedStream();
}

function changeFeedScope(newScope) {
    currentFeedScope = newScope;
    document.getElementById("tabBtnGlobal").classList.toggle("active", newScope === 'allPhoneUsers');
    document.getElementById("tabBtnRegional").classList.toggle("active", newScope === 'myCountryCode');
    renderFeedStream();
}

function renderFeedStream() {
    const streamContainer = document.getElementById("feedPostsStream");
    if (!streamContainer) return;

    db.collection("posts").orderBy("timestamp", "desc").get().then((querySnapshot) => {
        let loadedPosts = [];
        querySnapshot.forEach((doc) => {
            let pData = doc.data();
            pData.id = doc.id;
            loadedPosts.push(pData);
        });

        // Filter 1: Enforce presence of registration database metadata signatures 
        let filteredStream = loadedPosts.filter(p => p.authorPhone && p.authorPhone.trim() !== "");

        // Filter 2: Optional validation check against phone country dialing signature values
        if (currentFeedScope === "myCountryCode") {
            const myPrefix = currentUser.phone.startsWith("+") ? currentUser.phone.substring(0, 3) : currentUser.phone.substring(0, 2);
            filteredStream = filteredStream.filter(p => p.authorPhone.startsWith(myPrefix));
        }

        if (filteredStream.length === 0) {
            streamContainer.innerHTML = `<p style='text-align:center; color:#888; margin-top:40px;'>No verified mobile network posts found inside view matrix.</p>`;
            return;
        }

        streamContainer.innerHTML = "";
        filteredStream.forEach(post => {
            const cardElement = document.createElement("div");
            cardElement.className = "post-card";

            let assetTag = post.type === "video" 
                ? `<video class="post-media-display" src="${post.media}" controls></video>` 
                : `<img class="post-media-display" src="${post.media}">`;

            const hasLiked = post.likes && post.likes.includes(currentUser.phone);
            const likeClass = hasLiked ? "post-btn liked" : "post-btn";

            cardElement.innerHTML = `
                <div class="post-header">
                    <div class="post-user-details">
                        <img class="pfp-circle" src="${defaultPfp}">
                        <div>
                            <strong>${post.author}</strong>
                            <div style="font-size:12px; color:#6b7280;">📱 ${post.authorPhone}</div>
                        </div>
                    </div>
                </div>
                <p style="margin-bottom:12px; color:#1f2937;">${post.title}</p>
                ${assetTag}
                <div class="post-actions">
                    <button class="${likeClass}" onclick="toggleLikePost('${post.id}')">
                        ♥ <span>${post.likes ? post.likes.length : 0}</span>
                    </button>
                </div>
            `;
            streamContainer.appendChild(cardElement);
        });
    }).catch(err => {
        streamContainer.innerHTML = "Database operational loading error: " + err;
    });
}

function toggleLikePost(postId) {
    const postRef = db.collection("posts").doc(postId);
    db.runTransaction((transaction) => {
        return transaction.get(postRef).then((sfDoc) => {
            if (!sfDoc.exists) return;
            let currentLikesArray = sfDoc.data().likes || [];
            const userIndex = currentLikesArray.indexOf(currentUser.phone);
            
            if (userIndex === -1) {
                currentLikesArray.push(currentUser.phone);
            } else {
                currentLikesArray.splice(userIndex, 1);
            }
            transaction.update(postRef, { likes: currentLikesArray });
        });
    }).then(() => {
        renderFeedStream();
    });
}

function showOwnProfile() {
    contentArea.innerHTML = `
        <div class="page-title">Account Details</div>
        <div class="profile-container">
            <img class="pfp-circle" src="${defaultPfp}" style="width:100px; height:100px; margin-bottom:15px;">
            <h2>${currentUser.username}</h2>
            <p style="color:#4b5563; margin-top:5px; font-weight:bold;">Verified Phone ID: ${currentUser.phone}</p>
            <p style="font-size:13px; color:#9ca3af; margin-top:10px;">Authenticated cloud storage profile active node.</p>
        </div>
    `;
}
</script>
</body>
</html>
