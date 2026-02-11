# Facebook Advantage+ 대량 광고 자동 생성기

Meta Marketing API를 활용하여 Facebook Advantage+ 광고를 대량으로 자동 생성하는 도구입니다.

## 개요

이미지/영상 소재가 담긴 폴더 구조를 기반으로, Excel에서 카피(본문·헤드라인·설명·URL·CTA)만 작성하면 수십 개의 광고를 한 번에 생성합니다.

### 주요 기능

- **대량 소재 업로드**: 폴더별 이미지(JPG/PNG) + 영상(MP4/MOV) 자동 수집 및 업로드
- **Excel 기반 카피 관리**: `.xlsx` 파일에서 광고 카피를 관리하고 스크립트가 자동으로 읽어옴
- **Advantage+ 최적화**: CBO, Advantage+ 타겟팅, 자동 배치, Advantage+ 크리에이티브 최적화 적용
- **안전한 실행**: 모든 광고가 `PAUSED` 상태로 생성되어 검토 후 활성화 가능

## 파일 구조

```
ad_facebook/
├── fb_ad_set.ipynb        # 메인 스크립트 (Jupyter Notebook)
├── fb_ad_config.xlsx      # 광고 카피 설정 파일 (Excel)
├── README.md
├── .gitignore
└── 2511_카테고리/          # 소재 폴더 (git 미포함)
    ├── 2511_캐릭터A/
    │   ├── Img/           # 이미지 소재 (JPG)
    │   └── Video/         # 영상 소재 (MP4)
    └── ...
```

## 사용법

### 1. 사전 준비

- [Meta for Developers](https://developers.facebook.com/)에서 앱 생성
- Marketing API 권한 획득 (ads_management, ads_read)
- 필요한 ID 확보: App ID, App Secret, Access Token, Ad Account ID, Page ID, Pixel ID

### 2. 소재 폴더 구성

```
소재폴더/
├── 2511_캐릭터명/
│   ├── Img/
│   │   ├── 캐릭터_이미지_작품명_202511_1080x1080.jpg
│   │   └── ...
│   └── Video/
│       ├── 캐릭터_영상_작품명_202511_1080x1080.mp4
│       └── ...
```

### 3. Excel에서 카피 작성

`fb_ad_config.xlsx`를 열어 **노란색 셀**만 채웁니다:

| 입력 항목 | 설명 |
|-----------|------|
| 본문 텍스트 | 광고 메인 카피 |
| 헤드라인 | 짧은 헤드라인 |
| 설명 | 부가 설명 |
| 랜딩 URL | 클릭 시 이동할 URL |
| CTA 버튼 | LEARN_MORE, SHOP_NOW 등 |

### 4. 노트북 실행

```bash
jupyter notebook fb_ad_set.ipynb
```

STEP 2에서 API 키를 입력하고, 순서대로 셀을 실행하면 됩니다.

## 광고 구조

```
Campaign (캠페인) ← 광고그룹명 기준
└── Ad Set (광고세트) ← CBO + Advantage+ 타겟팅
    ├── Ad (광고) ← 이미지 소재 1
    ├── Ad (광고) ← 이미지 소재 2
    ├── Ad (광고) ← 영상 소재 1
    └── ...
```

## 기술 스택

- **Python** + Jupyter Notebook
- **facebook-business** (Meta Marketing API SDK)
- **openpyxl** (Excel 읽기)
- **Advantage+ Features**: Campaign Budget Optimization, Advantage+ Targeting, Advantage+ Placements, Advantage+ Creative

## 라이선스

MIT License
