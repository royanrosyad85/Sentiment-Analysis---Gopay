# Analisis Sentiment Ulasan Aplikasi GoPay

Proyek ini merupakan implementasi analisis sentimen untuk menganalisis ulasan pengguna aplikasi GoPay menggunakan teknik Natural Language Processing (NLP) dan Machine Learning. Dataset berisi 40.000 ulasan pengguna yang diklasifikasikan menjadi sentimen positif, negatif, dan netral.

## 📋 Deskripsi Proyek

Proyek ini bertujuan untuk:
- Menganalisis sentimen ulasan pengguna aplikasi GoPay dari Google Play Store
- Melakukan preprocessing teks bahasa Indonesia yang komprehensif
- Implementasi sistem pelabelan otomatis menggunakan lexicon-based approach
- Visualisasi hasil analisis dengan word clouds dan distribusi sentimen
- Memahami persepsi pengguna terhadap aplikasi GoPay

## 🗂️ Struktur Proyek

```
.
├── README.md                           # Dokumentasi proyek
├── requirements.txt                    # Dependencies Python
├── notebook_scrapper.ipynb            # Notebook scraping data
├── notebook_model_nayor.ipynb         # Notebook analisis sentimen utama
└── ulasan_aplikasi_gopay_40K(2).csv  # Dataset ulasan (40.000 records)
```

## 🔧 Requirements & Dependencies

### Library Utama
- **Data Processing**: `pandas`, `numpy`, `requests`
- **Text Processing**: `nltk`, `Sastrawi`, `re`
- **Visualization**: `matplotlib`, `seaborn`, `wordcloud`
- **Machine Learning**: `scikit-learn`, `tensorflow`, `keras`
- **Web Scraping**: `google-play-scraper`

### Instalasi Dependencies
```bash
pip install -r requirements.txt
```

## 📊 Dataset

### Sumber Data
- **Source**: Google Play Store - Aplikasi GoPay
- **Package ID**: `com.gojek.gopay`
- **Jumlah Review**: 40.000 ulasan
- **Bahasa**: Indonesia
- **Periode**: Data terbaru dari Google Play Store

### Struktur Dataset
| Column | Description |
|--------|-------------|
| `reviewId` | ID unik untuk setiap review |
| `userName` | Nama pengguna reviewer |
| `userImage` | URL gambar profil pengguna |
| `content` | Isi ulasan/review |
| `score` | Rating bintang (1-5) |
| `thumbsUpCount` | Jumlah like pada review |
| `reviewCreatedVersion` | Versi aplikasi saat review dibuat |
| `at` | Timestamp review |
| `replyContent` | Balasan dari developer |
| `repliedAt` | Timestamp balasan developer |
| `appVersion` | Versi aplikasi |

## 🔄 Preprocessing Pipeline

### 1. Data Cleaning
- Penghapusan kolom yang tidak relevan
- Eliminasi data duplikat
- Handling missing values

### 2. Text Preprocessing
```python
def cleaningText(text):
    # Remove mentions (@username)
    # Remove hashtags (#hashtag)
    # Remove URLs
    # Remove special characters & numbers
    # Remove extra whitespaces
```

### 3. Text Normalization
- **Case Folding**: Konversi ke huruf kecil
- **Slang Words Correction**: Normalisasi kata-kata slang/gaul
- **Emoji Removal**: Penghapusan emoji dan emoticon
- **Tokenization**: Pemisahan kata
- **Stopwords Removal**: Penghapusan kata-kata umum bahasa Indonesia
- **Text Stemming**: Menggunakan Sastrawi stemmer

## 🏷️ Sentiment Labeling

### Lexicon-Based Approach
Sistem pelabelan menggunakan kamus sentimen bahasa Indonesia:

- **Positive Lexicon**: Dataset kata-kata positif dengan bobot
- **Negative Lexicon**: Dataset kata-kata negatif dengan bobot
- **Source**: Repository lexicon Indonesia dari GitHub

### Klasifikasi Sentimen
```python
def sentiment_analysis_lexicon_indonesia(text):
    # Menghitung skor sentimen berdasarkan lexicon
    # Positive score > 0: Positive sentiment
    # Negative score < 0: Negative sentiment  
    # Score = 0: Neutral sentiment
```

### Distribusi Hasil Labeling
- **Positive**: 16.995 ulasan (42.5%)
- **Negative**: 16.653 ulasan (41.6%)
- **Neutral**: 6.352 ulasan (15.9%)

## 📈 Visualisasi & Analisis

