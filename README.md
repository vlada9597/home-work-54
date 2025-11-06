# 🧩 Homework #53-54 — Basic Buffer Operations in Node.js 

## 📘 Тема
**Базові операції з буфером у Node.js: перетворення між Base64 та Hex**

---

## 🧠 Зміст

### 1️⃣ `isDebugMode()`
Функція визначає, чи запущено додаток у режимі розробки.

- Читає значення `process.env.NODE_ENV`.
- Повертає `true`, якщо середовище = `'development'`.
- Повертає `false` у будь-якому іншому випадку.
- Логує поточне значення середовища і результат перевірки.

js
const isDebugMode = () => {
  const env = process.env.NODE_ENV;
  const debug = env === 'development';
  console.log(`[isDebugMode] NODE_ENV = ${env}`);
  console.log(`[isDebugMode] Debug mode: ${debug}`);
  return debug;
};

2️⃣ Кодування та декодування рядків
🔹 encodeToBase64(...args)
Об’єднує всі аргументи через : і перетворює у Base64.

🔹 encodeToHex(...args)
Об’єднує всі аргументи через : і перетворює у Hex.

🔹 decodeFromBase64(base64String)
Перетворює рядок із Base64 у звичайний текст.

🔹 decodeFromHex(hexString)
Перетворює рядок із Hex у звичайний текст.

js

const base64 = encodeToBase64('john@email.com', '123', 'extraData');
console.log('Base64:', base64);

const decoded = decodeFromBase64(base64);
console.log('Decoded:', decoded);

3️⃣ Безпечне декодування
🔹 safeDecodeFromBase64(base64String)
Перевіряє валідність base64-рядка перед декодуванням.
Якщо формат невірний — повертає null і виводить помилку.

🔹 safeDecodeFromHex(hexString)
Аналогічна функція для Hex-рядків.

js

const safeDecoded = safeDecodeFromBase64('am9obkBlbWFpbC5jb206MTIzOmV4dHJhRGF0YQ==');
console.log('Safe Base64 Decoded:', safeDecoded);

⚙️ Використані технології
Node.js Buffer API

ES6+ (стрілкові функції, rest-параметри)

Регулярні вирази для валідації форматів

Обробка помилок через try/catch

🧪 Приклад виконання

NODE_ENV=development
Debug mode: true

Base64 Encoded: am9obkBlbWFpbC5jb206MTIzOmV4dHJhRGF0YQ==
Base64 Decoded: john@email.com:123:extraData

Hex Encoded: 6a6f686e40656d61696c2e636f6d3a3132333a657874726144617461
Hex Decoded: john@email.com:123:extraData .....
