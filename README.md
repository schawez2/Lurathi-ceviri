<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Lurathi Çeviri Aracı</title>
<style>
  body { font-family: Arial, sans-serif; max-width: 400px; margin: auto; padding: 1rem; }
  input, textarea, button { width: 100%; margin: 0.5rem 0; padding: 0.5rem; font-size: 1rem; }
  button { cursor: pointer; }
</style>
</head>
<body>

<h2>Lurathi - Türkçe Çeviri Aracı</h2>

<label>Türkçe → Lurathi</label>
<input type="text" id="turkce" placeholder="Türkçe kelime yaz..." />

<label>Lurathi → Türkçe</label>
<input type="text" id="lurathi" placeholder="Lurathi kodu yaz..." />

<button onclick="turkceToLurathi()">Türkçe'yi Lurathi'ye Çevir</button>
<button onclick="lurathiToTurkce()">Lurathi'yi Türkçe'ye Çevir</button>

<h3>Sonuç:</h3>
<textarea id="sonuc" rows="4" readonly></textarea>

<script>
  const alphabet = {
    'A': 'ah', 'B': 'buh', 'C': 'seh', 'D': 'duh', 'E': 'eh', 'F': 'fuh', 'G': 'guh',
    'H': 'huh', 'I': 'ih', 'J': 'juh', 'K': 'kuh', 'L': 'luh', 'M': 'muh', 'N': 'nuh',
    'O': 'oh', 'P': 'puh', 'Q': 'quh', 'R': 'ruh', 'S': 'suh', 'T': 'tuh', 'U': 'uh',
    'V': 'vuh', 'W': 'wuh', 'X': 'xuh', 'Y': 'yuh', 'Z': 'zuh'
  };

  function turkceToLurathi() {
    let input = document.getElementById('turkce').value.toUpperCase();
    let result = '';
    for(let ch of input) {
      if(alphabet[ch]) {
        result += alphabet[ch] + ' ';
      } else {
        result += ch + ' '; // boşluk, noktalama vs
      }
    }
    document.getElementById('sonuc').value = result.trim();
  }

  function lurathiToTurkce() {
    let input = document.getElementById('lurathi').value.trim().toLowerCase();
    let result = '';
    // Alfabenin tersini oluştur
    let reverseAlphabet = {};
    for(let key in alphabet) {
      reverseAlphabet[alphabet[key]] = key;
    }

    // input'u kelimelere böl
    let parts = input.split(/\s+/);
    for(let p of parts) {
      if(reverseAlphabet[p]) {
        result += reverseAlphabet[p];
      } else {
        result += '?'; // bilinmeyen kod
      }
    }
    document.getElementById('sonuc').value = result;
  }
</script>

</body>
</html>
