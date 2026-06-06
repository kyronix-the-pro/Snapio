<!DOCTYPE html>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SNAPIO</title>

```
<style>
    *{
        margin:0;
        padding:0;
        box-sizing:border-box;
        font-family:Arial, Helvetica, sans-serif;
    }

    body{
        height:100vh;
        display:flex;
        justify-content:center;
        align-items:center;
        background:linear-gradient(135deg,#0f172a,#1e293b);
    }

    .container{
        text-align:center;
        background:white;
        padding:60px;
        border-radius:20px;
        box-shadow:0 10px 30px rgba(0,0,0,0.25);
        width:420px;
    }

    h1{
        font-size:4rem;
        color:#111827;
        margin-bottom:15px;
        letter-spacing:3px;
    }

    p{
        color:#6b7280;
        margin-bottom:35px;
    }

    .btn{
        width:100%;
        padding:15px;
        border:none;
        border-radius:12px;
        cursor:pointer;
        font-size:1rem;
        font-weight:bold;
        transition:0.2s;
        margin-bottom:15px;
    }

    .create-btn{
        background:#2563eb;
        color:white;
    }

    .create-btn:hover{
        background:#1d4ed8;
        transform:translateY(-2px);
    }

    .login-btn{
        background:#111827;
        color:white;
    }

    .login-btn:hover{
        background:#000;
        transform:translateY(-2px);
    }
</style>
```

</head>
<body>

```
<div class="container">
    <h1>SNAPIO</h1>
    <p>Connect with friends and share moments.</p>

    <button class="btn create-btn"
        onclick="window.location.href='register.html'">
        Create Account
    </button>

    <button class="btn login-btn"
        onclick="window.location.href='login.html'">
        Sign In
    </button>
</div>
```

</body>
</html>

