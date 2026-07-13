# Endüstri Mühendisliği AI Becerileri

🇬🇧 English version: [README.md](README.md)

> Yapay zeka asistanınız, metodolojisi olmayan parlak bir analisttir. Kendi haline bırakılırsa verinizin dörtte birini sessizce düşüren bir MAPE hesaplar, Pareto'yu yanlış birimle sıralar ve müşterinizin tanımayacağı bir zamanında-teslimat KPI'ı raporlar.
>
> Bu beceriler ona endüstri mühendisinin disiplinini kurar — tanımları, tuzakları ve doğrulama alışkanlıklarını — böylece ajanınızın ürettiği analiz, yönetim toplantısında savunabileceğiniz bir analiz olur.

Agent skill'leri, düz markdown talimat klasörleridir ([açık standart](https://agentskills.io); Claude Code, Codex, Cursor ve 40'tan fazla ajan aracı destekler). Buradaki her beceri bir **süreç disiplinidir**: kod eklemez, yargı ekler — neyi hangi sırayla hesaplamalı, hangi tuzaklara bakmalı ve sunmadan önce nasıl doğrulamalı.

## Beceriler

| Beceri | Neyi disipline eder | Şunları söylediğinizde devreye girer |
|--------|--------------------|--------------------------------------|
| [`otif-analysis`](skills/otif-analysis/SKILL.md) | Teslimat performansı: 5 basamaklı metrik merdiveni, sürücü ayrıştırma, kuyruk analizi | "OTIF", "zamanında teslimat", "%95'te müşteriler neden şikayetçi?" |
| [`forecast-accuracy-review`](skills/forecast-accuracy-review/SKILL.md) | Tahmin değerlendirme: WMAPE + yanlılık + naive'e karşı FVA, kayan-orijin testleri | "tahmin doğruluğu", "talep planlamamız işe yarıyor mu?" |
| [`abc-xyz-segmentation`](skills/abc-xyz-segmentation/SKILL.md) | Portföy segmentasyonu: değer × değişkenlik 9-kutusu, hücre başına politika | "ABC analizi", "hangi SKU'lar ilgiyi hak ediyor?" |
| [`safety-stock-review`](skills/safety-stock-review/SKILL.md) | Tampon boyutlandırma: formül **artı** gerçekte ne teslim ettiğinin ampirik stres testi | "emniyet stoku", "servis seviyesi", "sipariş noktası" |
| [`root-cause-pareto`](skills/root-cause-pareto/SKILL.md) | Pareto disiplini: birim seçimi, kategori hijyeni, maruziyet normalizasyonu, takip metriği | "duruş paretosu", "hata sıralaması", "80/20" |
| [`weekly-ops-report`](skills/weekly-ops-report/SKILL.md) | Raporlama sözleşmesi: ne değişti / nerede yoğun / hangi karar | "haftalık rapor", "KPI'larımızı yönetim için özetle" |

## Bunları farklı kılan ne?

Her beceri **adımları değil, tuzakları** kodlar — gerçek operasyonlarda tekrar tekrar karşılaştığım ölçüm kapanlarını: MAPE'nin sessiz sıfır-düşürmesi, bedava KPI puanı satın alan tolerans pencereleri, sözleşme dolum oranı derken çevrim servisi kotasyonu, Pareto'nun en uzun çubuğu olarak "Diğer". Her biri bir doğrulama döngüsüyle (sunmadan önce ham veriyle mutabakat) ve tanımlı bir çıktı sözleşmesiyle biter.

Bu becerilerin arkasındaki metodoloji, sayılar ve grafiklerle *ölçüm dürüstlüğü* serisinde gösterilmiştir: [otif-analytics](https://github.com/gulmezeren2-byte/otif-analytics) · [forecast-accuracy-lab](https://github.com/gulmezeren2-byte/forecast-accuracy-lab) · [abc-xyz-inventory](https://github.com/gulmezeren2-byte/abc-xyz-inventory) · [auto-report-pipeline](https://github.com/gulmezeren2-byte/auto-report-pipeline)

## Kurulum

**Claude Code** — beceri klasörlerini proje ya da kullanıcı beceri dizininize kopyalayın:

```bash
git clone https://github.com/gulmezeren2-byte/industrial-engineering-ai-skills
cp -r industrial-engineering-ai-skills/skills/* ~/.claude/skills/        # kullanıcı geneli
# veya: cp -r industrial-engineering-ai-skills/skills/* .claude/skills/  # yalnızca bu proje
```

**Diğer ajanlar** (Codex, Cursor, Gemini CLI, ...) — aynı klasörler, [Agent Skills standardına](https://agentskills.io) göre; aracınızın beceri dizinine bakın.

**Ajansız, herhangi bir LLM** — bir SKILL.md dosyasını açın ve sorunuzdan önce bağlam olarak yapıştırın; her biri tek başına çalışan bir metodoloji brifingi olarak yazılmıştır.

## Yol haritası — sıradaki beceriler

- [ ] `smed-changeover-analysis` — model dönüş süresi kısaltma, iç/dış ayrım disiplini
- [ ] `line-balancing` — takt, öncelik ilişkileri, denge kaybı muhasebesi
- [ ] `demand-pattern-classification` — düzgün/düzensiz/kesikli/lumpy talebi doğru yönteme yönlendirme
- [ ] `mrp-sanity-check` — parametre denetimi: parti büyüklükleri, temin süreleri, emniyet ayarları vs gerçek
- [ ] `kpi-tree-design` — stratejik hedeften ölçülebilir sürücü ağacına, gösteriş metriksiz
- [ ] `inventory-health-audit` — fazla/ölü stok tespiti ve nakit-serbestleştirme boyutlandırması

Öneriler açık — tekrar tekrar yaptığınız en dağınık analizle bir issue açın.

## Hakkında

**[Eren Gülmez](https://www.linkedin.com/in/erengulmez)** tarafından derlendi ve yazıldı — endüstri mühendisi, İstanbul. Ölçüm sistemleri tasarlar ve onları hayata geçirmek için modern araçları yönetirim; bu beceriler o işin yargı katmanının yeniden kullanım için paketlenmiş halidir.

Açık endüstri mühendisliği araç setinin parçası → **[awesome-industrial-engineering](https://github.com/gulmezeren2-byte/awesome-industrial-engineering)**

## Lisans

[MIT](LICENSE)
