<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>カスタムダイアログテストサイト</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50px;
        }
        button {
            padding: 10px 20px;
            font-size: 16px;
            margin: 10px;
            cursor: pointer;
        }

        /* カスタムダイアログのスタイル */
        .custom-dialog-overlay {
            display: none; /* 初期状態では非表示 */
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5); /* 半透明の背景 */
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }

        .custom-dialog-content {
            background-color: white;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            text-align: center;
            min-width: 300px;
        }

        .custom-dialog-content h2 {
            margin-top: 0;
            color: #333;
        }

        .custom-dialog-content p {
            margin-bottom: 20px;
            color: #555;
        }

        .custom-dialog-content .dialog-buttons button {
            background-color: #007bff;
            color: white;
            border: none;
            padding: 8px 15px;
            border-radius: 5px;
            cursor: pointer;
            margin: 0 5px;
            font-size: 14px;
        }

        .custom-dialog-content .dialog-buttons button:hover {
            opacity: 0.9;
        }

        .custom-dialog-content .dialog-buttons button.cancel {
            background-color: #6c757d;
        }

        .custom-dialog-content input[type="text"] {
            width: calc(100% - 20px);
            padding: 8px;
            margin-bottom: 15px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
    </style>
</head>
<body>
    <h1>カスタムダイアログのテスト</h1>

    <button onclick="showCustomAlert()">カスタムアラートを表示</button>
    <button onclick="showCustomConfirm()">カスタム確認ダイアログを表示</button>
    <button onclick="showCustomPrompt()">カスタムプロンプトを表示</button>

    <p id="result"></p>

    <div id="customAlertDialog" class="custom-dialog-overlay">
        <div class="custom-dialog-content">
            <h2>カスタムアラート</h2>
            <p>これはXPathで操作できるカスタムアラートです。</p>
            <div class="dialog-buttons">
                <button onclick="closeCustomAlertDialog()" id="customAlertOkButton">OK</button>
            </div>
        </div>
    </div>

    <div id="customConfirmDialog" class="custom-dialog-overlay">
        <div class="custom-dialog-content">
            <h2>カスタム確認</h2>
            <p>この操作を実行しますか？</p>
            <div class="dialog-buttons">
                <button onclick="confirmCustomDialog(true)" id="customConfirmOkButton">はい</button>
                <button onclick="confirmCustomDialog(false)" id="customConfirmCancelButton" class="cancel">いいえ</button>
            </div>
        </div>
    </div>

    <div id="customPromptDialog" class="custom-dialog-overlay">
        <div class="custom-dialog-content">
            <h2>カスタムプロンプト</h2>
            <p>お名前を入力してください:</p>
            <input type="text" id="customPromptInput" placeholder="お名前">
            <div class="dialog-buttons">
                <button onclick="promptCustomDialog(true)" id="customPromptOkButton">OK</button>
                <button onclick="promptCustomDialog(false)" id="customPromptCancelButton" class="cancel">キャンセル</button>
            </div>
        </div>
    </div>

    <script>
        // カスタムアラート
        function showCustomAlert() {
            document.getElementById('customAlertDialog').style.display = 'flex'; // flexで中央寄せ
        }

        function closeCustomAlertDialog() {
            document.getElementById('customAlertDialog').style.display = 'none';
        }

        // カスタム確認ダイアログ
        function showCustomConfirm() {
            document.getElementById('customConfirmDialog').style.display = 'flex';
        }

        function confirmCustomDialog(isConfirmed) {
            document.getElementById("result").innerText = "カスタム確認ダイアログの結果: " + (isConfirmed ? "はい" : "いいえ");
            document.getElementById('customConfirmDialog').style.display = 'none';
        }

        // カスタムプロンプトダイアログ
        function showCustomPrompt() {
            document.getElementById('customPromptDialog').style.display = 'flex';
            document.getElementById('customPromptInput').value = ''; // 入力欄をクリア
        }

        function promptCustomDialog(isConfirmed) {
            const inputElement = document.getElementById('customPromptInput');
            if (isConfirmed) {
                const name = inputElement.value;
                document.getElementById("result").innerText = "カスタムプロンプトダイアログの結果: " + (name === "" ? "何も入力されませんでした" : name + "さんと入力されました");
            } else {
                document.getElementById("result").innerText = "カスタムプロンプトダイアログの結果: キャンセルされました";
            }
            document.getElementById('customPromptDialog').style.display = 'none';
        }
    </script>
</body>
</html>
