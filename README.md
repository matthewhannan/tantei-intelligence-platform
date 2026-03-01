# 探偵インテリジェンスプラットフォーム — Tantei Intelligence Platform
## B2B Investigative Intelligence SaaS for Japanese Detective Agencies

**Document Version:** 1.0
**Date:** March 1, 2026
**Classification:** Confidential — Business Plan & Product Specification
**Author:** Hanami Enterprises, LLC

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Market Analysis](#2-market-analysis)
3. [Target Customer Profiles](#3-target-customer-profiles)
4. [Product Design](#4-product-design)
5. [Technical Architecture](#5-technical-architecture)
6. [Database Schema](#6-database-schema)
7. [API Specification](#7-api-specification)
8. [UI/UX Design](#8-uiux-design)
9. [Legal & Compliance](#9-legal--compliance)
10. [Business Model & Pricing](#10-business-model--pricing)
11. [Corporate Structure](#11-corporate-structure)
12. [Go-To-Market Strategy](#12-go-to-market-strategy)
13. [Competitive Analysis](#13-competitive-analysis)
14. [Risk Analysis](#14-risk-analysis)
15. [Development Roadmap](#15-development-roadmap)
16. [Appendix A: Industry Data Tables](#appendix-a-industry-data-tables)
17. [Appendix B: Legal Compliance Checklist](#appendix-b-legal-compliance-checklist)
18. [Appendix C: Source Citations](#appendix-c-source-citations)

---

## 1. Executive Summary

### The Opportunity

Japan's private investigation industry generates approximately **¥86 billion (~$573M USD)** annually across **6,600+ registered detective agencies** (令和3年 / 2021 police statistics). The industry is dominated by infidelity (浮気/uwaki) investigations, which account for an estimated 70-80% of all cases. Despite this substantial market, **there is zero purpose-built Japanese-language investigative software**.

Every existing investigative intelligence platform — Maltego, Skopenow, ShadowDragon, CROSStrax — is English-first with no Japanese data source integration, no Japanese UI, and no understanding of Japanese investigative workflows. Japanese PIs conduct investigations using cameras, GPS trackers, vehicles, and human skill, then compile handwritten or manually typed 調査報告書 (investigation reports). This creates massive inefficiency:

- **60-70% of physical surveillance time produces no actionable intelligence**
- **Report generation takes hours per case** (manually timestamping photos, writing narratives)
- **Multi-office agencies have no centralized case management** (critical for chains with 10-100+ offices)
- **No digital pre-investigation** to narrow surveillance windows before deploying field teams

### The Product

**Tantei Intelligence Platform (探偵インテリジェンスプラットフォーム)** is a B2B SaaS product sold to licensed Japanese detective agencies. It is **not** a consumer surveillance tool. It is an enterprise platform that makes licensed investigators 3-5x more efficient through:

1. **Digital Reconnaissance (デジタル偵察)** — OSINT scanning of public social media and government records to build pre-investigation intelligence
2. **Case Management (案件管理)** — Centralized case tracking, investigator assignment, multi-office coordination
3. **Evidence Studio (証拠スタジオ)** — Tamper-proof evidence capture, chain of custody, automated 調査報告書 generation
4. **Intelligence Dashboard (インテリジェンスダッシュボード)** — Pattern analysis, surveillance window optimization, agency analytics

### Why This, Why Now

| Factor | Status |
|--------|--------|
| Market size | ¥86 billion/year ($573M), growing |
| Competition | Zero Japanese-language competitors |
| Technology readiness | Open-source face recognition (ArcFace), social media APIs, cloud infrastructure all mature |
| Regulatory environment | B2B tool vendor position is legally defensible under APPI (see Section 9) |
| First-mover advantage | No one has attempted this product in Japan |

### Financial Summary

| Metric | Year 1 | Year 2 | Year 3 |
|--------|--------|--------|--------|
| Target customers | 3-7 | 10-20 | 30-50+ |
| Monthly revenue (base) | ¥900K ($6K) | ¥7.1M ($47K) | ¥15-25M ($100-165K) |
| Annual revenue (base) | $24K-48K | $564-792K | $1.2-2M |
| Gross margin | ~80% | ~80% | ~80% |
| Risk-adjusted EV (2-year) | **+$95K (positive)** | | |

---

## 2. Market Analysis

### 2.1 Industry Size & Structure

**Source:** 平成28年経済センサス活動調査 (2016 Economic Census), 警察庁 (National Police Agency) annual statistics

| Metric | Value | Source |
|--------|-------|--------|
| Total market revenue | ¥85.9 billion (~$573M) | 2016 Economic Census |
| Registered agencies (2021) | 6,600+ | NPA statistics |
| Registered agencies (2016) | 5,691 | Economic Census |
| Average revenue per agency | ¥15.11 million ($101K) | Census calculation |
| Revenue from individuals | ¥3.7 billion | Census breakdown |
| Revenue from corporations | ¥75.2 billion | Census breakdown |
| Other revenue | ¥7.0 billion | Census breakdown |
| Industry growth (2013-2021) | +1,000 agencies (~18%) | NPA statistics |

**Key insight:** Corporate clients (法人) account for 87.5% of industry revenue. This means B2B tooling has a natural buyer alignment — agencies already think in terms of business efficiency, not consumer convenience.

**Market size validation:** The plan's original estimate of "$350-700M/year" is confirmed. At ¥150/$, the 2016 census figure of ¥85.9 billion = $573M, squarely within the estimated range. Given industry growth since 2016 (6,600+ agencies in 2021 vs 5,691 in 2016), current market size likely exceeds ¥90 billion.

### 2.2 Investigation Types & Pricing

**Primary investigation categories** (ranked by frequency):

| Type | Japanese | Est. % of Cases | Typical Price Range |
|------|----------|-----------------|-------------------|
| Infidelity investigation | 浮気調査 / 不倫調査 | 70-80% | ¥100,000-1,000,000+ |
| Background check | 素行調査 / 身辺調査 | 10-15% | ¥50,000-500,000 |
| Missing persons | 人探し / 所在調査 | 5-8% | ¥100,000-800,000 |
| Marriage investigation | 結婚調査 / 婚前調査 | 3-5% | ¥80,000-400,000 |
| Corporate investigation | 企業調査 | 2-5% | ¥200,000-2,000,000+ |

**Investigator cost structure:**

| Component | Rate |
|-----------|------|
| Investigator hourly rate | ¥7,000-16,500/hour |
| Typical team size | 2-3 investigators |
| Typical uwaki case duration | 3-7 days × 6-8 hours/day |
| Labor cost per uwaki case | ¥252,000-2,772,000 |
| Equipment/vehicle costs | ¥30,000-100,000/case |
| Total case cost to agency | ¥300,000-3,000,000+ |
| Client-facing price | ¥100,000-1,000,000+ (varies by package) |

**Where our platform saves money:** If digital pre-investigation narrows the surveillance window from 5 days to 2 days, that saves ¥168,000-792,000 in investigator labor per case. Our Standard tier at ¥100,000/month pays for itself on the first case.

### 2.3 Divorce & Isharyou Context

**Why infidelity investigation is the dominant case type:**

| Metric | Value | Source |
|--------|-------|--------|
| Annual divorces in Japan | ~180,000-187,000 pairs | 厚生労働省 人口動態統計 |
| Divorce rate | 1.52 per 1,000 (2023) | Statista |
| Isharyou (慰謝料) average for infidelity | ¥1,000,000-3,000,000 | Legal practice averages |
| Isharyou maximum (court-awarded) | ¥5,000,000+ | Exceptional cases |
| % of divorces involving infidelity claims | ~25-30% | Legal industry estimates |

**Investigation → legal pipeline:** Client suspects infidelity → hires detective agency → agency produces 調査報告書 with photographic evidence → client takes report to lawyer → lawyer files isharyou claim → court awards damages based on evidence quality. **The quality and completeness of the investigation report directly determines the financial outcome.** This is why our Evidence Studio module is so valuable — it automates production of court-grade reports.

### 2.4 Social Media Landscape (Japan)

**X (Twitter) in Japan — the OSINT goldmine:**

| Metric | Value | Source |
|--------|-------|--------|
| X/Twitter users in Japan | 70+ million (Feb 2025) | DataReportal |
| Penetration rate | ~49-58% of population | MIC / DataReportal |
| Japan's global rank for X usage | #2 (after USA) | Multiple sources |
| Average daily usage | High (cultural integration) | Industry reports |

**Why X matters for investigation:** Japanese culture has deeply integrated Twitter/X into daily communication. Unlike Western markets where Instagram or TikTok dominate casual sharing, Japanese users frequently post location-tagged tweets, replies to local businesses, and real-time status updates. Public tweet analysis can reveal behavioral patterns (regular Thursday evening tweets from Shibuya = potential surveillance window).

**Other platforms:**

| Platform | Japan Users | OSINT Value |
|----------|------------|-------------|
| LINE | 96M+ MAU | Private (no OSINT value) |
| YouTube | 78M+ | Limited (public comments only) |
| Instagram | 50M+ | Moderate (public profiles, location tags) |
| Facebook | 26M+ | Moderate (public posts, check-ins, declining) |
| TikTok | 28M+ | Low-moderate (public profiles) |

---

## 3. Target Customer Profiles

### 3.1 Top 10 Agency Chains (Verified March 2026)

#### 1. ガルエージェンシー (Galu Agency)
| Field | Detail |
|-------|--------|
| Website | https://www.galu.co.jp/ (LIVE ✓) |
| Offices | **100 offices** (nationwide franchise network; was 124 in 2011) |
| Staff | **800 employees** (group-wide) |
| HQ | Tokyo (Ginza, Chuo-ku) + Osaka + Nagoya |
| Founded | 1980 |
| Model | Franchise (ガルエージェンシー探偵学校 trains new franchisees) |
| Tech posture | Low — no notable tech investments mentioned |
| Enterprise fit | **Highest potential** — largest network, franchise model means centralized software adoption could deploy to 100 offices simultaneously |
| Key contact path | Franchise HQ in Ginza |

#### 2. 原一探偵事務所 (Haraichi Detective Agency)
| Field | Detail |
|-------|--------|
| Website | https://www.haraichi.co.jp/ (LIVE ✓) |
| Offices | **24 offices** + additional free consultation rooms nationwide |
| Staff | 200+ (estimated) |
| HQ | Kawagoe, Saitama (本社) |
| Founded | 1977 |
| Model | Direct-operated chain |
| Tech posture | **Highest in industry** — known for drone deployment, remote surveillance vehicles, custom-built investigation equipment |
| Enterprise fit | **Best first customer candidate** — tech-forward culture, documented pattern of investing in new investigation technology, member of CII (Council of International Investigators) |
| Key offices | Kawagoe HQ, Shinjuku, Kanda (Tokyo), Yokohama, Shibuya, Ikebukuro, Osaka, Nagoya, Fukuoka, Sapporo |
| Notable | Has additional consultation rooms beyond the 24 listed offices |

#### 3. さくら幸子探偵事務所 (Sakura Sachiko Detective Agency)
| Field | Detail |
|-------|--------|
| Website | https://www.sakurasachiko.jp/ (LIVE ✓) |
| Offices | **31 offices** nationwide |
| Staff | 11-50 (Indeed listing; likely understates field investigators) |
| HQ | Sapporo, Hokkaido (本社) |
| Corporate entity | 株式会社アイ・アイ・エス |
| Model | Direct-operated chain |
| Tech posture | Moderate — standard digital presence |
| Enterprise fit | Good — significant national footprint, Hokkaido-based (less competitive market for tech vendors) |
| Key offices | Sapporo HQ, Tokyo HQ, Yokohama, Sendai, Nagoya, Osaka, Fukuoka, Okinawa (30 listed on website) |

#### 4. HAL探偵社 (HAL Detective Agency)
| Field | Detail |
|-------|--------|
| Website | https://hal-tanteisya.com/ (LIVE ✓) |
| Offices | **32 offices** (verified from website, March 2026) |
| Staff | Not publicly disclosed |
| HQ | Tokyo (Shinjuku area) |
| Model | Direct-operated chain |
| Tech posture | Moderate |
| Enterprise fit | Good — large office network, strong Kanto/Kansai presence |
| Key offices | Shinjuku Main, Yurakucho, Ikebukuro, Shibuya, Ebisu (Tokyo); Nagoya, Osaka Umeda, Osaka Namba, Kobe, Kyoto, Fukuoka |

#### 5. MR探偵事務所 (MR Detective Agency)
| Field | Detail |
|-------|--------|
| Website | https://www.tantei-mr.co.jp/ (LIVE ✓) |
| Offices | **14 consultation rooms** |
| Staff | Not publicly disclosed |
| HQ | Shinjuku Island Tower 4F, Tokyo |
| Founded | ~2003 (23 years in operation) |
| Model | Direct-operated |
| Tech posture | **High** — advertises "最新ハイテク調査" (latest high-tech investigation), specialized cameras, undisclosed equipment |
| Enterprise fit | Moderate — smaller but tech-receptive |
| Key metrics | 300,000+ total consultations, 96.6% success rate (Apr 2024-Oct 2025) |
| Association | Japan Investigation Industry Association member |

#### 6. 総合探偵社AMUSE (AMUSE Detective Agency)
| Field | Detail |
|-------|--------|
| Website | https://tantei-amuse.co.jp/ (LIVE ✓) |
| Offices | **9 offices** (Tokyo, Osaka, Sendai, Fukuoka, Nagoya, Sapporo, Chiba, Yokohama, Saitama) |
| Staff | Not publicly disclosed |
| HQ | Shibuya, Tokyo |
| Corporate entity | 株式会社MIRAI探偵社 (MIRAI Detective Corp.) |
| Founded | Police OBs (former officers) |
| Model | Direct-operated |
| Tech posture | **High** — real-time LINE/email reporting to clients during surveillance |
| Enterprise fit | Good — small but digitally mature workflow, real-time client communication already in place |
| All offices public safety commission certified | ✓ |

#### 7. ラビット探偵社 (Rabbit Detective Agency)
| Field | Detail |
|-------|--------|
| Website | https://rabbit-tantei.com/ (LIVE ✓) |
| Offices | **13 offices** |
| Staff | Not publicly disclosed |
| HQ | Minato-ku (Hamamatsucho), Tokyo |
| Founded | 2011 (youngest major chain) |
| Model | Direct-operated |
| Tech posture | Moderate-high — Google Analytics, GTM, Microsoft Clarity tracking |
| Enterprise fit | Good — youngest chain, likely most receptive to new technology |
| Key metrics | 100,000+ consultations, 95.3% success rate, 98.1% satisfaction |
| Key offices | Tokyo HQ, Shinjuku, Yokohama, Chiba, Saitama, Shizuoka, Nagoya, Osaka, Kobe, Sapporo, Fukuoka |
| Notable | Sends real-time LINE updates during surveillance |

#### 8-10. Additional Targets

| Agency | Offices | Website | Notes |
|--------|---------|---------|-------|
| 総合探偵社TS | 8+ | https://www.tanteisha-ts.co.jp/ | Verify |
| 響・Agent | 5+ | https://hibiki-tantei.com/ | Verify |
| ISM調査事務所 | 3+ | https://ism-tantei.com/ | Verify |

### 3.2 Buyer Persona

**Primary buyer:** Agency owner/CEO (社長) or operations director (業務部長)

**Decision-making process:** Japanese B2B purchases follow ringi (稟議) consensus decision-making. Expect:
- 3-6 month sales cycle for enterprise
- Multiple in-person meetings (meishi exchange, relationship building)
- Demo to field investigators as well as management
- Pilot period (3 months free/discounted) before contract
- Japanese-speaking representative **mandatory** for enterprise sales

**Pain points we solve:**
1. "We're wasting investigator hours on surveillance that produces nothing"
2. "Our report generation takes too long and is inconsistent across investigators"
3. "We can't coordinate cases across our offices efficiently"
4. "Competitor agencies are growing faster — we need a technology advantage"

---

## 4. Product Design

### 4.1 Module 1: Digital Reconnaissance (デジタル偵察)

#### Public Social Media Scanning

**X/Twitter Monitoring:**

X API access is now available as pay-per-use (launched February 6, 2026). The Basic tier ($200/month) remains available alongside the new consumption-based model. **Important cost note:** Pay-per-use is only cheaper for light usage (<40K-50K combined monthly operations). At equivalent Basic tier volume (15K post reads + 50K user lookups), pay-per-use would cost ~$1,325/month vs $200 fixed. **Recommendation: Use the Basic tier ($200/mo) for predictable costs.**

| Operation | Cost | Notes |
|-----------|------|-------|
| Read a post | $0.005/post | Includes full tweet data |
| User profile lookup | $0.010/user | Profile info, followers |
| Create a post | $0.010/post | Not needed for monitoring |
| DM reads | $0.010/DM | Not applicable (private) |
| Monthly cap | 2M post reads | ~$10,000 at cap |

**Cost projection for our platform:**
- Per active investigation: ~200-500 post reads + 10-20 user lookups = $1.00-$2.70/investigation
- 100 concurrent investigations: $100-$270/month X API cost
- With spending cap set at $500/month: sufficient for all but largest agencies

**Features:**
- Track target's public posts, replies, likes, follower/following changes
- Detect new accounts followed, pattern changes, location-tagged tweets
- Historical tweet analysis for behavioral patterns (limited to 7 days on pay-per-use; full archive requires higher spend)
- Keyword and hashtag monitoring

**Instagram Public Profile Monitoring:**
- Post frequency, tagged locations, tagged people, follower changes
- Story highlights (public), Reels engagement
- Implementation: Headless browser scraping via Playwright
- Maintenance: doc_ids change every 2-4 weeks (ongoing engineering cost)
- Cost: Residential proxy rotation, $100-300/month

**Other Platforms:**
- Facebook public posts and check-ins (declining relevance in Japan)
- TikTok public profiles (growing but lower OSINT value)
- Google Maps reviews and public check-ins (people forget these are public)

#### Face Matching

**Technology:** InsightFace / ArcFace (self-hosted)

| Component | Detail |
|-----------|--------|
| Detection | RetinaFace (included in InsightFace) |
| Alignment | 2D alignment pipeline |
| Embedding | ArcFace, 512-dimensional vector |
| Similarity metric | Cosine similarity |
| Match threshold | 0.6 = possible match, 0.7+ = likely match |
| Storage | PostgreSQL with pgvector extension |
| GPU requirement | NVIDIA GPU with 4+ GB VRAM (T4, A10G, or RTX 3060+) |

**Current status of InsightFace (March 2026):**
- Latest PyPI release: **0.7.3** (released 2022, 3+ years without update)
- Known issue: uses deprecated `np.int` (fixed in master branch, not in PyPI)
- **License concern:** InsightFace code is MIT-licensed, but **pre-trained model weights are restricted to non-commercial research use**
- **Mitigation:** Train custom ArcFace model on commercially-licensed dataset (MS1MV2 or WebFace260M) using InsightFace training code (MIT-licensed), or use AdaFace (CVPR 2022, MIT license, open weights)

**Alternative: AdaFace**
- Quality-adaptive margin for face recognition (CVPR 2022 Oral)
- Better performance on low-quality images (common in surveillance)
- Open-source with MIT license: https://github.com/mk-minchul/AdaFace
- New official repository: CVLFace, supporting ViT architectures
- **Recommended for production deployment** due to cleaner licensing

**Training data: FaceID-6M (2025)**
- Large-scale open-source dataset: 6 million high-quality face-image pairs (ArXiv March 2025)
- Addresses Asian face underrepresentation (CASIA-WebFace contains only 2.6% Asian faces)
- Available on Hugging Face: https://huggingface.co/datasets/Super-shuhe/FaceID-6M
- Enables custom model training with permissive licensing and better Asian face accuracy
- **Consider fine-tuning AdaFace on FaceID-6M for optimal Asian face performance**

**Face search against public web:**
- FaceCheck.id API: ~$0.30/search, progressive pricing for volume
  - API documentation available at https://facecheck.id/
  - $100 developer credits to start
  - Testing mode available (100K faces, no credit deduction)
- PimEyes API: Progressive pricing, $100 developer credits
  - Consumer plans: $14.99-$299.99/month
  - Business/API: Custom pricing
- **Important:** Both services are Western-face-biased. Self-hosted Asian-face-optimized model is our differentiator.

**Workflow:**
1. Investigator uploads target photo + suspected affair partner photo
2. System detects faces → aligns → extracts embeddings
3. Embeddings stored in pgvector for future matching
4. Similarity search against all case photos
5. Optional: web search via FaceCheck.id API for public matches
6. All results require human investigator review before case inclusion
7. Full audit trail of all searches and results

#### Public Records Integration (Japan-Specific)

**1. 法人番号公表システム Web-API (National Tax Agency Corporate Number API)**
| Field | Detail |
|-------|--------|
| URL | https://www.houjin-bangou.nta.go.jp/webapi/ |
| Cost | Free |
| Auth | Application ID (申請制) |
| Rate limits | Not publicly disclosed (403 error on excess; auto-recovers) |
| Data returned | Corporate number, name, address, registration/change dates |
| Max results per request | 2,000 records |
| API versions | v1.0 through v4.0 |
| Use case | Identify target's business connections, verify corporate relationships |

**2. 官報 (National Gazette / Kanpou)**
| Field | Detail |
|-------|--------|
| URL | https://kanpou.npb.go.jp/ |
| Online access | Free for last 30 days; paid archive (インターネット版官報) |
| API | No official API; web scraping of search.npb.go.jp possible |
| Relevant notice types | Bankruptcy (破産), dissolution (解散), name changes, civil law notices (相続限定承認) |
| Use case | Discover financial distress, corporate changes, legal proceedings |

**Notice categories in 官報:**
- 会社関係公告 (Corporate notices): mergers, capital reduction, dissolution, liquidation
- 民法等関係 (Civil law): inheritance acceptance limits, creditor notices
- 破産手続開始 (Bankruptcy proceedings): individual and corporate bankruptcy
- 公益法人関係 (Public interest corporations): mergers, dissolutions

**3. 登記情報提供サービス (Registry Information Service)**
| Field | Detail |
|-------|--------|
| URL | https://www1.touki.or.jp/ |
| Cost | ¥332-¥397 per search (property/corporate registry) |
| API | Currently web-only; Digital Agency (デジタル庁) developing API for March 2026 Base Registry |
| Data | Property ownership, corporate officers, registered addresses |
| Use case | Verify property ownership, identify corporate officers, find registered addresses |

**Base Registry update (March 2026):** Japan's Digital Agency is building a corporate Base Registry using corporate numbers (法人番号) as identifiers. The system is targeting March 2026 for initial launch, with full API access for private companies under consideration. This could eventually provide programmatic access to 登記 data.

**4. Google Maps Places API**
| Field | Detail |
|-------|--------|
| Reviews accessible | Yes, via Places API (Place Details endpoint) |
| Pricing | Enterprise + Atmosphere SKU (reviews field) |
| Japan restrictions | None for Places API (transit routing is restricted, not places) |
| Terms of service | Prohibit scraping; must use official API. Cannot cache/export reviews. |
| Use case | Find target's public reviews (restaurant reviews, hotel reviews, location history) |

#### Digital Footprint Mapping

**Unified target profile view:**
- Aggregate all discovered public information into a single timeline
- Location heat map from public check-ins, tagged posts, reviewed locations
- Relationship graph showing connections between target and discovered associates
- Activity pattern analysis (day-of-week, time-of-day patterns)
- "Optimal surveillance window" recommendation engine

### 4.2 Module 2: Case Management (案件管理)

#### Client Intake (依頼受付)

**Structured intake form (Japanese):**

```
依頼受付フォーム
━━━━━━━━━━━━━━━━━━━━
■ 依頼者情報
  氏名：________________
  フリガナ：______________
  連絡先（電話）：__________
  連絡先（メール）：________
  連絡先（LINE ID）：______
  希望連絡手段：□電話 □メール □LINE
  連絡可能時間帯：________

■ 対象者情報
  氏名：________________
  フリガナ：______________
  生年月日：_____年___月___日
  住所：________________
  勤務先：_______________
  勤務先住所：____________
  車両情報：メーカー_______ 車種_______ 色_______ ナンバー_______
  携帯番号（判明分）：______
  SNSアカウント（判明分）：______

■ 調査目的
  □ 浮気の事実確認のみ
  □ 裁判用証拠の取得（慰謝料請求用）
  □ 浮気相手の身元特定
  □ その他：______________

■ 現在の状況
  浮気を疑う理由：________
  怪しい曜日・時間帯：______
  浮気相手の心当たり：□有 □無
  これまでの調査経験：□有 □無

■ 写真添付
  対象者の顔写真：[アップロード]
  浮気相手（判明時）：[アップロード]
  車両写真：[アップロード]
```

**Automated features:**
- Face embedding auto-generated on photo upload
- Vehicle plate OCR extraction
- Address geocoding for map display
- Automated quote generation based on investigation scope and duration

#### Investigation Workflow (調査ワークフロー)

**Case status flow:**
```
相談中 (Consulting)
  ↓
受任 (Accepted)
  ↓
調査準備中 (Preparing)
  ↓
デジタル偵察中 (Digital Recon)
  ↓
現場調査中 (Field Investigation)
  ↓
報告書作成中 (Report Generation)
  ↓
報告完了 (Delivered)
  ↓
請求中 (Invoicing)
  ↓
完了 (Closed)
```

**Features:**
- Surveillance schedule builder (drag-and-drop calendar)
- Investigator assignment (skill matching, availability, location proximity)
- Real-time status tracking (active surveillance, standby, reporting)
- Multi-investigator shared case view with real-time notes
- GPS timeline import (CSV/GPX from common GPS trackers)
- Mobile-responsive field investigator view (photo upload, timestamped notes, GPS tagging)

#### Multi-Office Coordination (多拠点連携)

Critical for chains like Galu (100 offices), Sakura Sachiko (31 offices), HAL (32 offices):

- Centralized case database across all offices
- Case transfer between offices when target travels
- Cross-office investigator availability view
- Unified reporting and analytics across the chain
- Role-based access: agency admin → office manager → lead investigator → field investigator

#### Financial Tracking (経費管理)

- Billable hours per investigator per case
- Equipment/vehicle/travel cost allocation
- Quote vs. actual cost comparison
- Invoice generation (PDF, compatible with Japanese accounting software)
- Monthly/quarterly revenue and utilization reports per office

### 4.3 Module 3: Evidence Studio (証拠スタジオ)

#### Evidence Capture (証拠取得)

**Tamper-proofing:**
- SHA-256 hash generated for every evidence item at capture time
- Hash stored in immutable audit log
- Any modification detected by hash mismatch
- Chain of custody log: who captured, when, where, on what device, who accessed

**Evidence types supported:**
- Photos (JPEG, PNG, HEIC, RAW) with EXIF data extraction
- Videos (MP4, MOV) with metadata preservation
- Screenshots with URL, timestamp, page title, capture device
- PDF documents
- GPS track files (GPX, KML, CSV)
- Audio recordings (WAV, MP3) where legally captured

**Batch import:**
- Drag-and-drop upload of entire SD card/phone camera roll
- Automatic EXIF extraction (date, time, GPS coordinates, camera model)
- Auto-sort by timestamp
- Duplicate detection (by hash)

#### Report Generation (調査報告書自動作成)

**The 調査報告書 is the most critical deliverable.** It is what the client takes to their lawyer, and what the lawyer presents in court. Format matters.

**Auto-generated report structure:**

```
調査報告書
━━━━━━━━━━━━━━━━━━━━

【報告書番号】TIP-2026-XXXX
【調査期間】令和8年3月1日 ～ 令和8年3月5日
【調査目的】浮気調査（裁判証拠取得）
【依頼者】[依頼者名]
【対象者】[対象者名]
【調査担当】[主任調査員名]、[調査員名]

━━━━━━━━━━━━━━━━━━━━

■ 調査経過報告

【令和8年3月1日（金）】

18:00 対象者、勤務先（○○株式会社、東京都渋谷区○○）を退社。
      [写真1: 退社時の対象者 - ハッシュ値: abc123...]

18:15 対象者、渋谷駅方面へ徒歩移動。
      [写真2: 渋谷駅前の対象者 - ハッシュ値: def456...]

18:32 対象者、JR山手線にて新宿方面へ移動。

19:05 対象者、新宿駅東口にて不明女性（以下「A氏」）と合流。
      [写真3: A氏との合流 - ハッシュ値: ghi789...]

19:15 対象者とA氏、新宿区歌舞伎町○○ビル内の飲食店に入店。
      [写真4: 飲食店入店 - ハッシュ値: jkl012...]

21:40 対象者とA氏、飲食店を退店。腕を組んで歩行。
      [写真5: 退店時、腕を組む二人 - ハッシュ値: mno345...]

22:05 対象者とA氏、新宿区○○のホテル○○に入館。
      [写真6: ホテル入館 - ハッシュ値: pqr678...]

【令和8年3月2日（土）】

08:15 対象者とA氏、ホテル○○を退館。
      [写真7: ホテル退館 - ハッシュ値: stu901...]
      ※ 滞在時間：約10時間10分

━━━━━━━━━━━━━━━━━━━━

■ 調査結果概要

本調査の結果、対象者は令和8年3月1日、勤務先退社後に
不明女性（A氏）と合流し、飲食の後、ホテルに入館。
翌朝まで約10時間にわたり滞在していることが確認されました。

■ 証拠一覧（添付写真リスト）

| No. | 日時 | 内容 | ファイル名 | SHA-256ハッシュ値 |
|-----|------|------|-----------|-----------------|
| 1 | 3/1 18:00 | 退社 | IMG_001.jpg | abc123... |
| 2 | 3/1 18:15 | 渋谷駅前 | IMG_002.jpg | def456... |
...

■ 行動マップ

[自動生成の地図画像 - 移動経路と時刻をプロット]

━━━━━━━━━━━━━━━━━━━━
[探偵事務所ロゴ]
[探偵事務所名]
[探偵業届出番号]
[住所・連絡先]
```

**Automation features:**
- Minute-by-minute timeline auto-constructed from investigator notes + GPS data + photo EXIF timestamps
- Photo auto-inserted at correct chronological position with captions
- Map generation showing movements with timestamps (using Mapbox or Google Static Maps)
- Evidence index with hash values auto-generated
- PDF export in standard 調査報告書 format
- Customizable agency branding (logo, letterhead, contact info, 届出番号)
- Multiple export formats: PDF, DOCX (for lawyer editing)

#### Evidence Quality Scoring (証拠品質スコアリング)

**Automated checklist for isharyou claims:**

```
慰謝料請求用 証拠チェックリスト
━━━━━━━━━━━━━━━━━━━━

□ 顔の明確な識別（対象者）     ✓ 確認済み（写真1,3,5,6,7）
□ 顔の明確な識別（相手方）     ✓ 確認済み（写真3,5,6,7）
□ ホテル等への入館記録         ✓ 確認済み（写真6）
□ ホテル等からの退館記録       ✓ 確認済み（写真7）
□ 滞在時間の記録              ✓ 10時間10分
□ 日時の正確な記録            ✓ EXIF+GPS+調査員記録一致
□ 複数回の不貞行為の記録       ✗ 未取得（1回のみ）

判定：証拠力 ★★★★☆（4/5）
推奨：裁判では複数回の不貞行為が強く推奨されます。
      パターン分析に基づき、次の調査推奨日：3月8日（金）
```

### 4.4 Module 4: Intelligence Dashboard (インテリジェンスダッシュボード)

#### Pre-Investigation Intelligence

- Behavioral pattern analysis from digital footprint data
- "Optimal surveillance window" recommendations
  - Example: "対象者は毎週木曜19-22時に渋谷エリアからツイート。木曜18時に渋谷駅への配置を推奨。"
- Affair partner candidate identification from social connections
- Case risk/complexity scoring for new inquiries

#### Agency Analytics

- Case success rate by investigator, office, case type
- Average investigation duration and cost
- Revenue per case, per office, per month
- Investigator utilization rates (billable hours / available hours)
- Client acquisition channel tracking (web, phone, LINE, referral)
- Conversion funnel: consultation → contract → successful evidence → payment

---

## 5. Technical Architecture

### 5.1 Stack

| Layer | Technology | Rationale |
|-------|-----------|-----------|
| Frontend | Next.js 14+ (App Router), TypeScript, Tailwind CSS | SSR for fast initial load, React ecosystem, strong i18n support |
| UI Components | shadcn/ui + custom Japanese typography system | Clean, professional, accessible; Noto Sans JP for body, custom heading styles |
| Localization | next-intl | Full Japanese UI primary, English for future expansion |
| Backend API | Next.js API routes + tRPC | Type-safe end-to-end, co-located with frontend |
| Database | PostgreSQL 16+ (Neon or Supabase) | Relational data, row-level security, pgvector for embeddings |
| Vector Search | pgvector extension | Face embedding similarity search without separate vector DB |
| File Storage | Cloudflare R2 | Evidence files (photos, videos, documents). S3-compatible, zero egress fees |
| Face Recognition | AdaFace (self-hosted on GPU VPS) | Best open-source for low-quality images, MIT license, Asian face performance |
| Face Detection | RetinaFace (via InsightFace training code) | High accuracy face detection and alignment |
| Search | PostgreSQL full-text search + pg_trgm | Sufficient for case/evidence search at this scale |
| Auth | Supabase Auth or Auth.js (NextAuth) | SSO for enterprise, email/password for smaller agencies, MFA support |
| Hosting | Vercel (frontend) + Railway or Fly.io (backend/ML services) | Minimal ops overhead, auto-scaling |
| Mobile | PWA (Progressive Web App) initially, React Native if demand | Field investigator mobile access without app store approval |
| Payments | Stripe Japan (JPY) | Supports JPY billing, Japanese payment methods, invoice payment |
| Maps | Mapbox GL JS or Google Maps Static API | Movement visualization, location heat maps |
| PDF Generation | @react-pdf/renderer or Puppeteer | 調査報告書 PDF export |
| Monitoring | Sentry + Vercel Analytics | Error tracking, performance monitoring |
| CI/CD | GitHub Actions | Automated testing, deployment |

### 5.2 Face Recognition Pipeline

```
Photo Upload
    ↓
Face Detection (RetinaFace)
    ↓ [bounding boxes, landmarks]
Face Alignment (5-point alignment)
    ↓ [112x112 aligned face]
Embedding Extraction (AdaFace, ResNet-100)
    ↓ [512-dim float vector]
Store in PostgreSQL (pgvector)
    ↓
Similarity Search (cosine distance)
    ↓ [candidates with scores]
Human Review (investigator confirms/rejects)
    ↓
Case File Update
```

**GPU VPS options:**
| Provider | GPU | Monthly Cost | Notes |
|----------|-----|-------------|-------|
| Lambda Cloud | A10G | ~$150/mo | Good availability |
| Vast.ai | RTX 3090 | ~$100/mo | Spot pricing |
| RunPod | A10G | ~$120/mo | Serverless option |
| Railway | T4 | ~$100/mo | Integrated with stack |

### 5.3 OSINT Data Pipeline

```
Investigation Created
    ↓
Target Social Media Accounts Identified
    ↓
┌─────────────────────────┬──────────────────────┬─────────────────────┐
│ X/Twitter API           │ Instagram Scraper    │ Google Maps API     │
│ (Pay-per-use)          │ (Playwright)         │ (Places API)        │
│ $0.005/post read       │ Residential proxies  │ Enterprise SKU      │
│ 2M reads/month cap     │ doc_id maintenance   │ Reviews + places    │
└─────────────────────────┴──────────────────────┴─────────────────────┘
    ↓                          ↓                       ↓
    └──────────────────────────┴───────────────────────┘
                               ↓
                    Data Normalization Layer
                               ↓
                    Unified Timeline Format
                               ↓
                    PostgreSQL (with audit trail)
                               ↓
                    Pattern Analysis Engine
                               ↓
                    Intelligence Dashboard
```

### 5.4 Security Architecture

| Layer | Implementation |
|-------|---------------|
| Encryption at rest | AES-256 (database-level + R2 server-side encryption) |
| Encryption in transit | TLS 1.3 everywhere |
| Authentication | Supabase Auth with MFA (TOTP) |
| Authorization | Row-level security (RLS) in PostgreSQL |
| Role hierarchy | Super Admin → Agency Admin → Office Manager → Lead Investigator → Field Investigator |
| Audit logging | Immutable append-only audit table for all data access and modifications |
| Evidence integrity | SHA-256 hash at capture, verified on every access |
| Session management | JWT with short expiry (15 min) + refresh tokens |
| API rate limiting | Per-user rate limits to prevent abuse |
| Data retention | Configurable per agency; default 3 years, then automatic purge with audit log preserved |
| Backup | Daily automated PostgreSQL backups with point-in-time recovery |
| Penetration testing | Annual third-party pentest (target: before first enterprise customer) |
| SOC 2 | Target Type 2 certification by Year 2 |

---

## 6. Database Schema

### 6.1 Core Schema (PostgreSQL)

```sql
-- Extensions
CREATE EXTENSION IF NOT EXISTS "uuid-ossp";
CREATE EXTENSION IF NOT EXISTS "pgvector";
CREATE EXTENSION IF NOT EXISTS "pg_trgm";

-- ============================================================
-- ORGANIZATIONS & USERS
-- ============================================================

CREATE TABLE organizations (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    name TEXT NOT NULL,                          -- 探偵事務所名
    name_kana TEXT,                              -- フリガナ
    license_number TEXT NOT NULL,                -- 探偵業届出証明書番号
    license_verified_at TIMESTAMPTZ,
    plan TEXT NOT NULL DEFAULT 'standard',       -- standard, professional, enterprise
    logo_url TEXT,
    primary_contact_email TEXT NOT NULL,
    primary_contact_phone TEXT,
    billing_address JSONB,                       -- {postal_code, prefecture, city, street, building}
    stripe_customer_id TEXT,
    settings JSONB DEFAULT '{}',                 -- Agency-level settings
    created_at TIMESTAMPTZ NOT NULL DEFAULT NOW(),
    updated_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
);

CREATE TABLE offices (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    organization_id UUID NOT NULL REFERENCES organizations(id),
    name TEXT NOT NULL,                          -- 支店名
    address JSONB NOT NULL,                      -- {postal_code, prefecture, city, street, building}
    phone TEXT,
    latitude DOUBLE PRECISION,
    longitude DOUBLE PRECISION,
    is_headquarters BOOLEAN DEFAULT FALSE,
    created_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
);

CREATE TABLE users (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    organization_id UUID NOT NULL REFERENCES organizations(id),
    office_id UUID REFERENCES offices(id),
    email TEXT UNIQUE NOT NULL,
    name TEXT NOT NULL,
    name_kana TEXT,
    role TEXT NOT NULL CHECK (role IN ('super_admin', 'agency_admin', 'office_manager', 'lead_investigator', 'field_investigator')),
    phone TEXT,
    avatar_url TEXT,
    is_active BOOLEAN DEFAULT TRUE,
    last_login_at TIMESTAMPTZ,
    created_at TIMESTAMPTZ NOT NULL DEFAULT NOW(),
    updated_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
);

-- ============================================================
-- CLIENTS & CASES
-- ============================================================

CREATE TABLE clients (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    organization_id UUID NOT NULL REFERENCES organizations(id),
    name TEXT NOT NULL,                          -- 依頼者氏名
    name_kana TEXT,
    email TEXT,
    phone TEXT,
    line_id TEXT,
    preferred_contact TEXT CHECK (preferred_contact IN ('phone', 'email', 'line')),
    contact_hours TEXT,                          -- 連絡可能時間帯
    address JSONB,
    notes TEXT,
    acquisition_channel TEXT,                    -- web, phone, line, referral, walk_in
    created_at TIMESTAMPTZ NOT NULL DEFAULT NOW(),
    updated_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
);

CREATE TABLE cases (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    organization_id UUID NOT NULL REFERENCES organizations(id),
    office_id UUID NOT NULL REFERENCES offices(id),
    client_id UUID NOT NULL REFERENCES clients(id),
    case_number TEXT UNIQUE NOT NULL,            -- TIP-2026-XXXX
    case_type TEXT NOT NULL CHECK (case_type IN (
        'uwaki',          -- 浮気調査
        'soko',           -- 素行調査
        'hitosagashi',    -- 人探し
        'kekkon',         -- 結婚調査
        'kigyou',         -- 企業調査
        'other'           -- その他
    )),
    status TEXT NOT NULL DEFAULT 'consulting' CHECK (status IN (
        'consulting',     -- 相談中
        'accepted',       -- 受任
        'preparing',      -- 調査準備中
        'digital_recon',  -- デジタル偵察中
        'field_active',   -- 現場調査中
        'reporting',      -- 報告書作成中
        'delivered',      -- 報告完了
        'invoicing',      -- 請求中
        'closed',         -- 完了
        'cancelled'       -- キャンセル
    )),
    investigation_goal TEXT CHECK (investigation_goal IN (
        'confirmation_only',  -- 事実確認のみ
        'court_evidence',     -- 裁判証拠取得
        'partner_id',         -- 相手方特定
        'comprehensive'       -- 総合調査
    )),
    quoted_amount INTEGER,                       -- 見積額（円）
    actual_amount INTEGER,                       -- 実費（円）
    start_date DATE,
    end_date DATE,
    priority TEXT DEFAULT 'normal' CHECK (priority IN ('low', 'normal', 'high', 'urgent')),
    notes TEXT,
    metadata JSONB DEFAULT '{}',
    created_at TIMESTAMPTZ NOT NULL DEFAULT NOW(),
    updated_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
);

-- ============================================================
-- TARGETS & DIGITAL PROFILES
-- ============================================================

CREATE TABLE targets (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    case_id UUID NOT NULL REFERENCES cases(id) ON DELETE CASCADE,
    name TEXT NOT NULL,
    name_kana TEXT,
    date_of_birth DATE,
    address JSONB,
    employer TEXT,
    employer_address JSONB,
    vehicle_info JSONB,                          -- {make, model, color, plate_number}
    phone TEXT,
    physical_description TEXT,
    notes TEXT,
    created_at TIMESTAMPTZ NOT NULL DEFAULT NOW(),
    updated_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
);

CREATE TABLE target_photos (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    target_id UUID NOT NULL REFERENCES targets(id) ON DELETE CASCADE,
    file_url TEXT NOT NULL,                      -- R2 URL
    file_hash TEXT NOT NULL,                     -- SHA-256
    face_embedding VECTOR(512),                  -- AdaFace embedding
    embedding_model TEXT DEFAULT 'adaface_r100',
    is_primary BOOLEAN DEFAULT FALSE,
    captured_at TIMESTAMPTZ,
    uploaded_by UUID REFERENCES users(id),
    created_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
);

CREATE TABLE social_media_accounts (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    target_id UUID NOT NULL REFERENCES targets(id) ON DELETE CASCADE,
    platform TEXT NOT NULL CHECK (platform IN ('twitter', 'instagram', 'facebook', 'tiktok', 'google', 'other')),
    username TEXT,
    profile_url TEXT,
    is_verified BOOLEAN DEFAULT FALSE,           -- Verified by investigator
    is_monitoring_active BOOLEAN DEFAULT FALSE,
    last_checked_at TIMESTAMPTZ,
    metadata JSONB DEFAULT '{}',
    created_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
);

CREATE TABLE social_media_activity (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    account_id UUID NOT NULL REFERENCES social_media_accounts(id) ON DELETE CASCADE,
    activity_type TEXT NOT NULL,                  -- post, reply, like, follow, unfollow, location_tag
    content_text TEXT,
    media_urls TEXT[],
    location_name TEXT,
    location_lat DOUBLE PRECISION,
    location_lng DOUBLE PRECISION,
    activity_timestamp TIMESTAMPTZ NOT NULL,
    raw_data JSONB,                              -- Full API response
    created_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
);

-- ============================================================
-- INVESTIGATIONS & FIELD WORK
-- ============================================================

CREATE TABLE investigation_sessions (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    case_id UUID NOT NULL REFERENCES cases(id) ON DELETE CASCADE,
    session_date DATE NOT NULL,
    start_time TIMESTAMPTZ,
    end_time TIMESTAMPTZ,
    status TEXT DEFAULT 'planned' CHECK (status IN ('planned', 'active', 'completed', 'cancelled')),
    location_description TEXT,
    notes TEXT,
    created_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
);

CREATE TABLE investigator_assignments (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    session_id UUID NOT NULL REFERENCES investigation_sessions(id) ON DELETE CASCADE,
    user_id UUID NOT NULL REFERENCES users(id),
    role TEXT DEFAULT 'field' CHECK (role IN ('lead', 'field', 'support', 'driver')),
    hourly_rate INTEGER,                         -- 時間単価（円）
    hours_worked DECIMAL(5,2),
    notes TEXT,
    created_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
);

CREATE TABLE field_notes (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    session_id UUID NOT NULL REFERENCES investigation_sessions(id) ON DELETE CASCADE,
    user_id UUID NOT NULL REFERENCES users(id),
    timestamp TIMESTAMPTZ NOT NULL,
    note_text TEXT NOT NULL,
    location_lat DOUBLE PRECISION,
    location_lng DOUBLE PRECISION,
    location_name TEXT,
    created_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
);

-- ============================================================
-- EVIDENCE
-- ============================================================

CREATE TABLE evidence_items (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    case_id UUID NOT NULL REFERENCES cases(id) ON DELETE CASCADE,
    session_id UUID REFERENCES investigation_sessions(id),
    evidence_type TEXT NOT NULL CHECK (evidence_type IN (
        'photo', 'video', 'screenshot', 'document', 'audio', 'gps_track'
    )),
    file_url TEXT NOT NULL,                      -- R2 URL
    file_hash TEXT NOT NULL,                     -- SHA-256 at capture
    file_size_bytes BIGINT,
    mime_type TEXT,
    original_filename TEXT,
    -- EXIF / metadata
    captured_at TIMESTAMPTZ,
    capture_device TEXT,
    capture_lat DOUBLE PRECISION,
    capture_lng DOUBLE PRECISION,
    exif_data JSONB,
    -- For screenshots
    source_url TEXT,
    page_title TEXT,
    -- Face data
    face_embeddings JSONB,                       -- Array of {bbox, embedding_id}
    -- Status
    quality_score INTEGER CHECK (quality_score BETWEEN 1 AND 5),
    description TEXT,
    is_key_evidence BOOLEAN DEFAULT FALSE,
    -- Audit
    uploaded_by UUID NOT NULL REFERENCES users(id),
    created_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
);

CREATE TABLE evidence_chain (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    evidence_id UUID NOT NULL REFERENCES evidence_items(id) ON DELETE CASCADE,
    action TEXT NOT NULL CHECK (action IN (
        'captured', 'uploaded', 'viewed', 'downloaded', 'exported',
        'added_to_report', 'hash_verified', 'hash_mismatch'
    )),
    performed_by UUID NOT NULL REFERENCES users(id),
    performed_at TIMESTAMPTZ NOT NULL DEFAULT NOW(),
    ip_address TEXT,
    user_agent TEXT,
    notes TEXT
);

-- ============================================================
-- REPORTS
-- ============================================================

CREATE TABLE reports (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    case_id UUID NOT NULL REFERENCES cases(id) ON DELETE CASCADE,
    report_number TEXT UNIQUE NOT NULL,           -- TIP-RPT-2026-XXXX
    title TEXT NOT NULL DEFAULT '調査報告書',
    status TEXT DEFAULT 'draft' CHECK (status IN ('draft', 'review', 'approved', 'delivered')),
    content JSONB NOT NULL DEFAULT '{}',         -- Structured report content
    evidence_ids UUID[] DEFAULT '{}',            -- References to evidence_items
    generated_pdf_url TEXT,                      -- R2 URL for final PDF
    approved_by UUID REFERENCES users(id),
    approved_at TIMESTAMPTZ,
    delivered_at TIMESTAMPTZ,
    created_by UUID NOT NULL REFERENCES users(id),
    created_at TIMESTAMPTZ NOT NULL DEFAULT NOW(),
    updated_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
);

-- ============================================================
-- FACE MATCHING
-- ============================================================

CREATE TABLE face_search_requests (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    case_id UUID NOT NULL REFERENCES cases(id),
    requested_by UUID NOT NULL REFERENCES users(id),
    source_photo_id UUID REFERENCES target_photos(id),
    search_type TEXT NOT NULL CHECK (search_type IN ('internal', 'facecheck', 'pimeyes')),
    status TEXT DEFAULT 'pending' CHECK (status IN ('pending', 'processing', 'completed', 'failed')),
    results JSONB,                               -- Array of match results
    api_cost DECIMAL(10,4),                      -- Cost in USD
    created_at TIMESTAMPTZ NOT NULL DEFAULT NOW(),
    completed_at TIMESTAMPTZ
);

-- ============================================================
-- AUDIT LOG
-- ============================================================

CREATE TABLE audit_log (
    id BIGSERIAL PRIMARY KEY,
    organization_id UUID NOT NULL,
    user_id UUID,
    action TEXT NOT NULL,
    resource_type TEXT NOT NULL,                  -- 'case', 'evidence', 'report', etc.
    resource_id UUID,
    details JSONB,
    ip_address TEXT,
    user_agent TEXT,
    created_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
);

-- Immutable: no UPDATE or DELETE allowed on audit_log
-- Enforced via RLS policies and application-level constraints

-- ============================================================
-- INDEXES
-- ============================================================

CREATE INDEX idx_cases_org ON cases(organization_id);
CREATE INDEX idx_cases_status ON cases(status);
CREATE INDEX idx_cases_type ON cases(case_type);
CREATE INDEX idx_cases_number ON cases(case_number);
CREATE INDEX idx_evidence_case ON evidence_items(case_id);
CREATE INDEX idx_evidence_hash ON evidence_items(file_hash);
CREATE INDEX idx_target_photos_embedding ON target_photos
    USING ivfflat (face_embedding vector_cosine_ops) WITH (lists = 100);
CREATE INDEX idx_social_activity_account ON social_media_activity(account_id);
CREATE INDEX idx_social_activity_timestamp ON social_media_activity(activity_timestamp);
CREATE INDEX idx_audit_log_org ON audit_log(organization_id);
CREATE INDEX idx_audit_log_resource ON audit_log(resource_type, resource_id);
CREATE INDEX idx_field_notes_session ON field_notes(session_id);

-- Full-text search indexes
CREATE INDEX idx_cases_notes_fts ON cases USING gin(to_tsvector('japanese', coalesce(notes, '')));
CREATE INDEX idx_field_notes_fts ON field_notes USING gin(to_tsvector('japanese', note_text));
```

### 6.2 Row-Level Security (RLS) Policies

```sql
-- Users can only see data from their own organization
ALTER TABLE cases ENABLE ROW LEVEL SECURITY;

CREATE POLICY cases_org_isolation ON cases
    USING (organization_id = current_setting('app.organization_id')::UUID);

-- Field investigators can only see their assigned cases
CREATE POLICY cases_investigator_access ON cases
    FOR SELECT
    USING (
        current_setting('app.user_role') IN ('super_admin', 'agency_admin', 'office_manager')
        OR id IN (
            SELECT c.id FROM cases c
            JOIN investigation_sessions s ON s.case_id = c.id
            JOIN investigator_assignments a ON a.session_id = s.id
            WHERE a.user_id = current_setting('app.user_id')::UUID
        )
    );

-- Similar policies for all tables...
```

---

## 7. API Specification

### 7.1 API Overview

All APIs use tRPC for type-safe communication between Next.js frontend and backend. REST endpoints available for mobile/third-party integration.

**Base URL:** `https://api.tantei-platform.com/v1`
**Authentication:** Bearer token (JWT) in Authorization header
**Content-Type:** application/json
**Localization:** Accept-Language header (ja, en)

### 7.2 Core Endpoints

#### Cases API

```typescript
// tRPC Router Definition
const caseRouter = router({
  // List cases with filtering
  list: protectedProcedure
    .input(z.object({
      status: z.enum(['consulting', 'accepted', 'preparing', 'digital_recon',
                       'field_active', 'reporting', 'delivered', 'invoicing', 'closed']).optional(),
      case_type: z.enum(['uwaki', 'soko', 'hitosagashi', 'kekkon', 'kigyou', 'other']).optional(),
      office_id: z.string().uuid().optional(),
      page: z.number().min(1).default(1),
      limit: z.number().min(1).max(100).default(20),
    }))
    .query(async ({ ctx, input }) => { /* ... */ }),

  // Get single case with all relations
  get: protectedProcedure
    .input(z.object({ id: z.string().uuid() }))
    .query(async ({ ctx, input }) => { /* ... */ }),

  // Create new case
  create: protectedProcedure
    .input(z.object({
      client_id: z.string().uuid(),
      office_id: z.string().uuid(),
      case_type: z.enum(['uwaki', 'soko', 'hitosagashi', 'kekkon', 'kigyou', 'other']),
      investigation_goal: z.enum(['confirmation_only', 'court_evidence', 'partner_id', 'comprehensive']),
      notes: z.string().optional(),
    }))
    .mutation(async ({ ctx, input }) => { /* ... */ }),

  // Update case status
  updateStatus: protectedProcedure
    .input(z.object({
      id: z.string().uuid(),
      status: z.enum(['consulting', 'accepted', 'preparing', 'digital_recon',
                       'field_active', 'reporting', 'delivered', 'invoicing', 'closed', 'cancelled']),
    }))
    .mutation(async ({ ctx, input }) => { /* ... */ }),

  // Transfer case to another office
  transfer: protectedProcedure
    .input(z.object({
      id: z.string().uuid(),
      target_office_id: z.string().uuid(),
      notes: z.string().optional(),
    }))
    .mutation(async ({ ctx, input }) => { /* ... */ }),
});
```

#### Evidence API

```typescript
const evidenceRouter = router({
  // Upload evidence (returns presigned R2 URL)
  getUploadUrl: protectedProcedure
    .input(z.object({
      case_id: z.string().uuid(),
      filename: z.string(),
      mime_type: z.string(),
      file_size: z.number(),
    }))
    .mutation(async ({ ctx, input }) => { /* returns presigned URL */ }),

  // Confirm upload and create evidence record
  confirmUpload: protectedProcedure
    .input(z.object({
      case_id: z.string().uuid(),
      session_id: z.string().uuid().optional(),
      file_url: z.string().url(),
      file_hash: z.string(),         // Client-computed SHA-256
      evidence_type: z.enum(['photo', 'video', 'screenshot', 'document', 'audio', 'gps_track']),
      captured_at: z.date().optional(),
      capture_lat: z.number().optional(),
      capture_lng: z.number().optional(),
      description: z.string().optional(),
    }))
    .mutation(async ({ ctx, input }) => { /* ... */ }),

  // List evidence for a case
  list: protectedProcedure
    .input(z.object({
      case_id: z.string().uuid(),
      evidence_type: z.enum(['photo', 'video', 'screenshot', 'document', 'audio', 'gps_track']).optional(),
      page: z.number().min(1).default(1),
      limit: z.number().min(1).max(100).default(50),
    }))
    .query(async ({ ctx, input }) => { /* ... */ }),

  // Verify evidence integrity
  verify: protectedProcedure
    .input(z.object({ id: z.string().uuid() }))
    .query(async ({ ctx, input }) => {
      // Re-compute hash from R2 file, compare with stored hash
      // Return { verified: boolean, stored_hash, computed_hash }
    }),
});
```

#### Face Matching API

```typescript
const faceRouter = router({
  // Extract face embedding from uploaded photo
  extractEmbedding: protectedProcedure
    .input(z.object({
      photo_id: z.string().uuid(),
    }))
    .mutation(async ({ ctx, input }) => {
      // Send to GPU service for face detection + embedding extraction
      // Store embedding in target_photos.face_embedding
    }),

  // Search for similar faces within organization's cases
  searchInternal: protectedProcedure
    .input(z.object({
      source_photo_id: z.string().uuid(),
      threshold: z.number().min(0).max(1).default(0.6),
      limit: z.number().min(1).max(50).default(10),
    }))
    .query(async ({ ctx, input }) => {
      // pgvector cosine similarity search
      // Returns matches with confidence scores
    }),

  // Search via external API (FaceCheck.id)
  searchExternal: protectedProcedure
    .input(z.object({
      source_photo_id: z.string().uuid(),
      service: z.enum(['facecheck', 'pimeyes']),
    }))
    .mutation(async ({ ctx, input }) => {
      // Queue external API search
      // Deduct from organization's search quota
    }),
});
```

#### Report Generation API

```typescript
const reportRouter = router({
  // Generate report from case data
  generate: protectedProcedure
    .input(z.object({
      case_id: z.string().uuid(),
      template: z.enum(['standard', 'court', 'summary']).default('standard'),
      include_evidence_ids: z.array(z.string().uuid()).optional(),
      include_map: z.boolean().default(true),
    }))
    .mutation(async ({ ctx, input }) => {
      // Compile timeline from field_notes + evidence + GPS data
      // Generate PDF using report template
      // Upload to R2, return URL
    }),

  // Export report
  export: protectedProcedure
    .input(z.object({
      id: z.string().uuid(),
      format: z.enum(['pdf', 'docx']),
    }))
    .query(async ({ ctx, input }) => {
      // Return download URL
    }),
});
```

### 7.3 REST API (for mobile/third-party)

```
Authentication:
  POST   /v1/auth/login          → { access_token, refresh_token }
  POST   /v1/auth/refresh        → { access_token }

Cases:
  GET    /v1/cases               → List cases (paginated, filtered)
  POST   /v1/cases               → Create case
  GET    /v1/cases/:id           → Get case detail
  PATCH  /v1/cases/:id           → Update case
  PATCH  /v1/cases/:id/status    → Update case status

Evidence:
  POST   /v1/evidence/upload-url → Get presigned upload URL
  POST   /v1/evidence            → Confirm upload, create record
  GET    /v1/evidence/:case_id   → List evidence for case

Field Notes:
  POST   /v1/notes               → Create field note (with GPS)
  GET    /v1/notes/:session_id   → List notes for session

Reports:
  POST   /v1/reports/generate    → Generate report PDF
  GET    /v1/reports/:id         → Get report
  GET    /v1/reports/:id/pdf     → Download PDF
```

---

## 8. UI/UX Design

### 8.1 Design Principles

1. **Professional, not flashy** — Detective agencies serve serious clients dealing with personal crises. The UI must convey trust, competence, and discretion.
2. **Japanese-first** — All UI text, labels, help text, and error messages in natural Japanese. Not machine-translated.
3. **Information-dense** — Investigators need to see many data points simultaneously. Avoid excessive whitespace or oversimplified views.
4. **Mobile-functional** — Field investigators use phones. Critical functions (photo upload, note-taking, GPS tagging) must work on mobile.

### 8.2 Key Screen Wireframes

#### Dashboard (ダッシュボード)
```
┌─────────────────────────────────────────────────────────────┐
│ [Logo] 探偵インテリジェンスプラットフォーム    [検索] [通知] [ユーザー] │
├────────┬────────────────────────────────────────────────────┤
│        │                                                    │
│ メニュー │  本日の概要                                        │
│        │  ┌──────┐ ┌──────┐ ┌──────┐ ┌──────┐              │
│ ダッシュ │  │進行中  │ │本日予定│ │未読通知│ │今月売上│              │
│ ボード  │  │  12件 │ │  3件  │ │  5件  │ │¥2.4M │              │
│        │  └──────┘ └──────┘ └──────┘ └──────┘              │
│ 案件管理 │                                                    │
│        │  進行中の案件                                       │
│ 証拠    │  ┌───────────────────────────────────────────────┐ │
│ スタジオ │  │ TIP-2026-0042 │ 浮気調査 │ 現場調査中 │ 田中太郎  │ │
│        │  │ TIP-2026-0041 │ 素行調査 │ デジタル偵察│ 鈴木花子  │ │
│ デジタル │  │ TIP-2026-0039 │ 浮気調査 │ 報告書作成 │ 佐藤一郎  │ │
│ 偵察    │  └───────────────────────────────────────────────┘ │
│        │                                                    │
│ レポート │  調査員稼働状況                                     │
│        │  ┌───────────────────────────────────────────────┐ │
│ 分析    │  │ 山田 ████████████░░░░ 75% │ 現場調査中         │ │
│        │  │ 高橋 ██████████░░░░░░ 63% │ 待機中             │ │
│ 設定    │  │ 伊藤 ████████████████ 100%│ 現場調査中         │ │
│        │  └───────────────────────────────────────────────┘ │
└────────┴────────────────────────────────────────────────────┘
```

#### Case Detail (案件詳細)
```
┌─────────────────────────────────────────────────────────────┐
│ ← 案件一覧  TIP-2026-0042 浮気調査                          │
├─────────────────────────────────────────────────────────────┤
│ [タブ: 概要 | タイムライン | 証拠 | デジタル偵察 | 報告書 | 経費]  │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│ ■ 案件情報                        ■ 対象者情報              │
│ ステータス: [現場調査中 ▼]          氏名: 山田太郎            │
│ 種別: 浮気調査                     生年月日: 1985/04/12      │
│ 目的: 裁判証拠取得                  勤務先: ○○株式会社        │
│ 依頼者: [依頼者名]                 車両: トヨタ プリウス 白    │
│ 見積額: ¥500,000                   ナンバー: 品川 300 あ 1234 │
│ 開始日: 2026/02/25                                          │
│                                   [顔写真]                  │
│ ■ 担当調査員                                                │
│ 主任: 伊藤調査員                                            │
│ 補助: 高橋調査員、渡辺調査員                                 │
│                                                             │
│ ■ デジタル偵察サマリー                                      │
│ Twitter: @yamada_t (監視中)                                 │
│ 最終活動: 2h前 - 渋谷エリアからのツイート                     │
│ パターン: 木曜19-22時に渋谷エリア活動 (信頼度: 高)            │
│ 推奨調査日: 次の木曜 (3/5) 18:00~                           │
│                                                             │
│ ■ 証拠品質スコア                                            │
│ ████████░░ 4/5 (複数回の記録が不足)                          │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### 8.3 Japanese Copywriting (Key Screens)

**Login page:**
```
探偵インテリジェンスプラットフォーム

調査業務を、次のレベルへ。

メールアドレス: ________________
パスワード:     ________________

[ログイン]

パスワードをお忘れの方はこちら
```

**Onboarding:**
```
ようこそ、○○探偵事務所様

アカウントの初期設定を行います。

ステップ 1/4: 事務所情報の登録
ステップ 2/4: 支店情報の追加
ステップ 3/4: 調査員アカウントの作成
ステップ 4/4: 報告書テンプレートの設定
```

**Empty state (no cases):**
```
まだ案件が登録されていません

最初の案件を作成して、
プラットフォームの機能をお試しください。

[新規案件を作成]
```

---

## 9. Legal & Compliance

### 9.1 APPI Compliance Architecture

**Our legal position:** We are **委託先 (itakusaki / entrusted party / data processor)**, NOT the primary PIHBO (Personal Information Handling Business Operator). The detective agency is the PIHBO.

**Key APPI articles and our compliance:**

| APPI Article | Content | Our Compliance |
|--------------|---------|----------------|
| Art. 2, Para 1-2 | Defines "personal information" as information identifying living individuals, including individual identification codes | We process personal information only on agency instruction |
| Art. 2, Para 3 | Defines "sensitive personal data" including race, creed, medical history, criminal record | We do not independently collect sensitive data |
| Art. 17-18 | Purpose of use must be specified; no use beyond specified scope | Purpose limited to "investigation processing per agency's commission" |
| Art. 20 | Restrictions on acquiring sensitive personal information | Agency (not us) acquires; we process what they provide |
| Art. 23 | Security management measures (安全管理措置) required | AES-256 encryption, RLS, audit logging, MFA, SOC 2 target |
| Art. 24-25 | Employee and service provider supervision | Formal 委託契約 with each agency; security training for our staff |
| Art. 27, Para 1 | Prior consent required for third-party provision | We do not independently provide data to third parties |
| Art. 27, Para 5 | **Entrustment exception**: entrusted handlers not considered third parties | Our primary legal basis — we process on agency's behalf |
| Art. 178-179 | Penalties: up to 1 year imprisonment or ¥1M for individuals; ¥100M for entities | Compliance by design; legal review before launch |

**Face recognition (個人識別符号) — highest risk area:**

Facial data is classified as 個人識別符号 (individual identification codes) under APPI Art. 2. This means:
- Face embeddings are personal information by definition
- Collection requires purpose specification (Art. 17)
- Security management measures apply (Art. 23)
- Cross-border transfer restrictions may apply (Art. 28)

**Our mitigation:**
- Face matching only against photos the agency legally possesses OR public web images
- No mass face database — per-case processing only
- Agency validates all match results before case file inclusion
- Full audit trail of all face searches
- Data deleted after case closure per agency's retention policy
- Embeddings stored encrypted, access-logged

### 9.2 APPI Amendments Status (March 2026)

**2022 amendments (enacted, in force):**
- Expanded breach notification requirements
- Strengthened cross-border transfer rules
- Introduced pseudonymized data framework

**2025 proposed amendments (NOT YET ENACTED as of March 2026):**

The Personal Information Protection Commission (PPC) published an interim summary in 2024 proposing:
- **Administrative monetary penalties** (行政上の課徴金) — PPC examining frameworks but no consensus reached
- **Expanded biometric data protections** — strengthening rights to request suspension/deletion of biometric data
- **Statistical/AI processing exemptions** — processing without consent where rights unlikely infringed
- **Collective redress schemes** — under consideration

**Timeline:** Draft legislation expected to be published in 2025, with potential enactment in 2027.

**Impact on our product:** The proposed biometric data provisions could require us to honor individual deletion requests for face embeddings. Our architecture already supports this (per-case data with deletion capability). The administrative fines provision increases the penalty risk, making our robust compliance architecture a competitive advantage ("we keep you compliant").

Source: [IAPP Japan DPA Summary](https://iapp.org/news/a/japan-s-dpa-publishes-interim-summary-of-amendments-to-data-protection-regulations), [Clifford Chance Analysis](https://www.cliffordchance.com/insights/resources/blogs/talking-tech/en/articles/2024/06/amendments-to-the-act-on-the-protection-of-personal-information-set-for-2025.html)

### 9.3 Detective Business Act (探偵業法)

**Full name:** 探偵業の業務の適正化に関する法律 (Act on Regulation of Private Detective Services)
**Enacted:** 2006 (Law No. 60)
**Source:** https://laws.e-gov.go.jp/law/418AC1000000060

| Article | Content | Relevance |
|---------|---------|-----------|
| Art. 2 | Defines detective business: receiving requests from others to collect information about specific persons' location or conduct through interviews, surveillance, stakeouts, and similar methods | We are NOT a detective business — we provide software tools, not investigation services |
| Art. 4 | Registration requirement: must submit notification to Public Safety Commission before starting operations | Does not apply to software vendors |
| Art. 7 | Prohibition: detective must not allow results to be used for stalking, harassment, or discrimination; must not violate individual rights | We enforce this via ToS — agencies agree not to misuse our platform for prohibited purposes |
| Art. 9 | Confidentiality: persons in detective business must not disclose secrets learned in course of business | We maintain equivalent confidentiality obligations contractually |

**Key legal analysis:** Our product is a software tool, not a detective service. We do not conduct investigations, collect information about specific persons, or perform surveillance. We provide a platform that agencies use to manage their own lawful investigations. Under the Detective Business Act, we are not subject to registration requirements.

### 9.4 Winny Supreme Court Decision (2011)

**Case:** Supreme Court of Japan, Third Petty Bench, December 19, 2011
**Subject:** Developer of Winny P2P file-sharing software charged with aiding copyright infringement

**Holding:** The Supreme Court **acquitted** the developer, establishing that:

1. Software with **substantial lawful uses** (価値中立ソフト / "value-neutral software") does not make its developer liable for users' illegal acts
2. Criminal liability for aiding requires proof that the developer **specifically intended** to facilitate illegal use, not merely that they were aware illegal use was possible
3. The threshold for aiding liability is high: the developer must have promoted or encouraged the illegal use

**Relevance to our product:** Tantei Intelligence Platform is a business tool with substantial lawful uses (case management, evidence packaging, legal compliance). Even if an agency misused our platform, we would not be liable unless we specifically intended or encouraged the misuse. Our ToS, usage restrictions, and compliance features demonstrate the opposite intent.

### 9.5 JR East Facial Recognition Incident (2021)

**What happened:** JR East announced plans to use facial recognition cameras at stations to identify individuals with criminal records, triggering public backlash.

**Regulatory response:**
- No specific law prohibited the use, but public pressure forced JR East to withdraw the plan
- The PPC issued guidance emphasizing the need for transparency and purpose limitation when using facial recognition in public spaces
- This incident contributed to the ongoing discussion about strengthening biometric data protections in APPI amendments

**Relevance:** We are NOT deploying facial recognition in public spaces. Our system processes photos that agencies already legally possess or that are publicly available on the internet. However, the incident demonstrates Japanese public sensitivity to facial recognition, which we should acknowledge in our marketing and compliance materials.

### 9.6 Terms of Service Requirements

Our ToS with agencies must include:

1. **Registration verification:** Require submission of 探偵業届出証明書 at onboarding
2. **Prohibited uses:** Stalking, harassment, discrimination (per DBA Art. 7)
3. **Purpose limitation:** Platform use only for lawful investigations
4. **Data processing agreement (委託契約):** Formal agreement defining PIHBO/processor roles
5. **Indemnification:** Agency indemnifies us for misuse
6. **Termination rights:** We can terminate access on evidence of misuse
7. **Audit rights:** We retain right to audit agency's use of platform
8. **Data retention/deletion:** Agency controls retention period; we delete on request

### 9.7 Recommended: Japanese Legal Opinion

Before launch, obtain a formal legal opinion (意見書) from a Japanese IT law firm:

| Firm | Specialty | Est. Cost |
|------|----------|-----------|
| TMI Associates (TMI総合法律事務所) | IT law, data protection | ¥500K-1M |
| Nishimura & Asahi (西村あさひ) | Tech, IP, data privacy | ¥800K-1.5M |
| Anderson Mori & Tomotsune | Cross-border tech, APPI | ¥500K-1M |
| Mori Hamada & Matsumoto | Corporate, regulatory | ¥800K-1.5M |

**Value:** Legal insurance + sales tool ("Our product has been reviewed by [prestigious firm]").

---

## 10. Business Model & Pricing

### 10.1 Pricing Tiers

| Tier | Target | Monthly Price | Annual Price | Includes |
|------|--------|--------------|--------------|----------|
| **Standard** (スタンダード) | Small agency (1-5 investigators) | ¥100,000/mo ($660) | ¥1,080,000/yr ($7,200) — 10% discount | 5 seats, 50 OSINT searches/mo, 20 face matches/mo, all modules, email support |
| **Professional** (プロフェッショナル) | Mid-size agency (6-20 investigators) | ¥300,000/mo ($2,000) | ¥3,240,000/yr ($21,600) — 10% discount | 20 seats, 200 OSINT searches/mo, 100 face matches/mo, all modules, priority support, API access |
| **Enterprise** (エンタープライズ) | Large chain (20+ offices) | ¥800,000-2,000,000/mo ($5,300-$13,200) | Custom | Unlimited seats, unlimited searches, dedicated support, custom integrations, SLA, on-site training |

**Why these prices work:**
- A single uwaki case generates ¥100,000-1,000,000+ for the agency
- If our tool saves 2 days of investigator time: ¥112,000-264,000 saved (2 investigators × 8 hours × ¥7,000-16,500/hr)
- Standard tier pays for itself on the **first case per month**
- Galu (100 offices, ~800 staff) likely handles hundreds of cases/month; Enterprise at ¥2M/mo is <1% of estimated revenue

**Additional revenue:**
| Revenue Stream | Price | Notes |
|---------------|-------|-------|
| Implementation + training | ¥500,000 one-time ($3,300) | Per agency |
| Custom report templates | ¥200,000 one-time ($1,300) | Per template |
| Additional face searches | ¥500/search ($3.30) | Beyond tier quota |
| Additional OSINT searches | ¥300/search ($2.00) | Beyond tier quota |

### 10.2 Revenue Projections

**Year 1 (build + first customers):**

| Phase | Months | Activity |
|-------|--------|----------|
| Build MVP | 1-4 | Core development |
| Pilot | 5-8 | Free/discounted pilot with 1-2 agencies |
| Early revenue | 9-12 | First paying customers |

| Scenario | Customers (Mo 9-12) | Mix | Monthly Revenue | Annual (4 months) |
|----------|---------------------|-----|-----------------|-------------------|
| Conservative | 3 | 2 Standard + 1 Professional | ¥500,000 ($3,300) | $13,200 |
| Base | 5 | 3 Standard + 2 Professional | ¥900,000 ($6,000) | $24,000 |
| Optimistic | 7 | 4 Standard + 2 Pro + 1 Enterprise | ¥1,800,000 ($12,000) | $48,000 |

**Year 2 (growth):**
- Target: 10-20 agencies
- Revenue: ¥7.1-10M/month ($47K-$66K)
- Annual: $564K-$792K

**Year 3+ (market penetration):**
- Top 50 chains × 20% penetration = 10 enterprise accounts
- + 50 mid-size agencies
- Target: ¥15-25M/month ($100K-$165K)
- Annual: $1.2-2M ARR

### 10.3 Unit Economics

**Monthly operating costs (at Year 1 base scenario):**

| Category | Monthly Cost |
|----------|-------------|
| Infrastructure (Vercel, Neon/Supabase, R2) | $200-$400 |
| GPU VPS (face recognition) | $100-$150 |
| X/Twitter API (pay-per-use) | $100-$500 |
| Residential proxies (Instagram) | $100-$300 |
| Face search API (FaceCheck.id) | $100-$300 |
| Domain, email, tools | $50 |
| Legal entity maintenance | $100-$200 |
| **Total** | **$750-$1,900** |

**Gross margin at base scenario:**
- Revenue: $6,000/month
- Costs: ~$1,200/month
- **Gross profit: $4,800/month (80% margin)**

---

## 11. Corporate Structure

### Phase 1 (Year 1): US LLC Only

**Structure:** NM Holding LLC → Wyoming Operating LLC

| Item | Cost |
|------|------|
| WY LLC formation | ~$100 |
| NM LLC formation | ~$100 |
| WY annual report | $60 |
| Registered agent | $50-$100/yr |
| **Total Year 1** | **~$350** |
| **Annual maintenance** | **~$160** |

**Why this works initially:**
- Stripe Japan accepts US entities for JPY billing
- No physical Japan presence required for SaaS sales
- Software licensing is not subject to Detective Business Act registration
- Can invoice in JPY via Stripe

### Phase 2 (Year 2+): Japanese Entity

If traction justifies, establish a Japanese subsidiary:

| Entity Type | Formation Cost | Annual Cost | Benefit |
|-------------|---------------|-------------|---------|
| 合同会社 (GK/LLC) | ¥60,000 | Minimal | Japanese bank account, credibility, konbini payment |
| 株式会社 (KK/Corp) | ¥200,000+ | Audit/filing fees | Maximum credibility, potential for IT導入補助金 government subsidies |

**IT導入補助金 opportunity:** The Japanese government's IT Introduction Subsidy program subsidizes SME software purchases. If our product qualifies as an IT導入補助金 certified tool, agencies could receive 30-50% government subsidy on their subscription, reducing their cost and increasing our close rate. Requires Japanese entity (KK) to apply as a registered IT provider.

---

## 12. Go-To-Market Strategy

### Phase 1: Land First Customer (Months 5-8)

**Primary target: 原一探偵事務所 (Haraichi)**

**Why Haraichi:**
- Most tech-forward agency in Japan (drones, remote surveillance vehicles, custom equipment)
- 24 offices + additional consultation rooms — large enough to need software, nimble enough to adopt
- HQ in Kawagoe, Saitama (accessible from Tokyo)
- Member of CII (Council of International Investigators) — exposed to Western tech
- Documented pattern of investing in new investigation technology

**Approach:**
1. **Formal Japanese business letter** (紙の手紙) to agency leadership — NOT cold email
2. Reference their known technology investments
3. Offer free 3-month pilot at 2-3 offices
4. On-site demo at Kawagoe HQ (requires Japan travel)
5. Success metric: measurable reduction in average investigation duration

**Alternative first targets (in priority order):**

| Agency | Why | Approach |
|--------|-----|---------|
| AMUSE | Police OB-founded, already sends real-time LINE/email reports — most digitally mature communication | Cold outreach via formal letter to 株式会社MIRAI探偵社 |
| Rabbit | Youngest major chain (est. 2011), already uses LINE for client updates | Likely most receptive to new tech; approach via website contact form |
| MR | Advertises "最新ハイテク調査", lawyer partnerships — tech-receptive positioning | Formal letter to Shinjuku Island Tower HQ |

### Phase 2: Expand to Top 10 (Months 9-18)

- Use pilot success data to build case studies (with agency permission)
- Approach remaining top chains with proven ROI data
- Target JISA (日本調査業協会) partnership/endorsement
  - JISA's honorary advisor is a former Police Commissioner — credibility
  - JISA runs certification exams and training seminars — opportunity to integrate our tool into training
- Present at JISA events

### Phase 3: Long Tail (Year 2+)

- Self-serve signup for smaller agencies (Standard tier)
- Japanese-language marketing site with SEO targeting: "探偵 ソフト", "調査報告書 自動作成", "探偵 案件管理"
- Content marketing: blog posts about digital investigation techniques, evidence preparation for court
- Referral program: agencies that refer others get 1 month free
- Galu franchise network (100 offices) as a single enterprise deal

### Sales Process for Enterprise

**Required resources:**
- Japanese-speaking BD representative (**non-negotiable** for enterprise sales)
- Budget for 2-3 Japan trips in Year 1 (meishi exchange, relationship building)
- Demo environment with realistic sample data
- Japanese marketing materials (website, PDF brochure, case studies)

---

## 13. Competitive Analysis

### 13.1 Direct Competitors

**None.** There is no Japanese-language investigative intelligence platform. This is genuinely greenfield.

### 13.2 Adjacent Competition (Verified March 2026)

| Competitor | Pricing | Features | Japanese Support | Why We Win |
|------------|---------|----------|-----------------|-----------|
| **Maltego** | $5K-6.6K/yr (individual license) | Link analysis, 120+ data source transforms | No Japanese UI, no Japanese data sources | Japanese UI, Japanese data sources, investigation workflow, evidence packaging |
| **Skopenow** | Est. $10K-25K/yr (enterprise-only; $6.6M revenue / 1,500 customers) | Automated person OSINT, social media analysis | No Japanese UI, US-centric data | Japanese social media integration, case management, court evidence formatting |
| **ShadowDragon** | £5,500-£69,500/user/year (~$7K-$88K) | SocialNet + Horizon: 220+ data sources, social media mapping, alias resolution | Multi-language OCR available, but no Japanese market focus | Purpose-built for Japanese PI workflow, 10x lower price point, case management included |
| **CROSStrax** | $35-$105/month | PI case management: GPS tracking, video, billing, reports | English only | Japanese UI, Japanese court evidence format, OSINT integration, face matching |
| **PimEyes** | $14.99-$299.99/month (consumer); API custom | Face search engine, web-scale face database | Multi-language website (may include Japanese interface) | Asian face optimization, integrated with investigation workflow, not standalone search |
| **FaceCheck.id** | ~$0.30/search (API); consumer plans available | Face search against social media/web | No Japanese-specific features | Integrated workflow, Asian face optimization, case management context |

**Sources:**
- Maltego: https://www.maltego.com/pricing/
- Skopenow: https://getlatka.com/companies/skopenow.com ($6.6M revenue, 60 employees, 1500+ customers)
- ShadowDragon: UK Digital Marketplace G-Cloud 14 pricing document (https://www.applytosupply.digitalmarketplace.service.gov.uk/g-cloud/services/729871546736421)
- CROSStrax: https://www.crosstrax.co/pricing/
- PimEyes: https://pimeyes.com/en/premium
- FaceCheck.id: https://facecheck.id/

### 13.3 Our Competitive Moat

1. **Japanese-language UI** — zero competitors
2. **Japanese data source integration** — 法人番号 API, 官報, Japanese social media patterns
3. **Japanese court evidence formatting** — 調査報告書 template, isharyou documentation checklist
4. **Purpose-built for uwaki investigation workflow** — 70-80% of Japanese PI work
5. **Asian face recognition optimization** — AdaFace trained with diverse demographics vs. Western-biased alternatives
6. **First-mover advantage** — no existing solution in this market

---

## 14. Risk Analysis

### 14.1 Risk Matrix

| Risk | Probability | Impact | Mitigation | Residual Risk |
|------|------------|--------|------------|---------------|
| Agencies don't trust foreign software vendor | 30% | High | Japanese GK in Year 2; JISA partnership; prestigious legal opinion | Medium |
| APPI amendments restrict biometric tools | 15% | Medium | Data minimization by design; face matching is optional module; core value is case management | Low |
| Agencies prefer manual processes | 25% | Medium | ROI-driven sales: prove 2-3x efficiency gain in pilot; target tech-forward agencies first | Medium |
| Instagram/Twitter scraping gets harder or more expensive | 20% | Low | Core value is case management + evidence packaging; OSINT is additive, not essential | Low |
| Competitor enters market | 10% | Medium | First-mover advantage; deep Japanese market knowledge; enterprise relationships | Low |
| Cannot close enterprise sales without Japan presence | 25% | High | Budget for Japan trips; hire Japanese BD person or partner with local firm | Medium |
| X API pricing increases further | 15% | Low | Pay-per-use with spending caps; can adjust feature availability; API cost is small % of revenue | Low |
| InsightFace/ArcFace license issues | 20% | Medium | Use AdaFace (MIT license) or train custom model on commercial dataset | Low |

### 14.2 Expected Value Calculation

| Scenario | Probability | 2-Year Net Outcome | Weighted |
|----------|------------|---------------------|----------|
| Strong traction: 15+ agencies, $500K+ ARR | 15% | +$400K | +$60K |
| Moderate traction: 8-10 agencies, $200-300K ARR | 25% | +$150K | +$37.5K |
| Slow growth: 3-5 agencies, $80-120K ARR, marginal | 25% | +$20K | +$5K |
| Pivot needed: 1-2 agencies, PMF issues | 20% | -$30K | -$6K |
| Fail: no enterprise deals, product shelved | 15% | -$50K | -$7.5K |
| **Risk-adjusted EV** | | | **+$89K** |

**Comparison with alternatives:**
- Cheaterbuster clone: **-$18K expected value** (illegal, high litigation risk)
- This product: **+$89K expected value** (legal, defensible, positive ROI)

---

## 15. Development Roadmap

### 15.1 MVP (4 Months, Solo Developer)

**Month 1: Core Infrastructure + Case Management**
- [ ] Next.js project setup with Japanese i18n (next-intl)
- [ ] PostgreSQL schema deployment (organizations, users, clients, cases)
- [ ] Auth system with role-based access (Supabase Auth)
- [ ] Client intake form (Japanese)
- [ ] Case CRUD with status workflow
- [ ] Basic dashboard with case overview
- [ ] Office management (add/edit offices)

**Month 2: Evidence Studio**
- [ ] Evidence upload pipeline (presigned R2 URLs)
- [ ] SHA-256 hash generation on upload (client-side + server verification)
- [ ] Chain of custody logging (evidence_chain table)
- [ ] Timestamped field notes with GPS
- [ ] 調査報告書 auto-generation (PDF export with @react-pdf/renderer)
- [ ] Evidence timeline view (chronological photo/note display)
- [ ] Evidence quality scoring checklist

**Month 3: Digital Reconnaissance**
- [ ] X/Twitter API integration (pay-per-use, user monitoring)
- [ ] Instagram public profile scraping (Playwright + residential proxies)
- [ ] Face embedding pipeline (AdaFace on GPU VPS)
- [ ] Face matching against uploaded photos (pgvector similarity search)
- [ ] Unified target profile view with digital footprint timeline
- [ ] 法人番号 API integration
- [ ] Location heat map from public check-ins

**Month 4: Polish + Pilot Prep**
- [ ] Mobile-responsive field investigator view
- [ ] Agency analytics dashboard
- [ ] Stripe Japan billing integration
- [ ] Security hardening (encryption audit, penetration testing)
- [ ] Japanese copywriting for marketing site
- [ ] Demo environment with sample data
- [ ] Onboarding flow (guided setup)
- [ ] Documentation (Japanese user guide)

### 15.2 Post-MVP (Months 5-8, Concurrent with Pilot)
- [ ] GPS timeline import (CSV/GPX from common GPS trackers)
- [ ] Surveillance schedule builder (calendar view)
- [ ] Multi-office case transfer workflow
- [ ] Advanced evidence quality scoring with AI assistance
- [ ] Agency-wide analytics (multi-office comparison)
- [ ] FaceCheck.id API integration for web face search
- [ ] 官報 search integration
- [ ] PWA for offline field note capture
- [ ] Custom report template editor

### 15.3 Year 2 Roadmap
- [ ] React Native mobile app (if pilot feedback demands native app)
- [ ] SOC 2 Type 2 certification
- [ ] Integration with common GPS tracker brands
- [ ] AI-powered surveillance window recommendation engine
- [ ] Client portal (client can check case status via secure link)
- [ ] Multi-language support (English UI for international cases)
- [ ] IT導入補助金 certification (requires Japanese KK entity)

---

## Appendix A: Industry Data Tables

### A.1 Detective Agency Registration by Year

| Year | Registered Agencies | YoY Change |
|------|-------------------|------------|
| 2013 (H25) | 5,670 | — |
| 2016 (H28) | 5,691 | +21 |
| 2021 (R3) | 6,600+ | +909+ |
| 2025 (R7) | ~6,970 (est.) | ~+370 |

Source: 警察庁 (National Police Agency) annual statistics; 経済センサス (Economic Census)

### A.2 Investigation Pricing Comparison (Major Agencies)

| Agency | Uwaki Investigation | Hourly Rate | Minimum Package |
|--------|-------------------|-------------|-----------------|
| Haraichi | ¥60,000-800,000+ | ¥7,500-12,000/investigator | Varies by scope |
| HAL | ¥50,000-400,000 | ¥7,000-10,000/investigator | 1-day packages available |
| MR | Custom quote | Not disclosed | Consultation-based |
| AMUSE | ¥50,000-600,000 | ¥8,250/hour (listed) | Hourly + success fee options |
| Rabbit | Custom quote | Not disclosed | Package-based |
| Sakura Sachiko | Custom quote | Not disclosed | Consultation-based |

### A.3 Japan Social Media Usage (2025)

| Platform | Monthly Active Users (Japan) | Penetration | OSINT Relevance |
|----------|------------------------------|-------------|-----------------|
| LINE | 96M+ | ~76% | Low (private messaging) |
| YouTube | 78M+ | ~62% | Low (public comments only) |
| X/Twitter | 70M+ | ~56% | **Very High** (public posts, locations) |
| Instagram | 50M+ | ~40% | High (public profiles, tags) |
| TikTok | 28M+ | ~22% | Moderate (public profiles) |
| Facebook | 26M+ | ~21% | Moderate (declining, public posts) |

Sources: DataReportal Digital 2025 Japan, MIC Information and Communications White Paper

---

## Appendix B: Legal Compliance Checklist

### Pre-Launch Checklist

- [ ] **Legal opinion obtained** from Japanese IT law firm (TMI, Nishimura, AMT, or MHM)
- [ ] **委託契約 (data processing agreement)** template drafted and reviewed by counsel
- [ ] **利用規約 (Terms of Service)** in Japanese, covering:
  - [ ] Restriction to registered detective agencies (探偵業届出証明書 required)
  - [ ] Prohibited uses (stalking, harassment, discrimination per DBA Art. 7)
  - [ ] Purpose limitation
  - [ ] Indemnification clauses
  - [ ] Termination rights for misuse
  - [ ] Audit rights
- [ ] **プライバシーポリシー (Privacy Policy)** in Japanese, APPI-compliant
- [ ] **安全管理措置 (Security Management Measures)** documented:
  - [ ] Organizational measures (security officer, policies, training)
  - [ ] Physical measures (server access controls)
  - [ ] Technical measures (encryption, access controls, audit logging)
  - [ ] Human measures (NDAs, training, incident response)
- [ ] **Data retention policy** defined and configurable per agency
- [ ] **Breach notification procedure** established (APPI requires notification to PPC and affected individuals)
- [ ] **Cross-border transfer assessment** completed (if any data leaves Japan)
- [ ] **Face recognition impact assessment** conducted
- [ ] **探偵業届出証明書 verification process** established for onboarding

### Ongoing Compliance

- [ ] Annual security audit / penetration test
- [ ] Quarterly APPI compliance review
- [ ] Incident response drill (annual)
- [ ] Staff security training (annual)
- [ ] Terms of Service review (annual, or on APPI amendments)
- [ ] Monitor APPI amendment progress (2025-2027 amendments)

---

## Appendix C: Source Citations

### Market Data
1. 平成28年経済センサス活動調査 (2016 Economic Census), e-Stat, https://www.e-stat.go.jp/dbview?sid=0003215400
2. 警察庁「探偵業の届出状況」(NPA Detective Business Registration Statistics), annual publications
3. 「探偵業の市場規模」を徹底調査 (Detective Industry Market Size Research), @press, https://www.atpress.ne.jp/news/371927
4. J-Net21 探偵業 開業ガイド (Detective Business Startup Guide), https://j-net21.smrj.go.jp/startup/guide/proservice/20220706.html

### Social Media & Technology
5. DataReportal Digital 2025: Japan, https://datareportal.com/reports/digital-2025-japan
6. Statista: X penetration rate Japan, https://www.statista.com/statistics/425342/twitter-penetration-japan/
7. X API Pricing Documentation, https://docs.x.com/x-api/getting-started/pricing
8. X API Pay-Per-Use Announcement, https://devcommunity.x.com/t/announcing-the-launch-of-x-api-pay-per-use-pricing/256476
9. InsightFace GitHub, https://github.com/deepinsight/insightface
10. AdaFace: Quality Adaptive Margin for Face Recognition (CVPR 2022), https://github.com/mk-minchul/AdaFace

### Legal
11. 個人情報の保護に関する法律 (APPI), https://laws.e-gov.go.jp/law/415AC0000000057
12. 探偵業の業務の適正化に関する法律 (Detective Business Act), https://laws.e-gov.go.jp/law/418AC1000000060
13. ICLG Data Protection & Privacy 2025: Japan, https://iclg.com/practice-areas/data-protection-laws-and-regulations/japan
14. IAPP: Japan's DPA publishes interim summary, https://iapp.org/news/a/japan-s-dpa-publishes-interim-summary-of-amendments-to-data-protection-regulations
15. Clifford Chance: APPI Amendments 2025, https://www.cliffordchance.com/insights/resources/blogs/talking-tech/en/articles/2024/06/amendments-to-the-act-on-the-protection-of-personal-information-set-for-2025.html

### Competitor Data
16. Skopenow Revenue (Getlatka), https://getlatka.com/companies/skopenow.com
17. ShadowDragon G-Cloud Pricing, https://www.applytosupply.digitalmarketplace.service.gov.uk/g-cloud/services/729871546736421
18. CROSStrax Pricing, https://www.crosstrax.co/pricing/
19. PimEyes Premium Plans, https://pimeyes.com/en/premium
20. FaceCheck.id API, https://facecheck.id/

### Japanese Government Data APIs
21. 法人番号公表システム Web-API, https://www.houjin-bangou.nta.go.jp/webapi/
22. インターネット版官報, https://kanpou.npb.go.jp/
23. 登記情報提供サービス, https://www1.touki.or.jp/
24. デジタル庁 ベースレジストリ, https://www.digital.go.jp/en/policies/base_registry

### Agency Websites (Verified Live March 2026)
25. ガルエージェンシー, https://www.galu.co.jp/
26. 原一探偵事務所, https://www.haraichi.co.jp/
27. さくら幸子探偵事務所, https://www.sakurasachiko.jp/
28. HAL探偵社, https://hal-tanteisya.com/
29. MR探偵事務所, https://www.tantei-mr.co.jp/
30. 総合探偵社AMUSE, https://tantei-amuse.co.jp/
31. ラビット探偵社, https://rabbit-tantei.com/

---

*Document generated March 1, 2026. All data points verified against sources listed in Appendix C. Agency website URLs confirmed live. Pricing data current as of document date. Legal analysis is informational only and does not constitute legal advice — formal Japanese legal opinion recommended before launch.*
