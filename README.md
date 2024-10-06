const sourceText = document.getElementById('source-text');
const sourceLang = document.getElementById('source-lang');
const targetLang = document.getElementById('target-lang');
const translateBtn = document.getElementById('translate-btn');
const targetText = document.getElementById('target-text');

// Google Translate API key
const apiKey = 'YOUR_API_KEY';

// Function to populate language options
function populateLanguages() {
  const languages = ['en', 'fr', 'es', 'de']; // Add more languages as needed
  languages.forEach(lang => {
    const option = document.createElement('option');
    option.value = lang;
    option.text = lang;
    sourceLang.appendChild(option.cloneNode(true));
    targetLang.appendChild(option);
  });
}

// Function to translate text
function translateText() {
  const textToTranslate = sourceText.value;
  const sourceLanguage = sourceLang.value;
  const targetLanguage = targetLang.value;

  const url = `https://api.example.com/translate?key=${apiKey}&text=${textToTranslate}&source=${sourceLanguage}&target=${targetLanguage}`;

  fetch(url)
    .then(response => response.json())
    .then(data => {
      targetText.value = data.translatedText;
    })
    .catch(error => {
      console.error('Error:', error);
    });
}

// Initialize the translator
populateLanguages();
translateBtn.addEventListener('click', translateText);
