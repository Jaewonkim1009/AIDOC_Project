
<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=auto&height=300&section=header&text=AIDOC(에이닥)&desc=위치기반%20의료정보%20서비스%20앱&fontSize=45&animation=fadeIn&fontAlignY=38&descAlignY=70&descAlign=62"/>
</p>

<h2 align="center">
  <a href="https://docs.google.com/presentation/d/1uwqsnHpFGsPQlSU_NgWOPyXh7gwr0bjA/edit?slide=id.p1#slide=id.p1">📊 프로젝트 발표 프레젠테이션</a>
</h2>

---

## 📑 목차

- [📌 프로젝트 개요](#-프로젝트-개요)
- [🚨 문제 정의 및 기획 의도](#-문제-정의-및-기획-의도)
- [🎯 주요 기능](#-주요-기능)
- [🛠️ 기술 스택](#️-기술-스택)
- [⚙️ 시스템 아키텍처](#️-시스템-아키텍처)
- [🗂️ ERD 및 API 구조](#️-erd-및-api-구조)
- [📁 디렉터리 구조](#-디렉터리-구조)
- [💬 주요 코드 스니펫](#-주요-코드-스니펫)
- [🔒 보안 및 개인정보 보호](#-보안-및-개인정보-보호)
- [📈 기대 효과 및 발전 방향](#-기대-효과-및-발전-방향)
- [💡 회고 및 배운 점](#-회고-및-배운-점)

---

## 📌 프로젝트 개요

**AIDoc**은 실시간으로 사용자의 위치를 기반으로 병원, 약국, 응급실 정보를 제공하고 예약 및 길찾기, AI 챗봇, 다국어 번역을 통합한 Flutter 기반 모바일 플랫폼입니다. 외국인과 내국인의 **의료 접근성을 동시에 개선**하는 것이 핵심 목표입니다.

---

## 🚨 문제 정의 및 기획 의도

- 긴급 상황에서 병원/약국 위치를 빠르게 찾기 어려움
- 외국인 사용자들이 한국의 의료 시스템과 언어 장벽에 취약
- 공공 데이터 접근은 존재하지만 실사용자 경험에 최적화되지 않음

🎯 **기획 목표**: 실시간 위치 + 의료정보 + 다국어 + AI 챗봇을 하나로 통합한 의료 길잡이 앱

---

## 🎯 주요 기능

| 기능 | 설명 |
|------|------|
| 🏥 병원/약국/응급실 위치 조회 | 실시간 거리 기반 필터링 |
| 🔍 AI 챗봇 문진 | 증상 입력 기반 병원 추천 (Google Gemini API 연동) |
| 🌐 다국어 번역 지원 | 영어, 일본어, 중국어 지원 (확장 가능) |
| 📅 예약 기능 | 병원별 진료과 정보 및 예약 등록 |
| 🗺️ 길찾기 기능 | Naver Map API 활용 (현재 위치 → 병원) |
| 🔐 Google OAuth2 로그인 | 보안 기반 사용자 인증 |

---

## 🛠️ 기술 스택

| 구분 | 기술 |
|------|------|
| 프론트엔드 | Flutter, Dart |
| 백엔드 | FastAPI, Python, Uvicorn |
| 데이터베이스 | PostgreSQL (AWS RDS) |
| 인증 | Google OAuth2 |
| 지도/위치 | Naver Map API |
| AI 번역/챗봇 | Google Gemini 2.5 API |
| 외부 API | 공공데이터포털 병원/약국/응급실 XML API |

---

## ⚙️ 시스템 아키텍처

[Flutter App]  
&nbsp;&nbsp;&nbsp;&nbsp;↓ REST API  
[FastAPI Backend]  
&nbsp;&nbsp;&nbsp;&nbsp;↓ ORM (asyncpg)  
[PostgreSQL DB]

**외부 연동**  
- Google OAuth2 (로그인)  
- Naver Map API (지도 및 길찾기)  
- Gemini API (AI 챗봇 및 번역)  
- 공공데이터포털 (병원/약국/응급실 정보)

---

## 🗂️ ERD 및 API 구조

### 🧬 ERD

<img src="https://raw.githubusercontent.com/Jaewonkim1009/AIDOC_Project/main/assets/ERD.png" alt="ERD"/>


### 테이블 설명

#### 👤 사용자 관련 테이블

| 테이블명 | 설명 |
|----------|------|
| `users` | Firebase 기반 소셜 로그인 사용자 정보 (닉네임, 이메일, 프로필 이미지 등) |
| `email_users` | 이메일/비밀번호 기반 간단 회원 계정 정보 저장 (패스워드 해시 포함) |
| `loginaccount` | 로그인 사용자의 개인정보 및 계정 상세 정보 (생년월일, 성별, 전화번호 등 포함) |

#### 🏥 의료기관 관련 테이블

| 테이블명 | 설명 |
|----------|------|
| `medical_facility` | 일반 병·의원 정보 (병원명, 주소, 좌표, 진료시간 dutyTime1~8 등 상세 포함) |
| `pharmacy_facility` | 약국 정보 (약국명, 주소, 우편번호, 위도/경도, 요일별 운영시간 포함) |
| `emergency_facility` | 응급의료기관 정보 (병원명, 주소, 응급여부, 위도/경도, 진료과목 등 포함) |

#### 📅 예약 관련 테이블

| 테이블명 | 설명 |
|----------|------|
| `reservation` | 사용자 예약 내역 저장 (예약 일시, 병원명, 주소, 상태, 사용자 ID 등 포함) |
"""


---

## 📁 디렉터리 구조

### 📦 Backend

<img src="https://raw.githubusercontent.com/Jaewonkim1009/AIDOC_Project/main/assets/Backend.png" alt="Backend"/>

### 📱 Frontend

```plaintext
frontend/
├── pubspec.yaml                # Flutter 종속성 및 설정
├── key.env                     # 환경변수 파일
├── assets/
│   ├── images/                 # 이미지 리소스
│   └── langs/                  # 다국어 JSON
└── lib/
    ├── main.dart
    ├── chat_bot/               # 챗봇 UI 및 서비스
    ├── component/              # 공통 재사용 위젯
    ├── constants/              # API 주소, 키 등 상수값
    ├── emergency/              # 응급기관 관련 기능
    ├── hospital/               # 병원 관련 기능
    ├── map/                    # 지도 관련 기능
    ├── models/                 # 데이터 모델 클래스
    ├── pharmacy/               # 약국 관련 기능
    ├── profile/                # 사용자 설정
    ├── reservation/            # 예약 기능
    ├── service/                # API 통신, 인증 등 서비스
    ├── splash/                 # 앱 시작 로딩화면
    ├── state/                  # 상태관리
    └── widgets/                # 공용 위젯
```

---

## 💬 주요 코드

### 1. 거리 계산 (Haversine 공식)

```python
def haversine(lat1, lon1, lat2, lon2):
    from math import radians, sin, cos, sqrt, atan2
    R = 6371  # km
    dlat = radians(lat2 - lat1)
    dlon = radians(lon2 - lon1)
    a = sin(dlat/2)**2 + cos(radians(lat1)) * cos(radians(lat2)) * sin(dlon/2)**2
    return R * 2 * atan2(sqrt(a), sqrt(1 - a))
```

### 2. 챗봇 - 증상 기반 병원 추천 (Gemini)

```python
prompt = f"증상: {user_input}, 어떤 병원을 가야 할까?"
response = gemini.generate(prompt)
return response.content
```

### 3. 내 주변 병원 목록 요청

```dart
final res = await http.get(Uri.parse('$api/hospital/nearby?lat=$lat&lon=$lon'));
final data = jsonDecode(res.body);
```

---

## 🔒 보안 및 개인정보 보호

- Google OAuth2 인증 적용
- 토큰 기반 인증 및 사용자 데이터 암호화
- 의료법 및 개인정보보호법 철저 준수
- 외부 API 접근 시 사용자 동의 기반 처리

---

## 📈 기대 효과 및 발전 방향

- 외국인의 병원 이용 접근성 향상
- 의료기관 운영 효율성 증대
- 건강 데이터 기반 AI 추천 시스템 확장
- 웨어러블, PHR 연동, 보험 정보 연계 기능 추가 예정

---