### Word Cloud Analysis
- **General Word Cloud**: Kata-kata paling umum dalam semua ulasan
- **Positive Word Cloud**: Kata-kata yang dominan dalam ulasan positif
- **Negative Word Cloud**: Kata-kata yang dominan dalam ulasan negatif
- **Neutral Word Cloud**: Kata-kata yang dominan dalam ulasan netral

### Insight Utama
- Kata-kata terkait masalah teknis sering muncul dalam ulasan negatif
- Ulasan positif fokus pada kemudahan penggunaan dan fitur
- Isu top-up dan transfer merupakan concern utama pengguna

## 🚀 Cara Menjalankan

### 1. Clone Repository
```bash
git clone <repository-url>
cd Analisis-Sentiment-Gopay
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Download NLTK Data
```python
import nltk
nltk.download('punkt')
nltk.download('stopwords')
```

### 4. Jalankan Notebook
- **Data Scraping**: Buka `notebook_scrapper.ipynb`
- **Analisis Sentimen**: Buka `notebook_model_nayor.ipynb`

## 📁 File Descriptions

### `notebook_scrapper.ipynb`
Notebook untuk scraping data ulasan dari Google Play Store menggunakan `google-play-scraper` library.

**Fitur utama**:
- Scraping 40.000 ulasan terbaru
- Export ke format CSV
- Konfigurasi parameter scraping

### `notebook_model_nayor.ipynb`
Notebook utama untuk analisis sentimen yang mencakup:

**Sections**:
1. **Data Loading & Exploration**
2. **Data Preprocessing**
   - Text cleaning
   - Normalization
   - Tokenization
   - Stopword removal
3. **Sentiment Labeling**
   - Lexicon-based sentiment analysis
   - Label assignment
4. **Data Understanding**
   - Distribusi sentimen
   - Statistik deskriptif
5. **Visualization**
   - Word clouds
   - Sentiment distribution plots

## 🔍 Metodologi

### Lexicon-Based Sentiment Analysis
Proyek ini menggunakan pendekatan lexicon-based untuk analisis sentimen:

1. **Lexicon Loading**: Memuat kamus sentimen positif dan negatif
2. **Score Calculation**: Menghitung skor sentimen untuk setiap teks
3. **Classification**: Klasifikasi berdasarkan threshold skor

### Keunggulan Pendekatan
- ✅ Tidak memerlukan data training berlabel
- ✅ Interpretable dan explainable
- ✅ Cocok untuk bahasa Indonesia
- ✅ Fast processing

### Limitasi
- ⚠️ Dependent pada kualitas lexicon
- ⚠️ Tidak capture context yang kompleks
- ⚠️ Kurang akurat untuk sarcasm/irony

## 📊 Hasil & Temuan

### Distribusi Sentimen
```
Positive: 42.5% (16,995 ulasan)
Negative: 41.6% (16,653 ulasan)  
Neutral:  15.9% (6,352 ulasan)
```

### Key Insights
1. **Balanced Distribution**: Sentimen positif dan negatif hampir berimbang
2. **Technical Issues**: Masalah teknis menjadi keluhan utama
3. **User Experience**: Kemudahan penggunaan diapresiasi pengguna
4. **Payment Issues**: Top-up dan transfer menjadi pain point utama

## 🔮 Future Improvements

### Machine Learning Models
- Implementasi algoritma supervised learning (Naive Bayes, SVM, Random Forest)
- Deep learning dengan LSTM/BERT untuk better context understanding
- Model ensemble untuk improved accuracy

### Advanced Text Processing
- Named Entity Recognition (NER)
- Aspect-based sentiment analysis
- Emotion detection beyond positive/negative/neutral

### Enhanced Visualization
- Interactive dashboards
- Temporal sentiment analysis
- Topic modeling dengan LDA

## 🤝 Contributing

Kontribusi sangat diterima! Silakan:

1. Fork repository
2. Create feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

Distributed under the MIT License. See `LICENSE` for more information.

## 🙏 Acknowledgments

- [Sastrawi](https://github.com/har07/Sastrawi) untuk stemming bahasa Indonesia
- [Google Play Scraper](https://pypi.org/project/google-play-scraper/) untuk data collection
- [NLTK](https://nltk.org/) untuk text processing utilities
- Lexicon dataset dari komunitas NLP Indonesia


**Note**: Proyek ini dibuat untuk tujuan edukasi dan penelitian dalam bidang Natural Language Processing dan Sentiment Analysis.
