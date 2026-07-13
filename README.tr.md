# Endüstri Mühendisliği AI Becerileri

🇬🇧 English version: [README.md](README.md)

> Yapay zeka asistanınız, metodolojisi olmayan parlak bir analisttir. Kendi haline bırakılırsa verinizin dörtte birini sessizce düşüren bir MAPE hesaplar, Pareto'yu yanlış birimle sıralar ve müşterinizin tanımayacağı bir zamanında-teslimat KPI'ı raporlar.
>
> Bu paket ona endüstri mühendisinin disiplinini kurar — sabit bir yöntem, tanımlar, tuzaklar ve doğrulama alışkanlıkları — böylece ajanınızın ürettiği analiz, yönetim toplantısında savunabileceğiniz bir analiz olur.

Bir prompt torbası değil: **tek bir operasyon-analizi yöntemi, kompoze edilebilir parçalar halinde.** Beceriler "nasıl"ı, roller "kim"i, kurallar "asla"ları, şablonlar çıktıları taşır. [Agent Skills açık standardı](https://agentskills.io) üzerine kuruludur (Claude Code, Codex, Cursor ve 40+ araç).

## Bileşenler

| Bileşen | Nedir | Anlamı |
|---------|-------|--------|
| [`skills/`](skills/) (7) | Ajanın ihtiyaç anında yüklediği metodoloji brifingleri | *İş nasıl yapılır* |
| [`agents/`](agents/) (4) | Rol tanımları (Claude Code subagent formatı; her yerde sistem promptu olarak kullanılabilir) | *İşi kim yapar* |
| [`rules/`](rules/) (1) | Her analizde geçerli veri-hijyeni kısıtları | *Neye asla izin yok* |
| [`templates/`](templates/) (3) | Analiz brifi, veri sözleşmesi, karar memosu | *İş ne üretir* |

## Yöntem

Her analiz aynı sırayı izler — giriş becerisi [`using-ops-method`](skills/using-ops-method/SKILL.md) bunu dayatır:

**brif → veri sözleşmesi → dürüst metrikler → sürücü ayrıştırma → stres testi → karar memosu**

Altındaki anayasa (tam metin: [`rules/data-hygiene.md`](rules/data-hygiene.md)): düşen her satırı raporla · her paydayı ve tarih çıpasını açıkça yaz · asla oranların ortalamasını alma · "hiçbir şey yapmama"ya karşı kıyasla · sunmadan önce bir manşet sayıyı ham veriyle mutabakata sok.

## Beceriler

| Beceri | Neyi disipline eder | Şunları söylediğinizde devreye girer |
|--------|--------------------|--------------------------------------|
| [`using-ops-method`](skills/using-ops-method/SKILL.md) | **Giriş noktası** — sıra, yönlendirme ve anayasa | herhangi bir operasyon/tedarik zinciri analizi |
| [`otif-analysis`](skills/otif-analysis/SKILL.md) | Teslimat performansı: 5 basamaklı metrik merdiveni, sürücü ayrıştırma, kuyruk analizi | "OTIF", "zamanında teslimat" |
| [`forecast-accuracy-review`](skills/forecast-accuracy-review/SKILL.md) | Tahmin değerlendirme: WMAPE + yanlılık + naive'e karşı FVA | "tahmin doğruluğu", "talep planlamamız işe yarıyor mu?" |
| [`abc-xyz-segmentation`](skills/abc-xyz-segmentation/SKILL.md) | Portföy segmentasyonu: değer × değişkenlik 9-kutusu | "ABC analizi", "hangi SKU'lar önemli?" |
| [`safety-stock-review`](skills/safety-stock-review/SKILL.md) | Tampon boyutlandırma: formül **artı** ampirik stres testi | "emniyet stoku", "servis seviyesi" |
| [`root-cause-pareto`](skills/root-cause-pareto/SKILL.md) | Pareto disiplini: birim seçimi, kategori hijyeni, normalizasyon | "duruş paretosu", "80/20" |
| [`weekly-ops-report`](skills/weekly-ops-report/SKILL.md) | Raporlama sözleşmesi: ne değişti / nerede yoğun / hangi karar | "haftalık rapor", "yönetim özeti" |

## Roller

| Rol | Görev |
|-----|-------|
| [`delivery-analyst`](agents/delivery-analyst.md) | OTIF ve servis seviyesi analizleri, uçtan uca |
| [`demand-planner`](agents/demand-planner.md) | Talep profilleme ve tahmin-değeri hükümleri |
| [`inventory-analyst`](agents/inventory-analyst.md) | Segmentasyon, emniyet stoku, rasyonalizasyon |
| [`ops-reviewer`](agents/ops-reviewer.md) | **Kapı bekçisi**: her analizi kurallara karşı hasmane gözden geçirir — yayından önce |

## Bunu farklı kılan ne?

Her parça **adımları değil, tuzakları** kodlar — gerçek operasyonların ölçüm kapanlarını: MAPE'nin sessiz sıfır-düşürmesi, bedava KPI puanı satın alan tolerans pencereleri, sözleşme dolum oranı derken çevrim servisi kotasyonu, Pareto'nun en uzun çubuğu olarak "Diğer". Her beceri bir doğrulama döngüsüyle ve tanımlı çıktı sözleşmesiyle biter; `ops-reviewer` rolü ise analizinizi bir toplantıda başkası kırmadan önce özel olarak kırmak için vardır.

Metodoloji, sayılar ve grafiklerle *ölçüm dürüstlüğü* serisinde gösterilmiştir: [otif-analytics](https://github.com/gulmezeren2-byte/otif-analytics) · [forecast-accuracy-lab](https://github.com/gulmezeren2-byte/forecast-accuracy-lab) · [abc-xyz-inventory](https://github.com/gulmezeren2-byte/abc-xyz-inventory) · [auto-report-pipeline](https://github.com/gulmezeren2-byte/auto-report-pipeline)

## Kurulum

**Claude Code** — istediğiniz parçaları kopyalayın:

```bash
git clone https://github.com/gulmezeren2-byte/industrial-engineering-ai-skills
cd industrial-engineering-ai-skills
cp -r skills/* ~/.claude/skills/          # kullanıcı geneli beceriler (veya proje başına .claude/skills/)
cp -r agents/* ~/.claude/agents/          # rol subagent'ları (veya proje başına .claude/agents/)
cat rules/data-hygiene.md >> CLAUDE.md    # her zaman geçerli kurallar, proje başına
cp templates/* projeniz/docs/             # çıktı şablonları
```

**Diğer ajanlar** (Codex, Cursor, Gemini CLI, ...) — `skills/` klasörleri [Agent Skills standardını](https://agentskills.io) izler; aracınızın beceri dizinine bakın. Rol dosyaları düz sistem promptu olarak çalışır.

**Ajansız, herhangi bir LLM** — bir SKILL.md dosyasını açın ve sorunuzdan önce bağlam olarak yapıştırın; her biri tek başına çalışan bir metodoloji brifingi olarak yazılmıştır.

## Yol haritası — sıradaki beceriler

- [x] Giriş becerisi, roller, kurallar ve şablonlar (paket yapısı)
- [ ] `smed-changeover-analysis` — model dönüş süresi, iç/dış ayrım disiplini
- [ ] `line-balancing` — takt, öncelik ilişkileri, denge kaybı muhasebesi
- [ ] `demand-pattern-classification` — talebi doğru yönteme yönlendirme
- [ ] `mrp-sanity-check` — parametre denetimi: parti büyüklükleri, temin süreleri vs gerçek
- [ ] `kpi-tree-design` — stratejik hedeften sürücü ağacına, gösteriş metriksiz
- [ ] `inventory-health-audit` — fazla/ölü stok tespiti ve nakit-serbestleştirme

Öneriler açık — tekrar tekrar yaptığınız en dağınık analizle bir issue açın.

## Hakkında

**[Eren Gülmez](https://www.linkedin.com/in/erengulmez)** tarafından derlendi ve yazıldı — endüstri mühendisi, İstanbul. Ölçüm sistemleri tasarlar ve onları hayata geçirmek için modern araçları yönetirim; bu paket o işin yargı katmanının yeniden kullanım için paketlenmiş halidir.

Açık endüstri mühendisliği araç setinin parçası → **[awesome-industrial-engineering](https://github.com/gulmezeren2-byte/awesome-industrial-engineering)**

## Lisans

[MIT](LICENSE)
