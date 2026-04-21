# MetaSurge v2

メタマスクウォレットのダウンロードと利用開始に関する日本語ガイドサイト。GitHub Pages でホストされる、完全静的・単一ファイル構成の本番対応版です。

- 公開 URL: <https://metasurge.github.io/>
- 言語: 日本語 (ja_JP)
- バージョン: 2.0 (v1 denetimi sonrası tüm bulgular giderildi)
- 公開日: 2026-04-20

## v1 → v2 İyileştirme listesi

| # | Kategori | Bulgu | Çözüm |
|---|---|---|---|
| 1 | Meta | Meta description 58 char (çok kısa) | **150 char**'a çıkarıldı |
| 2 | A11Y | Dokunma hedefleri 44px | **Tüm interaktif öğeler 48×48px** |
| 3 | Schema | Person/Editorial schema eksik | **Dedicated editorial-team Org schema eklendi** |
| 4 | E-E-A-T | Hakkımızda / iletişim eksik | **About + Contact + Editorial Policy modal'ları eklendi** |
| 5 | E-E-A-T | Who/How/Why açıklanmamış | **"Bu rehber nasıl hazırlandı?" bölümü eklendi** |
| 6 | SEO | hreflang link tag yok | `<link rel="alternate" hreflang="ja">` + `x-default` eklendi |
| 7 | SEO | robots.txt `Host:` non-standard | Kaldırıldı |
| 8 | SEO | AI search bot'ları global bloke | **GEO için OAI-SearchBot/PerplexityBot/Google-Extended ALLOW edildi**; sadece training-only bot'lar bloklandı |
| 9 | Güvenlik | CSP yok | `<meta http-equiv="Content-Security-Policy">` eklendi |
| 10 | Güvenlik | Referrer-Policy yok | `<meta name="referrer" content="strict-origin-when-cross-origin">` |
| 11 | Güvenlik | Upgrade-insecure yok | CSP içinde `upgrade-insecure-requests` |
| 12 | UX | Table of Contents yok | **目次 navigation eklendi** (11 maddeli) |
| 13 | Semantik | H1 `<section>` içinde | **`<article><header>` yapısına taşındı** |
| 14 | Kontrast | `#9A9A9F` AA sınırda | **`#85888B`** (daha iyi kontrast) |
| 15 | Kontrast | `#5A5A5F` kullanıldı | **`#3A3A3F` / `#4A4A4F`** ana metin için |
| 16 | İç link | Kontekstüel link azlığı | **Paragraf içi cross-section link'ler artırıldı** |
| 17 | İçerik | 6159 JP char | **~8500 JP char**'a genişletildi |
| 18 | A11Y | Dark mode desteği yok | **`prefers-color-scheme: dark` ile tam dark mode** |

## Ek kazanımlar

- `itemprop` microdata (Schema.org) direkt article üzerinde
- Gelişmiş sitemap: `image:image` extension ile OG image de indexlenir
- `<meta property="article:tag">` her hedef anahtar kelime için
- `apple-touch-icon.png` (180×180) ayrı dosya
- `color-scheme: light dark` meta ile native dark mode desteği
- `scroll-padding-top: 72px` ile sticky header ve anchor link uyumu
- `prefers-reduced-motion` tam desteği
- `format-detection: telephone=no` (Japonca sayılarının otomatik tel linki yapılmasını engeller)
- CSS `contain: layout style` ile paint alanı sınırlama (INP için)

## Dosya yapısı (12 dosya)

```
metasurge-v2/
├── index.html              47 KB — ana içerik + 5 modal
├── 404.html                2.5 KB
├── sitemap.xml             0.7 KB — image extension ile
├── robots.txt              0.9 KB
├── site.webmanifest        0.6 KB
├── humans.txt              0.6 KB
├── og-image.png            96 KB — 1200×630
├── og-image.svg            2.8 KB
├── apple-touch-icon.png    8.7 KB — 180×180
├── README.md               (bu dosya)
├── .nojekyll               (GitHub Pages bypass)
└── .well-known/
    └── security.txt        0.3 KB — RFC 9116
```

## Core Web Vitals (saha verisi hedefi)

| Metrik | Hedef | Tahmini |
|---|---|---|
| LCP | ≤ 2.5 s | < 1.0 s (inline SVG hero) |
| INP | ≤ 200 ms | < 50 ms (vanilla JS delegated listeners) |
| CLS | ≤ 0.1 | 0 (sistem fontu, tüm görsellerde width/height) |
| TTFB | < 500 ms | < 200 ms (Fastly CDN üzerinden GitHub Pages) |

## Deploy

1. Repo: `metasurge.github.io` (user-site deseni)
2. Dosyaları kök dizine yükle (`.nojekyll` ve `.well-known/` dahil)
3. Settings → Pages → Deploy from branch (main / root)
4. Search Console → sitemap.xml gönder
5. Rich Results Test + PageSpeed Insights doğrula
