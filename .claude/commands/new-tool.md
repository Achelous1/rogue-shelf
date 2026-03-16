# ROGUE SHELF - 새 도구 페이지 추가

새 도구/게임 HTML 페이지를 ROGUE SHELF 사이트 규칙에 맞게 생성하고, index.html에 카드를 추가한다.

## 프로젝트 규칙

### 공통 구조
- 스타일: Tailwind CSS (CDN) + 인라인 `<style>` (다크 테마 커스텀)
- 언어: 한국어 (`lang="ko"`)
- 배경: `background-color: #0f0f0f` (body에 인라인 스타일 또는 Tailwind `bg-[#0f0f0f]`)
- 텍스트: 기본 흰색 (`text-white`), 보조 회색 (`text-gray-500`)
- 최대 너비: `max-w-5xl mx-auto` (도구/게임 공통)
- 폰트: Helvetica Neue 계열 (sans-serif 시스템 폰트)

### 헤더 (모든 페이지 필수)
```html
<a href="index.html" class="inline-block mb-6 text-xs tracking-widest uppercase text-gray-600 hover:text-white transition-colors font-mono">← ROGUE SHELF</a>
```

### AdSense (index.html 제외한 모든 페이지에 삽입)
```html
<!-- Google AdSense -->
<meta name="google-adsense-account" content="ca-pub-4857107637953203">
<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-4857107637953203"
     crossorigin="anonymous"></script>
```

### SEO 필수 태그 (모든 페이지)
```html
<meta name="description" content="...">
<meta name="keywords" content="...">
<meta name="robots" content="index, follow">
<meta name="author" content="ROGUE SHELF">
<meta property="og:type" content="website">
<meta property="og:title" content="...">
<meta property="og:description" content="...">
<meta property="og:locale" content="ko_KR">
<meta property="og:site_name" content="ROGUE SHELF">
<meta name="twitter:card" content="summary">
<meta name="twitter:title" content="...">
<meta name="twitter:description" content="...">
```

### JSON-LD (도구/게임 페이지)
```json
{
  "@context": "https://schema.org",
  "@type": "WebApplication",
  "name": "도구 이름",
  "description": "...",
  "applicationCategory": "UtilitiesApplication 또는 GameApplication",
  "operatingSystem": "Web",
  "inLanguage": "ko",
  "offers": { "@type": "Offer", "price": "0", "priceCurrency": "KRW" }
}
```

### 푸터 (모든 페이지)
```html
<div class="mt-12 border-t border-[#2a2a2a] pt-6 pb-4">
    <div class="flex items-center justify-between">
        <p class="text-xs text-gray-700">© 2026 ROGUE SHELF</p>
        <a href="privacy-policy.html" class="text-xs text-gray-700 hover:text-gray-400 transition-colors">개인정보처리방침</a>
    </div>
</div>
```

### index.html 카드 추가 형식
`<!-- 추후 추가될 도구 자리 -->` 블록 **앞**에 삽입하고 index 번호를 순서대로 증가시킨다:
```html
<!-- 도구명 -->
<a href="파일명.html" class="card-link bg-[#0f0f0f] p-6 block group">
    <div class="flex items-start justify-between mb-6">
        <span class="index-num text-xs text-gray-600 font-mono">NN</span>
        <div class="flex gap-2">
            <span class="tag text-[10px] tracking-widest uppercase text-gray-500 px-2 py-0.5">GAME 또는 UTILITY</span>
        </div>
    </div>
    <div class="text-3xl mb-4">이모지</div>
    <h2 class="text-base font-semibold text-white mb-2 group-hover:text-gray-300 transition-colors">
        도구명
    </h2>
    <p class="text-xs text-gray-500 leading-relaxed">한 줄 설명</p>
    <div class="mt-6 text-xs text-gray-600 group-hover:text-white transition-colors font-mono">→</div>
</a>
```

멀티플레이어 게임의 경우 태그를 두 개 추가:
```html
<span class="tag text-[10px] tracking-widest uppercase text-gray-500 px-2 py-0.5">GAME</span>
<span class="tag text-[10px] tracking-widest uppercase text-gray-500 px-2 py-0.5">2P</span>
```

index.html의 SEO 태그(description, keywords, og:description, twitter:description, JSON-LD description)에도 새 도구명을 추가하고, header의 `items` 카운트(`5 items` 등)를 업데이트한다.

## 다크 테마 CSS (index.html 및 각 페이지 `<style>` 블록)
```css
body { background-color: #0f0f0f; font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif; }
.card-link { border: 1px solid #2a2a2a; transition: border-color 0.2s, background-color 0.2s; }
.card-link:hover { border-color: #ffffff; background-color: #181818; }
.tag { border: 1px solid #3a3a3a; }
.shelf-line { border-top: 1px solid #2a2a2a; }
.index-num { font-variant-numeric: tabular-nums; }
```

## 작업 순서

1. 새 도구 HTML 파일 생성 (위 규칙 적용)
2. index.html 카드, SEO, items 카운트 업데이트
3. 변경 파일 커밋 & `claude/webrtc-omok-game-0yZ5Q` 브랜치에 푸시

## 현재 도구 목록
- `lotto-generator.html` — 로또 번호 생성기 🎱
- `pension-lottery.html` — 연금복권 번호 생성기 💸
- `baseball-game.html` — 숫자야구 게임 ⚾
- `slot-machine.html` — 슬롯머신 🎰
- `omok-battle.html` — 오목대전 ⚫ (WebRTC 2P, 렌주룰)
