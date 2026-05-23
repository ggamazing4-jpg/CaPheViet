# AEO & AIEO – Hướng Dẫn Triển Khai Chi Tiết
## Website Demo: CaPhêViet.vn

---

## Tổng quan về AEO và AIEO

### AEO (Answer Engine Optimization)
Tối ưu hóa để nội dung được **trích dẫn trực tiếp** bởi các công cụ trả lời như Google AI Overviews, voice search, featured snippets.

### AIEO (AI Engine Optimization)
Tối ưu hóa để AI như ChatGPT, Claude, Perplexity **hiểu và cite** nội dung của bạn khi người dùng hỏi về chủ đề liên quan.

### Tại sao quan trọng năm 2025-2026?
- 69% tìm kiếm Google kết thúc không có click (zero-click)
- ChatGPT phục vụ 800 triệu user/tuần
- AI-referred traffic tăng 357% YoY (2025)
- Chỉ 12.4% website hiện tại implement structured data

---

## Các kỹ thuật đã triển khai trên website

### 1. Structured Data / Schema Markup (JSON-LD)

**FAQPage Schema** – Ưu tiên cao nhất
```json
{ "@type": "FAQPage", "mainEntity": [...] }
```
- Research: FAQPage schema = 41% citation rate vs 15% không có
- 3.2x khả năng xuất hiện trong Google AI Overviews
- Mỗi câu hỏi được đặt trong `@type: Question` và `@type: Answer`

**HowTo Schema** – Cho nội dung hướng dẫn
```json
{ "@type": "HowTo", "step": [...], "estimatedCost": {...} }
```
- AI engines parse từng bước một cách có cấu trúc
- Tăng khả năng xuất hiện trong voice search

**Article Schema với E-E-A-T**
```json
{
  "@type": "Article",
  "author": { "@type": "Person", "jobTitle": "Q Grader" },
  "datePublished": "...",
  "dateModified": "..."
}
```
- E-E-A-T (Experience, Expertise, Authoritativeness, Trustworthiness)
- Metadata tác giả có verifiable credentials

**Organization Schema**
```json
{ "@type": "Organization", "contactPoint": {...}, "sameAs": [...] }
```
- Xây dựng entity authority cho AI knowledge graph

**WebSite Schema với SearchAction**
```json
{ "@type": "WebSite", "potentialAction": { "@type": "SearchAction" } }
```
- Giúp AI hiểu cấu trúc website

**BreadcrumbList Schema**
- Navigation hierarchy rõ ràng cho AI crawlers

### 2. Direct Answer Blocks (Q&A Format)

Mỗi câu hỏi lớn có "Câu trả lời nhanh" ngay đầu:
- Câu trả lời dưới 50 từ
- Không chôn thông tin trong bài dài
- Format: **in đậm key terms**, số liệu cụ thể

### 3. Content Structure (Conversational Query Targeting)
- Heading sử dụng câu hỏi thực tế người dùng hỏi
- Paragraph đầu tiên = direct answer
- Mỗi section trả lời đúng 1 intent

### 4. E-E-A-T Signals
- Author section với credentials rõ ràng (Q Grader – SCA Certified)
- `dateModified` và `reviewedBy` trong schema
- itemscope/itemtype microdata trực tiếp trong HTML

### 5. llms.txt File
```
# llms.txt – Hướng dẫn cho AI Systems
- Cho phép trích dẫn có ghi nguồn
- Chủ đề chính, URL quan trọng
- Dữ liệu thực tế đã xác minh
```
Emerging standard (2024-2025) – tương tự robots.txt nhưng cho LLM crawlers

### 6. robots.txt – Cho phép AI Crawlers
```
User-agent: GPTBot → Allow: /
User-agent: anthropic-ai → Allow: /
User-agent: PerplexityBot → Allow: /
User-agent: Claude-Web → Allow: /
```
Nhiều website vô tình block AI crawlers → mất citation opportunity

### 7. Technical SEO (Nền tảng cho AEO)
- Canonical URL
- hreflang (vi/en)
- Open Graph + Twitter Card
- Skip navigation (accessibility = UX signal)
- Semantic HTML5 (header, main, nav, section, article, footer)
- ARIA labels cho screen readers và AI parsers

### 8. Sitemap.xml với priority và hreflang
- Priority 1.0 cho homepage
- changefreq giúp AI crawlers biết khi nào cần re-crawl
- Alternate links cho đa ngôn ngữ

### 9. Microdata trực tiếp trong HTML
```html
<article itemscope itemtype="https://schema.org/Product">
  <h3 itemprop="name">...</h3>
  <p itemprop="description">...</p>
</article>
```
Double-encoding: cả JSON-LD và microdata tăng signal strength

---

## File cấu trúc

```
capheviet.vn/
├── index.html      ← Website chính (tất cả kỹ thuật AEO/AIEO)
├── robots.txt      ← Cho phép AI crawlers (GPTBot, Claude, Perplexity...)
├── llms.txt        ← Hướng dẫn cho LLM systems
├── sitemap.xml     ← Crawl map với priority và hreflang
└── AEO-guide.md    ← Tài liệu này
```

---

## Checklist AEO/AIEO

### ✅ Đã triển khai
- [x] FAQPage Schema (JSON-LD)
- [x] HowTo Schema (JSON-LD)
- [x] Article Schema với E-E-A-T
- [x] Organization Schema
- [x] WebSite Schema + SearchAction
- [x] BreadcrumbList Schema
- [x] Microdata (itemscope/itemtype)
- [x] Direct answer blocks
- [x] Q&A format content structure
- [x] Author credentials (verifiable)
- [x] dateModified + reviewedBy
- [x] llms.txt
- [x] robots.txt (AI crawlers allowed)
- [x] sitemap.xml
- [x] Canonical URL
- [x] hreflang tags
- [x] Open Graph + Twitter Card
- [x] Semantic HTML5
- [x] ARIA labels
- [x] Skip navigation
- [x] Mobile-responsive
- [x] Fast loading (inline CSS, preconnect fonts)

### 📊 Metrics để đo lường
- Share-of-Answer (SoA): % queries bạn được cite
- Featured snippet presence (Semrush, Ahrefs)
- Google Search Console: high impressions, low CTR = snippet
- Manual test: hỏi ChatGPT/Perplexity về chủ đề của bạn

---

## Nguồn tham khảo

- Relixir (2025): FAQPage schema = 41% citation rate
- Frase.io: 3.2x AI Overviews với FAQ schema
- Zensciences: Brands adopting AEO = 40% higher AI visibility
- CXL Blog: 69% zero-click searches in 2025
- UNU Campus: 357% YoY growth in AI-referred traffic
