<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Lurathi Alfabesi Çevirici</title>
<style>
    body { font-family: Arial, sans-serif; margin: 20px; background: #121212; color: #eee; }
    h1 { color: #56b6c2; }
    textarea { width: 100%; height: 120px; font-size: 18px; padding: 10px; border-radius: 8px; border: none; resize: vertical; background: #222; color: #eee; }
    #output { margin-top: 20px; background: #222; padding: 15px; border-radius: 8px; min-height: 100px; font-size: 18px; white-space: pre-wrap; word-wrap: break-word; }
    label { font-weight: bold; font-size: 16px; }
    footer { margin-top: 30px; font-size: 14px; color: #666; text-align: center; }
</style>
</head>
<body>
<h1>Lurathi Alfabesi Çevirici</h1>
<label for="inputText">Metni buraya yaz:</label>
<textarea id="inputText" placeholder="Buraya normal metni yaz..."></textarea>
<div id="output"></div>
<footer>© 2025 Lurathi Alfabesi by Schawez</footer>

<script>
const alphabetMap = {
    "a": "ah", "b": "buh", "c": "seh", "d": "duh", "e": "eh", "f": "fuh", "g": "guh", "h": "huh",
    "i": "ih", "j": "juh", "k": "kuh", "l": "luh", "m": "muh", "n": "nuh", "o": "oh", "p": "puh",
    "q": "quh", "r": "ruh", "s": "suh", "t": "tuh", "u": "uh", "v": "vuh", "w": "wuh", "x": "xuh",
    "y": "yuh", "z": "zuh"
};

const inputText = document.getElementById('inputText');
const outputDiv = document.getElementById('output');

function convertToLurathi(text) {
    text = text.toLowerCase();
    let result = '';
    for (let ch of text) {
        if (alphabetMap[ch]) {
            result += alphabetMap[ch];
        } else {
            result += ch; // harf değilse aynen bırak (boşluk, noktalama, rakam vs.)
        }
    }
    return result;
}

inputText.addEventListener('input', () => {
    outputDiv.textContent = convertToLurathi(inputText.value);
});
</script>

</body>
</html>
