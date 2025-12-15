# ChemFind: AI Agent-based for Novel Chemical Discovery

Projek ini adalah *web application* untuk pencarian dan eksplorasi senyawa kimia baru berbasis Large Language Model (LLM) dan Agentic AI. Melalui ChemFind, proses pencarian senyawa dilakukan dengan generasi SMILES berdasarkan kriteria yang ditentukan pengguna, meliputi pIC50, jumlah atom, dan logP.

Dataset yang digunakan adalah “SMILES DataSet for Analysis & Prediction Dataset” oleh Yan Maksi, didapat dan diakses pada platform Kaggle melalui url berikut: [SMILES DataSet for Analysis & Prediction Dataset](https://www.kaggle.com/datasets/yanmaksi/big-molecules-smiles-dataset)

Untuk Link Google Drive model ML yang dibangun, dapat diakses melalui url berikut: [Drive Model ML](https://drive.google.com/drive/folders/1nSy71N53NAd53wnLZAZOYg9GILsRPy73?usp=sharing)

## Petunjuk Environment Setup
Daftar dependensi dan konfigurasi *environment* dapat dilihat pada file `requirements.txt`.

## Cara Menjalankan Aplikasi
### API Configuration (Windows)
1. Masukkan Gemini API Key ke CMD VS Code dengan prompt berikut.
```
setx GOOGLE_API_KEY "API_KEY_ANDA”
```
2. Setelah perintah dijalankan, tutup terminal VS Code dan tutup aplikasi VS Code agar perubahan environment variable tersimpan dengan benar.
3. Buka Command Prompt (CMD) biasa di Windows, kemudian jalankan perintah:
```
# Pada CMD Windows
echo %GOOGLE_API_KEY%
```
Perintah ini digunakan untuk mengecek apakah API Key telah berhasil disimpan.
> Jika API Key muncul, berarti konfigurasi berhasil dan API siap digunakan.
> Jika tidak muncul, berarti API Key belum tersimpan dengan benar dan perlu dikonfigurasi ulang.
4. Setelah itu, buka kembali VS Code, lalu jalankan perintah yang sama pada terminal:
```
echo %GOOGLE_API_KEY%
```

### Menjalankan Aplikasi (Localhost) 
#### Aktifkan Conda Environment
Buka terminal baru dan jalankan:
```
conda activate chemAPPChapter2
```
#### Jalankan Backend
```
cd backend
uvicorn main:app --reload
```
#### Jalankan Frontend
Buka terminal baru dan jalankan:
```
npm run dev
```

## Load Model Machine Learning
Model machine learning yang digunakan pada proyek ini adalah multi-target regressor yang dilatih menggunakan MultiOutputRegressor dengan Ridge Regression sebagai base model. Model hasil pelatihan disimpan dalam file ```multitarget_model.pkl```
