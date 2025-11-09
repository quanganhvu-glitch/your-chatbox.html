<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Chatbot Hóa học</title>

<style>
    body {
        margin: 0;
        padding: 0;
        font-family: Arial, sans-serif;
        background: var(--bg);
        color: var(--text);
        transition: 0.3s;
    }

    :root {
        --bg: #111;
        --text: #fff;
        --card: #1c1c1c;
    }

    .light {
        --bg: #fff;
        --text: #000;
        --card: #f2f2f2;
    }

    #chat-container {
        width: 100%;
        max-width: 1100px;
        margin: auto;
        padding-top: 20px;
    }

    /* Khung chat */
    #chat-box {
        width: 100%;
        height: 650px;
        border-radius: 16px;
        overflow: hidden;
        background: var(--card);
        position: relative;
        box-shadow: 0px 0px 15px rgba(0,0,0,0.4);
        transition: 0.3s;
    }

    /* Thu nhỏ */
    #chat-box.small {
        height: 70px;
    }

    #toggle-btn, #theme-btn {
        position: absolute;
        z-index: 99;
        border: none;
        padding: 8px 12px;
        border-radius: 6px;
        cursor: pointer;
        background: #333;
        color: white;
        font-size: 14px;
    }

    #toggle-btn { top: 10px; right: 10px; }
    #theme-btn { top: 10px; left: 10px; }

    #description {
        text-align: center;
        margin-bottom: 10px;
        font-size: 15px;
        opacity: 0.8;
        padding: 0 10px;
    }
</style>

</head>

<body class="dark">
<div id="chat-container">

    <div id="description">
        <b>Một kỹ sư hóa học trẻ, nhiệt huyết</b>, tốt nghiệp từ một trường đại học danh tiếng trong nước.  
        Là người yêu thích giáo dục, mong muốn truyền cảm hứng cho thế hệ trẻ về vẻ đẹp của hóa học  
        và giá trị của tài nguyên thiên nhiên quê hương.
    </div>

    <div id="chat-box">
        <button id="toggle-btn">Thu nhỏ</button>
        <button id="theme-btn">Light mode</button>
        <div id="coze-chat-container" style="width:100%; height:100%;"></div>
    </div>
</div>

<script src="https://sf-cdn.coze.com/obj/unpkg-va/flow-platform/chat-app-sdk/1.2.0-beta.6/libs/oversea/index.js"></script>

<script>

    // ✅ Khởi tạo chatbot
    new CozeWebSDK.WebChatClient({
        config: {
            bot_id: "7570019252804190209"
        },
        componentProps: {
            title: "Chatbot Hóa học"
        },
        auth: {
            type: "token",
            token: "pat_Ckv0mIayDnqK72MOlxTw6YZTyphhpxLdJMmOKDi6U5pUwhtzPTBdUAr0hCbpz8Hl",
            onRefreshToken: () =>
                "pat_Ckv0mIayDnqK72MOlxTw6YZTyphhpxLdJMmOKDi6U5pUwhtzPTBdUAr0hCbpz8Hl",
        },
    });

    // ✅ Nút thu nhỏ / mở rộng
    const chatBox = document.getElementById("chat-box");
    const toggleBtn = document.getElementById("toggle-btn");

    toggleBtn.onclick = () => {
        chatBox.classList.toggle("small");
        toggleBtn.textContent = chatBox.classList.contains("small")
            ? "Mở rộng"
            : "Thu nhỏ";
    };

    // ✅ Light / Dark mode
    const themeBtn = document.getElementById("theme-btn");
    const body = document.body;

    themeBtn.onclick = () => {
        const light = body.classList.toggle("light");
        themeBtn.textContent = light ? "Dark mode" : "Light mode";
    };

</script>

</body>
</html>
