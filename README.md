<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>アラートテストサイト</title>
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
    </style>
</head>
<body>
    <h1>アラート・確認・プロンプトダイアログのテスト</h1>

    <button onclick="showAlert()">アラートを表示</button>
    <button onclick="showConfirm()">確認ダイアログを表示</button>
    <button onclick="showPrompt()">プロンプトを表示</button>

    <p id="result"></p>

    <script>
        function showAlert() {
            alert("これはRPAテスト用のアラートです！");
        }

        function showConfirm() {
            const result = confirm("この操作を実行しますか？");
            document.getElementById("result").innerText = "確認ダイアログの結果: " + (result ? "はい" : "いいえ");
        }

        function showPrompt() {
            const name = prompt("お名前を入力してください:");
            if (name !== null) {
                document.getElementById("result").innerText = "プロンプトダイアログの結果: " + (name === "" ? "何も入力されませんでした" : name + "さんと入力されました");
            } else {
                document.getElementById("result").innerText = "プロンプトダイアログの結果: キャンセルされました";
            }
        }
    </script>
</body>
</html>
