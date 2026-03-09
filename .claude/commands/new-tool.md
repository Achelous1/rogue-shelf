# My Toys - 새 도구 페이지 추가

새 도구/게임 HTML 페이지를 My Toys 사이트 규칙에 맞게 생성하고, index.html에 카드를 추가한다.

## 프로젝트 규칙

### 공통 구조
- 스타일: Tailwind CSS (CDN)
- 언어: 한국어 (`lang="ko"`)
- 배경: `bg-gradient-to-br from-blue-50 to-indigo-100`
- 최대 너비: `max-w-6xl mx-auto` (도구) / `max-w-xl mx-auto` (게임)

### 헤더 (모든 페이지 필수)
```html
<a href="index.html" class="inline-block mb-4 text-sm text-blue-600 hover:text-blue-800 transition-colors">← 홈으로 돌아가기</a>
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
<meta name="author" content="My Toys">
<meta property="og:type" content="website">
<meta property="og:title" content="...">
<meta property="og:description" content="...">
<meta property="og:locale" content="ko_KR">
<meta property="og:site_name" content="My Toys">
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
<div class="mt-8 text-center text-xs text-gray-400 space-y-1">
    <p>© 2026 My Toys ·
        <a href="privacy-policy.html" class="hover:text-gray-600 transition-colors">개인정보처리방침</a>
    </p>
</div>
```

### index.html 카드 추가 형식
`<!-- 추후 추가될 도구 자리 -->` 블록 **앞**에 삽입:
```html
<!-- 도구명 -->
<a href="파일명.html"
    class="group bg-white border border-gray-200 rounded-xl p-6 shadow-sm hover:shadow-md hover:border-blue-300 transition-all duration-200">
    <div class="text-5xl mb-4">이모지</div>
    <h2 class="text-lg font-semibold text-gray-800 group-hover:text-blue-600 transition-colors mb-2">
        도구명
    </h2>
    <p class="text-sm text-gray-500">한 줄 설명</p>
    <div class="mt-4 text-xs text-blue-500 font-medium group-hover:underline">바로가기 →</div>
</a>
```

index.html의 SEO 태그(description, keywords, og:description, twitter:description, JSON-LD description)에도 새 도구명을 추가한다.

## 작업 순서

1. 새 도구 HTML 파일 생성 (위 규칙 적용)
2. index.html 카드 및 SEO 업데이트
3. 변경 파일 커밋 & `claude/fix-adsense-policy-rLdSj` 브랜치에 푸시

## 현재 도구 목록
- `lotto-generator.html` — 로또 번호 생성기 🎱
- `baseball-game.html` — 숫자야구 게임 ⚾
