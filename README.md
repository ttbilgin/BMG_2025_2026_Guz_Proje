# BLM0101 - Bilgisayar Mühendisliğine Giriş
## 2025-2026 Güz Dönemi | Dönem Projesi: 1-Bit Aritmetik ve Mantık Birimi (ALU) Tasarımı

**Ders Sorumlusu:** Prof. Dr. Turgay Tugay BİLGİN

---

### 1. Projenin Amacı
Bu projenin amacı; bilgisayar işlemcilerinin (CPU) merkezinde yer alan ve matematiksel/mantıksal işlemleri gerçekleştiren **ALU (Arithmetic Logic Unit)** biriminin temel çalışma prensibini en basit haliyle anlamaktır. Öğrencilerden, **CircuitVerse** simülasyon ortamında temel mantık kapılarını (AND, OR, XOR vb.) kullanarak **1-bitlik** veriler üzerinde çalışan bir işlemci prototipi tasarlamaları beklenmektedir.

### 2. Proje Tanımı ve Blok Diyagramı
Her öğrenci, **[CircuitVerse.org/simulator](https://circuitverse.org/simulator)** platformunu kullanarak aşağıda belirtilen özelliklere sahip **1-Bitlik bir ALU** tasarlayacaktır.

Devrenin genel yapısı aşağıdaki blok diyagramda gösterildiği gibi olmalıdır:

```text
                     İşlem Seçici Uçlar
                       (Select Lines)
                        S1        S0
                        │         │
                  ┌─────▼─────────▼─────┐
                  │                     │
      A Girişi    │                     │
     (1 x Input)  │                     │
        A ───────>│      1-BIT ALU      │
                  │       DEVRESİ       │──────> Sonuç (Out)
      B Girişi    │                     │      (1 x Output)
     (1 x Input)  │                     │
        B ───────>│                     │
                  │                     │
                  └─────────────────────┘
````

  * **Girişler:** A sayısı için 1 adet, B sayısı için 1 adet ve İşlem Seçimi (S1, S0) için 2 adet standart "Input" (Kare buton) bileşeni kullanılacaktır.
  * **Çıkış:** Sonucu göstermek için 1 adet standart "Output" (Yuvarlak LED) bileşeni kullanılacaktır.

### 3\. Grup Dağılımı ve Görevler

Proje varyasyonları, **Öğrenci Numaranızın Son Rakamına** göre belirlenmiştir. Aşağıdaki tablodan numaranıza uygun grubu bulunuz. Her grup, devresinde **Toplama (ADD)** işlemini (Elde/Carry ihmal edilerek sadece Toplam/Sum biti) ve kendisine atanan diğer 3 işlemi gerçekleştirmek zorundadır.

| Grup | Öğrenci No Son Rakam | İşlem 00 (S1=0, S0=0) | İşlem 01 (S1=0, S0=1) | İşlem 10 (S1=1, S0=0) | İşlem 11 (S1=1, S0=1) |
| :--- | :---: | :--- | :--- | :--- | :--- |
| **A** | **0 veya 1** | **Toplama (ADD)**<br>($A + B$) | **VE (AND)**<br>($A \land B$) | **VEYA (OR)**<br>($A \lor B$) | **Tümleyen A (NOT A)**<br>(A'nın tersi) |
| **B** | **2 veya 3** | **Toplama (ADD)**<br>($A + B$) | **Özel VEYA (XOR)**<br>($A \oplus B$) | **VE Değil (NAND)**<br>($(A \land B)'$) | **VEYA Değil (NOR)**<br>($(A \lor B)'$) |
| **C** | **4 veya 5** | **Toplama (ADD)**<br>($A + B$) | **Transfer A**<br>(Çıkış = A) | **Transfer B**<br>(Çıkış = B) | **Eşitlik (XNOR)**<br>($A \odot B$) |
| **D** | **6 veya 7** | **Toplama (ADD)**<br>($A + B$) | **Tümleyen B (NOT B)**<br>(B'nin tersi) | **Sıfırlama (ZERO)**<br>(Çıkış daima 0) | **Birleme (ONE)**<br>(Çıkış daima 1) |
| **E** | **8 veya 9** | **Toplama (ADD)**<br>($A + B$) | **VE (AND)**<br>($A \land B$) | **Özel VEYA (XOR)**<br>($A \oplus B$) | **Transfer A**<br>(Çıkış = A) |

*(Not: 1-Bitlik Toplama işleminde $1+1=0$ (Elde 1) sonucunu verir. Bu projede sadece Sonuç biti (0) gösterilecektir.)*

### 4\. Teknik Tasarım Kuralları

1.  **İşlem Seçme Mantığı:**
    Devreniz aynı anda 4 farklı işlemi de arka planda hesaplayabilir. Ancak devrenin ana çıkışına (Output) sadece **S1 ve S0** uçlarının seçtiği işlem sonucu gitmelidir. Bunu sağlamak için **Mantık Kapılarını (AND, OR, NOT)** kullanarak bir yönlendirme/seçme mekanizması kurmalısınız.
2.  **Bileşen Kullanımı:**
    Devrede "Hex Display", "Seven Segment Display" gibi hazır göstergeler veya entegre devre blokları (Multiplexer, Adder vb.) **kullanılmayacaktır**. Tüm işlemler temel kapılarla (AND, OR, NOT, XOR) tasarlanmalıdır.
3.  **Tasarım Ortamı:**
    Proje sadece **CircuitVerse** (online) simülatöründe yapılacaktır.

### 5\. Teslimat Yöntemi ve İçeriği

Teslimatlar **Ekampus** sistemi üzerinden yapılacaktır. Sisteme yüklemeniz gerekenler şunlardır:

#### A) CircuitVerse Proje Dosyası (\*.cv)

  * Tasarımınızı tamamladıktan sonra CircuitVerse menüsünden **Project \> Export Project** seçeneği ile `.cv` uzantılı dosyayı bilgisayarınıza indiriniz.
  * Bu dosyayı `Ad_Soyad_No.cv` formatında isimlendirip Ekampus'e yükleyiniz.

#### B) GitHub Proje Linki

  * Projeniz için **GitHub** üzerinde bir "Repository" (Depo) oluşturunuz.
  * Bu reponun linkini (`https://github.com/kullaniciadi/projeadi`) Ekampus'teki ilgili alana yapıştırınız.

### 6\. GitHub README.md İçeriği (Proje Raporu)

> GitHub reponuza `Ad_Soyad_No.cv` formatında isimlendirdiğiniz Devre Tasarım dosyasını da yükleyiniz.

GitHub reponuzun ana sayfasında bulunan `README.md` dosyası, **Proje Raporunuz** niteliğindedir ve Markdown formatında hazırlanmalıdır. Rapor şu başlıkları ve içerikleri **zorunlu olarak** kapsamalıdır:

1.  **Proje Başlığı ve Öğrenci Bilgileri:** Ad, Soyad, Numara ve Grup Bilgisi.
2.  **Devre Tasarımı ve Mantığı:**
      * Devrenizin genel çalışma mantığını kısaca açıklayınız.
      * Hangi kapıları neden kullandığınızı belirtiniz.
      * **CircuitVerse Ekran Görüntüsü:** Devrenizin tamamını gösteren net bir ekran görüntüsünü buraya ekleyiniz.
3.  **İşlem Doğrulama (Test Senaryoları):**
      * Her işlem modu (00, 01, 10, 11) için en az birer örnek deneme yapınız.
      * Her deneme için CircuitVerse üzerindeki giriş ve çıkışları (yanan/sönen ışıkları) gösteren **Ekran Görüntülerini** koyunuz ve altına açıklamasını yazınız.
      * *Örnek Format:*
          * **İşlem:** Toplama (00)
          * **Giriş:** A=1 (Açık), B=0 (Kapalı)
          * **Beklenen:** 1 (Açık)
          * **Sonuç:** [Ekran Görüntüsü] -\> Çıkış LED'i yanmaktadır, devre doğrudur.

### 7\. Değerlendirme Kriterleri

  * **Devre Doğruluğu (%50):** `.cv` dosyası çalıştırıldığında devrenin kendisine atanan 4 işlemi hatasız yapması.
  * **GitHub Dokümantasyonu (%30):** `README.md` dosyasının düzeni, açıklamaların netliği ve ekran görüntülerinin (kanıtların) eksiksiz olması.
  * **Tasarım Temizliği (%20):** Devre şemasının anlaşılır ve düzenli olması (kablo karmaşasının önlenmesi).

-----

**Son Teslim Tarihi:** [TARİH GİRİNİZ] Saat: 23:59

**Önemli Uyarı:**

  * CircuitVerse projeleri ve GitHub repoları üzerinden intihal kontrolü yapılacaktır. Birbirinden kopyalanmış tasarımlar veya raporlar tespit edilirse, ilgili tüm öğrencilerin ödevi geçersiz sayılacaktır.
  * Her öğrenci sadece kendi grubuna ait işlemleri yapmalıdır.

Başarılar dilerim.

```
