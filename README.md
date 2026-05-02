📊 CSV UTF-8 Encoding Fixer

A simple and practical project to detect, fix, and standardize CSV file encodings for reliable data processing, NLP, and machine learning workflows.

🚀 Problem

Many CSV files are not encoded in UTF-8.
This causes issues like:

❌ UnicodeDecodeError
❌ Broken characters (??, �)
❌ Lost emojis and multilingual text
❌ Poor NLP model performance

Example error:

UnicodeDecodeError: 'utf-8' codec can't decode byte 0xe9...
🎯 Solution

This project:

Detects file encoding automatically
Reads CSV files safely
Converts them into UTF-8 format
Cleans corrupted text
🛠️ Tech Stack
Python 🐍
Pandas
Chardet (encoding detection)
📂 Project Structure
.
├── data/
│   ├── raw.csv
│   └── clean_utf8.csv
├── src/
│   └── encoding_fixer.py
├── README.md
⚙️ Installation
pip install pandas chardet
💡 Usage
1. Detect Encoding
import chardet

with open("data/raw.csv", "rb") as f:
    result = chardet.detect(f.read())

print(result)
2. Read File Safely
import pandas as pd

df = pd.read_csv("data/raw.csv", encoding="latin1")
3. Convert to UTF-8
df.to_csv("data/clean_utf8.csv", encoding="utf-8-sig", index=False)
4. Clean Corrupted Text
df = df.applymap(lambda x: x.encode("utf-8", "ignore").decode("utf-8") if isinstance(x, str) else x)
📌 Example
Before	After
Délicieux! J'ai adoré	Délicieux! J'ai adoré
??	(removed or cleaned)
⚠️ Limitations
❌ Lost characters (like emojis replaced with ??) cannot be recovered
⚠️ Detection may not be 100% accurate for mixed encodings
🧠 Why This Matters

For projects like:

NLP applications
Resume analyzers
Chatbots

Bad encoding can lead to:

Incorrect text processing
Poor model accuracy
Data corruption
🔮 Future Improvements
Web-based file upload tool
Automatic cleaning pipeline
Multilingual dataset support (Sinhala 🇱🇰, Tamil, English)
🤝 Contributing

Pull requests are welcome!
Feel free to improve encoding detection or cleaning methods.

📄 License

MIT License

✨ Author

Dimalsha Kinkini
Undergraduate Data Science Student
