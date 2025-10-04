# 🫀 Yurak-qon tomir kasalliklarini EKG signallar asosida aniqlash (MIT-BIH Arrhythmia)

## 📘 Loyiha haqida

Ushbu loyiha MIT-BIH Arrhythmia ma’lumotlar bazasidan olingan **EKG (elektrokardiogramma)** signallarini qayta ishlash va yurakdagi aritmiyalarni (noto‘g‘ri urishlar) aniqlashga bag‘ishlangan.

Loyihada **signalni filtrlash**, **R-piklarni aniqlash (Pan–Tompkins yondashuvi)**, **xususiyatlarni ajratish (feature extraction)** va **mashina o‘rganish asosida tasniflash** bosqichlari amalga oshiriladi.  
Bu EKG tahlilining amaliy qo‘llanmasi bo‘lib, Python va mashina o‘rganish kutubxonalari yordamida yurak ritmidagi buzilishlarni aniqlaydi.

---

## 🎯 Maqsad

- MIT-BIH Arrhythmia ma’lumotlar bazasidan EKG signalini tahlil qilish  
- Yurak urishlaridagi **R-piklarni** aniqlash  
- **HR (Heart Rate)** va **HRV (Heart Rate Variability)** ni hisoblash  
- Aritmiyalarni (Normal / Pathological) **mashina o‘rganish** orqali tasniflash  
- Sog‘lom va patologik yurak urishlarini farqlovchi **model yaratish**

---

## ⚙️ Foydalanilgan texnologiyalar

| Texnologiya / Kutubxona | Vazifasi |
|--------------------------|----------|
| `wfdb` | MIT-BIH ma’lumotlarini yuklash va annotatsiyalarni o‘qish |
| `neurokit2` | EKG signalining to‘lqinlarini (P, QRS, T) aniqlash |
| `numpy`, `scipy` | Signal tahlili va matematik amallar |
| `matplotlib` | EKG signalini vizualizatsiya qilish |
| `scikit-learn` | Tasniflash modeli (Random Forest) |
| `tensorflow / keras` | (ixtiyoriy) Chuqur o‘rganish modeli qurish |

---

## 🧩 Loyiha tarkibi

1. **Muhitni tayyorlash**  
   `pip install wfdb neurokit2 numpy scipy matplotlib scikit-learn tensorflow`

2. **Ma’lumotlarni yuklash**  
   ```python
   import wfdb
   record = wfdb.rdrecord('100', pn_dir='mitdb')
   signal = record.p_signal[:,0]
