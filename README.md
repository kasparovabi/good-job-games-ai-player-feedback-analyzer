# AI Destekli Oyuncu Geri Bildirim Analiz Otomasyonu

**[▶️ Projenin Çalışmasını İzleyin (Video Demo)] https://www.loom.com/share/a096887d7df84dca85ea4e91e8602c8b?sid=08302e7f-7559-4f01-9e37-0e5578fca48f**

## Projenin Amacı

Bu otomasyon, oyuncu geri bildirimlerini (App Store yorumları, sosyal medya vb.) anlık olarak toplayıp, Google'ın dil modeli Gemini 2.5 Flash'ı kullanarak analiz eder. Yorumun duygu tonunu ve konusunu (Hata Bildirimi, Özellik İsteği vb.) belirleyerek, ilgili ekiplere (ürün, QA, topluluk yönetimi) anında Slack üzerinden bildirim gönderir.

Bu proje, ilanda belirtilen "pazarlama ve ürün ekipleriyle işbirliği yapma", "otomasyon çözümleri tasarlama" ve "en son yapay zeka trendlerini takip etme" yetkinliklerini somut bir şekilde sergilemeyi amaçlamaktadır.

## Teknoloji ve Akış

- **Orkestrasyon:** n8n.io
- **Yapay Zeka Modeli:** Google Gemini 2.5 Flash
- **Bildirim:** Slack API
- **Test Aracı:** Postman

**İş Akışı:**
1.  **Tetikleyici (Webhook):** Yeni bir oyuncu yorumu Postman aracılığıyla sisteme gönderilir.
2.  **AI Analizi (Google Gemini):** Gelen yorum, tek bir API çağrısı ile analiz edilir. Modelden, çıktıyı belirli bir JSON formatında (`sentiment`, `topic`, `summary`) vermesi istenir.
3.  **Veri Ayrıştırma (Code Node):** Gemini'den gelen metin tabanlı JSON, JavaScript ile ayrıştırılır.
4.  **Mantıksal Yönlendirme (Switch Node):** Analiz sonucundaki `topic` alanına göre iş akışı doğru yola yönlendirilir.
5.  **Eylem (Slack):** İlgili Slack kanalına (`#bugs`, `#product-ideas` vb.) formatlanmış bir bildirim gönderilir.

## Öne Çıkan Özellikler

- **Verimlilik:** Üç farklı analiz (duygu, konu, özet) için üç ayrı API çağrısı yapmak yerine, Gemini 2.5 Flash'ın tek çağrıda yapılandırılmış JSON üretme yeteneği kullanılarak maliyet ve gecikme süresi düşürülmüştür.
- **Güncellik:** Sektördeki en yeni ve yetenekli modellerden biri olan Gemini 2.5 Flash kullanılmıştır.
- **Otomatik Yönlendirme:** Geri bildirimin türüne göre ilgili ekibe anında uyarı giderek, sorunlara müdahale süresini kısaltır ve departmanlar arası iletişimi otomatikleştirir.
