# LLM Security Nedir? Yapay Zeka Güvenliğinin Yeni Cephesi

**Yazar:** Fevzi Ege Yurtsevenler — Yapay Zeka Güvenliği Araştırmacısı, AltaySec Kurucusu  
**Yayın:** AltaySec | [altaysec.com.tr](https://altaysec.com.tr)  
**Tarih:** Nisan 2026  
**Seri:** LLM Security Temelleri #1

---

> *"Yazılımı artık yapay zeka yazıyor; güvenliğini ise yalnızca yapay zekanın nasıl 'düşündüğünü' anlayanlar sağlayacak."*

---

## Giriş: Yeni Bir Güvenlik Alanı Doğuyor

Siber güvenlik tarihinde her yeni teknoloji dalgası, beraberinde yeni saldırı yüzeyleri getirdi. Web uygulamalarının yaygınlaşması SQL Injection ve XSS gibi açıkları doğurdu. Mobil uygulamalar yeni bir saldırı kategorisi yarattı. Bulut altyapıları güvenlik paradigmasını kökten değiştirdi.

Şimdi aynı süreç, büyük dil modelleri (LLM) ve yapay zeka sistemleri için yaşanıyor.

**LLM Security** (LLM Güvenliği), büyük dil modellerine dayalı yapay zeka sistemlerini hedef alan saldırıları inceleyen, bu sistemlerin zafiyetlerini tespit eden ve savunma mekanizmaları geliştiren disiplinlerarası bir güvenlik alanıdır.

Bu yazı, LLM Security'nin ne olduğunu, neden önemli olduğunu ve klasik siber güvenlikten nasıl ayrıldığını açıklamaktadır.

---

## LLM Nedir? (Hızlı Özet)

**Büyük Dil Modeli (Large Language Model — LLM)**, milyarlarca parametreyle eğitilmiş ve doğal dili anlayıp üretebilen derin öğrenme modelidir. ChatGPT, Claude, Gemini ve Llama bu kategorinin en tanınan örnekleridir.

LLM'ler artık sadece chatbot değil:
- Müşteri destek sistemleri
- Kod yazma asistanları (GitHub Copilot, Cursor)
- Belge analiz araçları
- Finansal danışmanlık botları
- Sağlık bilgi sistemleri
- Otonom yapay zeka ajanları

...olarak kritik iş süreçlerinin merkezine konumlanıyor. Bu kritiklik, güvenliği zorunlu kılıyor.

---

## LLM Security Nedir?

LLM Security, üç temel soruyu yanıtlar:

**1. LLM sistemleri nasıl saldırıya uğrar?**  
Prompt injection, jailbreak, veri zehirlenmesi, model çalma gibi tekniklerle.

**2. Bu saldırıların sonuçları nelerdir?**  
Veri sızıntısı, yetkisiz erişim, zararlı içerik üretimi, sistem ele geçirme.

**3. Bu sistemler nasıl korunur?**  
Guardrail'ler, girdi/çıktı filtreleme, erişim kontrolü, izleme sistemleri.

### Resmi Tanım

[OWASP Gen AI Security Project](https://genai.owasp.org/), LLM güvenliğini şu bağlamlarda ele alır:
- Büyük dil modellerinin kendisindeki zafiyetler
- LLM'lerin entegre edildiği uygulama katmanındaki açıklar
- LLM'lerin kullandığı harici araç ve veri kaynaklarındaki riskler
- Otonom ajan sistemlerinin oluşturduğu yeni saldırı yüzeyleri

---

## Neden Klasik Güvenlikten Farklı?

Bu sorunun cevabı LLM Security'yi anlamak için kritik.

### Klasik Güvenlikte
- Sistem deterministik çalışır: aynı girdi her zaman aynı çıktıyı üretir
- Zafiyetler kod düzeyinde tanımlanabilir
- Patch uygulanabilir, sorun çözülür
- Saldırı yüzeyi öngörülebilir

### LLM Güvenliğinde
- Sistem **stokastik** (rastlantısal) çalışır: aynı girdi farklı çıktılar üretebilir
- Zafiyetler genellikle **modelin doğasından** kaynaklanır, kod hatası değil
- Tam anlamıyla "patch" uygulanamaz; sürekli güncelleme ve izleme şarttır
- Saldırı yüzeyi **dil**dir — ve dil sonsuz kombinasyonlar sunar

> [OWASP LLM Top 10 2025](https://genai.owasp.org/llm-top-10/) belgesinin giriş kısmı şunu vurgular: "Prompt injection güvenlik açıkları, modellerin prompt'ları işleme biçiminden kaynaklanmaktadır ve girdi, modelin diğer bölümlerine yanlış şekilde prompt verisi iletmesine zorlayabilir."

Bu, bir SQL Injection açığını yamamak gibi değil. Çünkü sorun kodda değil, modelin "düşünme" biçiminde.

---

## LLM Security'nin Kapsadığı Alan

### Saldırı Kategorileri

| Kategori | Açıklama |
|----------|----------|
| **Prompt Injection** | Girdi manipülasyonuyla modelin davranışını değiştirme |
| **Jailbreak** | Güvenlik filtrelerini ve guardrail'leri aşma |
| **Indirect Prompt Injection** | Dış kaynaklardan (doküman, web, e-posta) talimat enjeksiyonu |
| **Data Poisoning** | Eğitim verisini zehirleme |
| **Model Extraction** | API sorguları yoluyla modeli kopyalama |
| **Supply Chain Saldırısı** | Üçüncü taraf model ve kütüphaneleri hedef alma |
| **RAG Poisoning** | Vektör veritabanlarına zararlı içerik enjeksiyonu |
| **Ajansal Saldırılar** | Otonom AI ajanlarını manipüle etme |
| **MCP Saldırıları** | Model Context Protocol güvenlik açıkları |

### Savunma Katmanları

- **Girdi Doğrulama:** Kullanıcı girdilerini zararlı talimatlar için tara
- **Çıktı Filtreleme:** LLM çıktılarını downstream sistemlere göndermeden denetle
- **Guardrail Sistemleri:** Modelin içi ve dışı için davranış sınırları
- **Erişim Kontrolü:** Modelin erişebildiği kaynak ve araçları sınırla
- **İzleme ve Loglama:** Anormal davranışları gerçek zamanlı tespit et
- **Red Teaming:** Sistemi düşman perspektifinden düzenli test et

---

## Neden Şimdi Kritik?

### Pazar Gerçeği

2025-2026 itibarıyla LLM tabanlı sistemler artık oyuncak değil, kritik altyapı:

- Bankalar müşteri hizmetlerini LLM'e devrediyor
- Hastaneler teşhis destek sistemleri için LLM kullanıyor
- Hukuk firmaları doküman analizini LLM'e yaptırıyor
- Savunma sanayii kod üretiminde AI asistanları kullanıyor

Bu sistemler saldırıya uğradığında hasar çok büyük olabilir.

### Verilerle Konuşalım

- [Adversa AI 2025 Güvenlik Raporu'na](https://adversa.ai/blog/adversa-ai-unveils-explosive-2025-ai-security-incidents-report-revealing-how-generative-and-agentic-ai-are-already-under-attack/) göre, gerçek dünya AI olaylarının **%35'i basit prompt manipülasyonlarından** kaynaklanıyor.
- 2025 araştırmaları, multi-turn (çok turlu) saldırıların 8 açık ağırlıklı modele karşı **%92 başarı oranı** sağladığını gösteriyor.
- Yayımlanmış 12 savunma yönteminden **%90'ından fazlası** uyarlanmış saldırılarla aşılabiliyor.

### Türkiye Bağlamı

Türkiye'de finans, e-ticaret ve kamu sektörü AI tabanlı sistemleri hızla benimsiyor. Ancak bu sistemlerin güvenliğini test edecek uzman sayısı henüz çok sınırlı. Bu boşluk hem bir risk hem de bir fırsat.

---

## LLM Security vs. AI Security vs. ML Security

Bu üç terim sıkça karıştırılır:

**ML Security (Makine Öğrenmesi Güvenliği):** En geniş kapsamlı alan. Tüm ML modellerini (sınıflandırıcılar, regresyon modelleri, neural network'ler dahil) kapsayan güvenlik. Adversarial örnekler, üyelik çıkarımı gibi klasik ML saldırıları bu alandadır.

**AI Security (Yapay Zeka Güvenliği):** ML Security'yi içerir, ayrıca AI sistemlerinin kullanıldığı daha geniş bağlamı (otonom sistemler, karar mekanizmaları) kapsar.

**LLM Security:** Özellikle büyük dil modellerine odaklanır. Prompt injection, jailbreak, sistem promptu sızıntısı gibi LLM'e özgü zafiyetleri kapsar. Ajansal AI ve MCP güvenliği de bu kapsamın en güncel parçasıdır.

---

## Temel Kaynaklar ve Çerçeveler

LLM Security'nin referans aldığı temel kurumlar ve kaynaklar:

| Kaynak | Açıklama | Link |
|--------|----------|------|
| OWASP LLM Top 10 (2025) | LLM zafiyetlerinin en kapsamlı sınıflandırması | [genai.owasp.org](https://genai.owasp.org/) |
| MITRE ATLAS | AI adversarial tehdit matrisi | [atlas.mitre.org](https://atlas.mitre.org/) |
| NIST AI RMF | Federal AI risk yönetim çerçevesi | [airc.nist.gov](https://airc.nist.gov/Home) |
| OWASP AI Exchange | Endüstriler arası AI güvenlik rehberi | [owaspai.org](https://owaspai.org/) |
| Google SAIF | Google'ın güvenli AI çerçevesi | [safety.google](https://safety.google/cybersecurity-advancements/saif/) |

---

## Sonraki Adımlar

Bu yazı serisi boyunca LLM Security'yi katman katman ele alacağız:

1. **LLM Security Nedir?** ← *Şu an buradasınız*
2. [Prompt Injection Nedir?](#) — En yaygın LLM saldırısı
3. [OWASP LLM Top 10 Türkçe](#) — 10 kritik zafiyet sınıfı
4. [RAG Security Nedir?](#) — Vektör veritabanı güvenliği
5. [AI Agent Security Nedir?](#) — Otonom sistemlerin güvenliği
6. [LLM Security Roadmap](#) — Kapsamlı öğrenme yolu
7. [AI Security Öğrenme Rehberi](#) — Başlangıç rehberi

---

## Özet

LLM Security, yapay zeka sistemlerinin güvenliğini sağlamaya odaklanan yeni ve hızla büyüyen bir alandır. Klasik güvenlikten temel farkı, saldırı yüzeyinin kod değil dil olması ve zafiyetlerin modelin stokastik doğasından kaynaklanmasıdır.

Türkiye'de bu alanda uzmanlaşmak, hem kariyer hem de girişimcilik açısından önemli bir avantaj sunuyor. AltaySec olarak bu boşluğu doldurmayı ve Türkiye'nin LLM güvenlik ekosistemini oluşturmayı hedefliyoruz.

---

**Yazar Hakkında**  
*Fevzi Ege Yurtsevenler, Türkiye'nin yapay zeka güvenliği alanındaki öncü araştırmacılarından biridir. AltaySec'in kurucusu olarak Türkçe LLM güvenlik içerikleri üretiyor, eğitimler veriyor ve bu alanda Türkiye'nin ilk ekosistemini inşa ediyor. LLM güvenliği alanında aktif araştırma sürdürmektedir.*

**İletişim:** [altaysec.com.tr](https://altaysec.com.tr) | LinkedIn: Fevzi Ege Yurtsevenler

---

*AltaySec — Türkiye'nin LLM Güvenlik Ekosistemi*  
*Bu içerik Creative Commons lisansı altında paylaşılmaktadır. Kaynak göstererek kullanabilirsiniz.*
