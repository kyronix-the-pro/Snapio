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
            cursor: pointer;
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

        /* USER DISPLAY STYLES */
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

        /* PROFILE SCREEN CONTROLS */
        .profile-container {
            max-width: 500px;
            background: #f8fafc;
            border-radius: 20px;
            padding: 30px;
            margin: 25px auto 30px auto;
            text-align: center;
        }

        .bio-text {
            color: #4b5563;
            margin: 10px 0 20px 0;
            font-style: italic;
        }

        .stats-row {
            display: flex;
            justify-content: center;
            gap: 20px;
            font-weight: bold;
            color: #2563eb;
            margin-bottom: 20px;
            font-size: 16px;
        }

        .profile-posts-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }

        .grid-media-item {
            width: 100%;
            height: 150px;
            object-fit: cover;
            border-radius: 10px;
            background: #000;
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
            <div class="sidebar-item" onclick="showForYouPage()">For You</div>
            <div class="sidebar-item" onclick="showPostMediaPage()">Post Media</div>
            <div class="sidebar-item" onclick="showOwnProfile()">Profile</div>
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
let base64ImageStorage = "";
let base64PostMediaStorage = "";
let postFileTypeStorage = ""; // "image" or "video"

// Core Databases initialization
function getUsers() {
    return JSON.parse(localStorage.getItem("snapio_users")) || [];
}

function getPosts() {
    return JSON.parse(localStorage.getItem("snapio_posts")) || [];
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
        registerMessage.style.color = "red";
        registerMessage.innerHTML = "Fill in all fields";
        return;
    }

    const exists = localUsers.find(user => user.username.toLowerCase() === username.toLowerCase());

    if(exists){
        registerMessage.style.color = "red";
        registerMessage.innerHTML = "Username already taken";
        return;
    }

    localUsers.push({
        username,
        password,
        bio: "Hey there! I am using SNAPIO.",
        pfp: defaultPfp,
        friends: [],
        requests: [],
        followers: [],  // Usernames tracking followers
        following: [],  // Usernames tracking who this user follows
        likesReceived: 0
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
    showForYouPage();
}


/* =========================================================
   POST MEDIA TAB
   ========================================================= */
function showPostMediaPage() {
    base64PostMediaStorage = "";
    postFileTypeStorage = "";

    contentArea.innerHTML = `
        <div class="page-title">Post Media</div>
        <div style="max-width: 500px;">
            <p style="color:#555; margin-bottom: 15px;">Upload photos or videos, configure availability rules, and broadcast to the platform ecosystem instantly.</p>
            
            <div class="media-upload-box">
                <label class="file-upload-btn" style="background:#2563eb;">
                    Select Photo or Video File
                    <input type="file" id="postFileInput" accept="image/*,video/*" style="display:none;" onchange="processPostFile(this)">
                </label>
                <div id="postMediaPreviewContainer" class="preview-container-box hidden"></div>
            </div>

            <label style="display:inline-block; margin-top:20px;"><b>Post Title / Name</b></label>
            <input id="postTitleInput" class="input" placeholder="Enter a descriptive post name...">

            <label style="display:inline-block; margin-top:15px;"><b>Visibility Settings</b></label>
            <select id="postVisibilityInput" class="select">
                <option value="public">Public (Everyone can view)</option>
                <option value="friends">Friends Only (Visible to your friend list)</option>
                <option value="private">Private (Only you can view)</option>
            </select>

            <button class="action-btn-styled" style="width: 100%; margin-top:25px; background:#10b981;" onclick="submitNewPost()">Publish Post</button>
            <div id="uploadError" style="margin-top:10px; color:red; text-align:center; font-weight:bold;"></div>
        </div>
    `;
}

function processPostFile(input) {
    const file = input.files[0];
    const previewContainer = document.getElementById("postMediaPreviewContainer");
    
    if (!file || !previewContainer) return;

    if (file.type.startsWith("image/")) {
        postFileTypeStorage = "image";
    } else if (file.type.startsWith("video/")) {
        postFileTypeStorage = "video";
    } else {
        alert("Unsupported file type! Please select an image or video file.");
        return;
    }

    const reader = new FileReader();
    reader.onload = function(e) {
        base64PostMediaStorage = e.target.result;
        previewContainer.classList.remove("hidden");
        
        if (postFileTypeStorage === "image") {
            previewContainer.innerHTML = `<img src="${base64PostMediaStorage}" alt="Post Preview">`;
        } else {
            previewContainer.innerHTML = `<video src="${base64PostMediaStorage}" controls muted></video>`;
        }
    };
    reader.readAsDataURL(file);
}

function submitNewPost() {
    const title = document.getElementById("postTitleInput").value.trim();
    const visibility = document.getElementById("postVisibilityInput").value;
    const errorDiv = document.getElementById("uploadError");

    if (!base64PostMediaStorage) {
        errorDiv.innerHTML = "Please select a photo or video file first!";
        return;
    }
    if (!title) {
        errorDiv.innerHTML = "Please provide a name/title for your post!";
        return;
    }

    let localPosts = getPosts();
    const uniquePostId = "post_" + Date.now() + "_" + Math.floor(Math.random() * 1000);

    localPosts.push({
        id: uniquePostId,
        author: currentUser.username,
        title: title,
        media: base64PostMediaStorage,
        type: postFileTypeStorage,
        visibility: visibility,
        likes: [], // Usernames of people who liked
        comments: [], // Objects array: { commenter: 'name', text: 'message' }
        timestamp: Date.now()
    });

    localStorage.setItem("snapio_posts", JSON.stringify(localPosts));
    showForYouPage(); // Direct redirect to live feed after broadcast
}


/* =========================================================
   FOR YOU TAB (GLOBAL COMBINED STREAM FEED)
   ========================================================= */
function showForYouPage() {
    contentArea.innerHTML = `
        <div class="page-title">For You Feed</div>
        <div class="feed-container" id="feedPostsStream"></div>
    `;
    renderFeedStream();
}

function renderFeedStream() {
    const streamContainer = document.getElementById("feedPostsStream");
    if (!streamContainer) return;

    let localPosts = getPosts();
    let localUsers = getUsers();
    let me = localUsers.find(u => u.username.toLowerCase() === currentUser.username.toLowerCase());

    // Sort newer updates upwards
    localPosts.sort((a, b) => b.timestamp - a.timestamp);

    // Context filter definitions parsing logic rules safely
    const visiblePosts = localPosts.filter(post => {
        if (post.visibility === "public") return true;
        if (post.author.toLowerCase() === currentUser.username.toLowerCase()) return true;
        if (post.visibility === "friends") {
            // Check cross connected friendship array references safely
            if (me && me.friends && me.friends.some(f => f.toLowerCase() === post.author.toLowerCase())) {
                return true;
            }
        }
        return false;
    });

    if (visiblePosts.length === 0) {
        streamContainer.innerHTML = "<p style='text-align:center; color:#888; margin-top:40px;'>No shared posts found inside the system database yet.</p>";
        return;
    }

    streamContainer.innerHTML = "";
    visiblePosts.forEach(post => {
        const authorObj = localUsers.find(u => u.username.toLowerCase() === post.author.toLowerCase());
        const authorPfp = (authorObj && authorObj.pfp) ? authorObj.pfp : defaultPfp;
        
        const hasLiked = post.likes.some(u => u.toLowerCase() === currentUser.username.toLowerCase());
        const likeBtnClass = hasLiked ? "post-btn liked" : "post-btn";

        const cardElement = document.createElement("div");
        cardElement.className = "post-card";
        
        let mediaTag = "";
        if (post.type === "video") {
            mediaTag = `<video class="post-media-display" src="${post.media}" controls></video>`;
        } else {
            mediaTag = `<img class="post-media-display" src="${post.media}" alt="Post Content">`;
        }

        // Render Comment Strings Elements Block
        let commentsMarkup = "";
        if (post.comments && post.comments.length > 0) {
            post.comments.forEach(c => {
                commentsMarkup += `<div class="comment-item"><b>${c.commenter}:</b> ${c.text}</div>`;
            });
        }

        cardElement.innerHTML = `
            <div class="post-header">
                <div class="post-user-details" onclick="showTargetUserProfile('${post.author}')">
                    <img class="pfp-circle" src="${authorPfp}" alt="pfp">
                    <div>
                        <strong>${post.author}</strong>
                        <div style="font-size:12px; color:#888;">${post.title}</div>
                    </div>
                </div>
                <span style="font-size:12px; color: #94a3b8; text-transform: capitalize;">${post.visibility}</span>
            </div>
            
            ${mediaTag}

            <div class="post-actions">
                <button class="${likeBtnClass}" onclick="toggleLikePost('${post.id}')">
                    ♥ <span>${post.likes ? post.likes.length : 0}</span>
                </button>
            </div>

            <div class="comment-section">
                <div style="margin-bottom:10px; max-height: 120px; overflow-y:auto;">
                    ${commentsMarkup}
                </div>
                <div style="display:flex; gap:8px;">
                    <input id="comment_input_${post.id}" class="input" style="padding:8px 12px; font-size:13px; margin-top:0;" placeholder="Add a comment...">
                    <button class="action-btn-styled" style="padding:8px 14px; font-size:13px;" onclick="submitComment('${post.id}')">Reply</button>
                </div>
            </div>
        `;
        streamContainer.appendChild(cardElement);
    });
}

function toggleLikePost(postId) {
    let localPosts = getPosts();
    const post = localPosts.find(p => p.id === postId);
    if (!post) return;

    if (!post.likes) post.likes = [];

    const myIndex = post.likes.findIndex(u => u.toLowerCase() === currentUser.username.toLowerCase());
    if (myIndex === -1) {
        post.likes.push(currentUser.username);
    } else {
        post.likes.splice(myIndex, 1);
    }

    localStorage.setItem("snapio_posts", JSON.stringify(localPosts));
    recalculateTotalLikesReceived();
    renderFeedStream();
}

function submitComment(postId) {
    const inputElement = document.getElementById(`comment_input_${postId}`);
    if (!inputElement) return;

    const text = inputElement.value.trim();
    if (!text) return;

    let localPosts = getPosts();
    const post = localPosts.find(p => p.id === postId);
    if (!post) return;

    if (!post.comments) post.comments = [];
    post.comments.push({
        commenter: currentUser.username,
        text: text
    });

    localStorage.setItem("snapio_posts", JSON.stringify(localPosts));
    inputElement.value = "";
    renderFeedStream();
}

function recalculateTotalLikesReceived() {
    let localUsers = getUsers();
    let localPosts = getPosts();

    localUsers.forEach(user => {
        let count = 0;
        localPosts.forEach(post => {
            if (post.author.toLowerCase() === user.username.toLowerCase()) {
                if (post.likes) count += post.likes.length;
            }
        });
        user.likesReceived = count;
    });

    localStorage.setItem("snapio_users", JSON.stringify(localUsers));
}


/* =========================================================
   PROFILE VIEW AND CUSTOMIZATION SECTION
   ========================================================= */
function showOwnProfile() {
    recalculateTotalLikesReceived();
    let localUsers = getUsers();
    let localPosts = getPosts();
    
    const me = localUsers.find(u => u.username.toLowerCase() === currentUser.username.toLowerCase());

    const currentPfp = me.pfp || defaultPfp;
    const currentBio = me.bio || "No bio set yet.";

    // Counts calculations
    const myOwnPosts = localPosts.filter(p => p.author.toLowerCase() === currentUser.username.toLowerCase());
    const totalPostsCount = myOwnPosts.length;
    const totalLikesCount = me.likesReceived || 0;
    const totalFollowersCount = me.followers ? me.followers.length : 0;

    contentArea.innerHTML = `
        <div class="page-title">My Profile</div>
        <div class="profile-container">
            <img class="pfp-circle-large" src="${currentPfp}" alt="Profile Picture">
            <h2>${me.username}</h2>
            <p class="bio-text">"${currentBio}"</p>
            
            <div class="stats-row">
                <span>Posts: ${totalPostsCount}</span>
                <span>Likes: ${totalLikesCount}</span>
                <span>Followers: ${totalFollowersCount}</span>
            </div>

            <button class="action-btn-styled" onclick="showCustomizeInterface()">Customize Profile</button>
            
            <h3 style="margin-top: 30px; text-align: left; border-bottom: 1px solid #e2e8f0; padding-bottom:8px;">My Uploaded Media</h3>
            <div class="profile-posts-grid" id="profileGridContainer"></div>
        </div>
    `;

    // Render personal uploads layout grid mapping inside profile cards
    const gridContainer = document.getElementById("profileGridContainer");
    if (myOwnPosts.length === 0) {
        gridContainer.innerHTML = "<p style='color:#888; grid-column: 1/-1; padding:20px;'>You haven't posted any media assets yet.</p>";
    } else {
        myOwnPosts.forEach(post => {
            if (post.type === "video") {
                gridContainer.innerHTML += `<video class="grid-media-item" src="${post.media}" muted preload="metadata"></video>`;
            } else {
                gridContainer.innerHTML += `<img class="grid-media-item" src="${post.media}" alt="Grid Asset">`;
            }
        });
    }
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
    let localPosts = getPosts();
    
    if (updatedName.toLowerCase() !== currentUser.username.toLowerCase()) {
        const nameExists = localUsers.find(u => u.username.toLowerCase() === updatedName.toLowerCase());
        if(nameExists) {
            errorDiv.innerHTML = "This username is already taken!";
            return;
        }

        // Migrate all posts authorship tracking records seamlessly
        localPosts.forEach(p => {
            if (p.author.toLowerCase() === currentUser.username.toLowerCase()) {
                p.author = updatedName;
            }
            if (p.likes) {
                p.likes = p.likes.map(u => u.toLowerCase() === currentUser.username.toLowerCase() ? updatedName : u);
            }
            if (p.comments) {
                p.comments.forEach(c => {
                    if (c.commenter.toLowerCase() === currentUser.username.toLowerCase()) c.commenter = updatedName;
                });
            }
        });

        // Migrate global follower reference fields
        localUsers.forEach(u => {
            if (u.followers) u.followers = u.followers.map(x => x.toLowerCase() === currentUser.username.toLowerCase() ? updatedName : x);
            if (u.following) u.following = u.following.map(x => x.toLowerCase() === currentUser.username.toLowerCase() ? updatedName : x);
            if (u.friends) u.friends = u.friends.map(x => x.toLowerCase() === currentUser.username.toLowerCase() ? updatedName : x);
            if (u.requests) u.requests = u.requests.map(x => x.toLowerCase() === currentUser.username.toLowerCase() ? updatedName : x);
        });

        localStorage.setItem("snapio_posts", JSON.stringify(localPosts));
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


/* =========================================================
   EXTERNAL ACCESSIBLE PROFILES LOOKUP (VISITING OTHER USERS)
   ========================================================= */
function showTargetUserProfile(targetUsername) {
    if (targetUsername.toLowerCase() === currentUser.username.toLowerCase()) {
        showOwnProfile();
        return;
    }

    recalculateTotalLikesReceived();
    let localUsers = getUsers();
    let localPosts = getPosts();

    const user = localUsers.find(u => u.username.toLowerCase() === targetUsername.toLowerCase());
    if(!user) {
        alert("Could not load user profile properly.");
        return;
    }

    if (!user.followers) user.followers = [];
    
    const me = localUsers.find(u => u.username.toLowerCase() === currentUser.username.toLowerCase());
    const isFollowing = user.followers.some(x => x.toLowerCase() === currentUser.username.toLowerCase());

    const followBtnText = isFollowing ? "Unfollow" : "Follow User";
    const followBtnColor = isFollowing ? "#ef4444" : "#2563eb";

    const targetUserPosts = localPosts.filter(p => {
        if (p.author.toLowerCase() !== user.username.toLowerCase()) return false;
        if (p.visibility === "public") return true;
        if (p.visibility === "friends" && me && me.friends && me.friends.some(f => f.toLowerCase() === user.username.toLowerCase())) {
            return true;
        }
        return false;
    });

    contentArea.innerHTML = `
        <div class="page-title">${user.username}'s Profile</div>
        <div class="profile-container">
            <img class="pfp-circle-large" src="${user.pfp || defaultPfp}" alt="Profile Image">
            <h2>${user.username}</h2>
            <p class="bio-text">"${user.bio || 'No status bio set yet.'}"</p>
            
            <div class="stats-row">
                <span>Posts: ${targetUserPosts.length}</span>
                <span>Likes: ${user.likesReceived || 0}</span>
                <span>Followers: ${user.followers.length}</span>
            </div>

            <div style="display:flex; gap:10px; justify-content:center; margin-bottom:25px;">
                <button class="action-btn-styled" style="background:${followBtnColor};" onclick="toggleFollowUser('${user.username}')">${followBtnText}</button>
                <button class="action-btn-styled" style="background:#4b5563;" onclick="showForYouPage()">Back to Feed</button>
            </div>

            <h3 style="margin-top: 30px; text-align: left; border-bottom: 1px solid #e2e8f0; padding-bottom:8px;">Shared Media</h3>
            <div class="profile-posts-grid" id="targetProfileGridContainer"></div>
        </div>
    `;

    const targetGrid = document.getElementById("targetProfileGridContainer");
    if (targetUserPosts.length === 0) {
        targetGrid.innerHTML = "<p style='color:#888; grid-column: 1/-1; padding:20px;'>No visible shared media entries found.</p>";
    } else {
        targetUserPosts.forEach(post => {
            if (post.type === "video") {
                targetGrid.innerHTML += `<video class="grid-media-item" src="${post.media}" muted preload="metadata"></video>`;
            } else {
                targetGrid.innerHTML += `<img class="grid-media-item" src="${post.media}" alt="Grid Asset">`;
            }
        });
    }
}

function toggleFollowUser(targetUsername) {
    let localUsers = getUsers();
    
    const targetUser = localUsers.find(u => u.username.toLowerCase() === targetUsername.toLowerCase());
    const me = localUsers.find(u => u.username.toLowerCase() === currentUser.username.toLowerCase());

    if (!targetUser || !me) return;

    if (!targetUser.followers) targetUser.followers = [];
    if (!me.following) me.following = [];

    const followerIndex = targetUser.followers.findIndex(x => x.toLowerCase() === currentUser.username.toLowerCase());

    if (followerIndex === -1) {
        targetUser.followers.push(me.username);
        me.following.push(targetUser.username);
    } else {
        targetUser.followers.splice(followerIndex, 1);
        me.following = me.following.filter(x => x.toLowerCase() !== targetUser.username.toLowerCase());
    }

    localStorage.setItem("snapio_users", JSON.stringify(localUsers));
    showTargetUserProfile(targetUser.username);
}
</script>

</body>
</html>
