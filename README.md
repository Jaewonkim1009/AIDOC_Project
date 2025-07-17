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
- [⚙️ 시스템 아키텍처](#-시스템-아키텍처)
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

```plaintext
[Flutter App]
   ↓ REST API
[FastAPI Backend]
   ↓ ORM (asyncpg)
[PostgreSQL DB]

외부 연동: 
 - Google OAuth2 (로그인)
 - Naver Map (지도 및 길찾기)
 - Gemini API (챗봇 및 다국어 번역)
 - 공공데이터포털 (병원/약국 데이터)

