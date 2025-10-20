# 광물캐기 (Mine Digger) 게임 프로젝트

## 📁 프로젝트 구조

```
mine-digger-game/
├── README.md                           # 이 파일
├── mine-digger-game-design.md          # 완전한 게임 기획서
├── mine-digger-sprites.html            # 초기 스프라이트 (광물 + 캐릭터)
├── mine-digger-complete-sprites.html   # 확장 스프라이트 (블록, 곡괭이, 이펙트 등)
└── mine-digger-all-sprites.html        # 최종 완전판 스프라이트 (모든 에셋)
```

## 🎮 게임 개요

**장르**: RPG + 채굴 시뮬레이션 + 방치형
**플랫폼**: 웹 브라우저 (모바일 대응)
**스타일**: 레트로 픽셀 아트 (32x32 도트)

### 핵심 게임플레이
집 → 마을 → 광산 → 채굴 → 상점 판매 → 업그레이드 → 반복

## 📊 현재 진행 상황

### ✅ 완료된 작업
1. **게임 기획서 작성** (`mine-digger-game-design.md`)
   - 게임 시스템 (HP, ATK, DEF)
   - 월드 맵 구조 (집, 마을, 광산 7개)
   - 광물 32종 데이터
   - 곡괭이 8종 데이터
   - 화면 구성 및 UI/UX 설계
   - 게임 경제 밸런스

2. **스프라이트 제작** (`mine-digger-all-sprites.html`)
   - ✅ 캐릭터 애니메이션 2종 (IDLE, MINING)
   - ✅ 광물 32종 (Tier 1~7)
   - ✅ 곡괭이 아이템 8종
   - ✅ 건물 4종 (집, 상점, 대장간, 광산입구)
   - ✅ NPC 2명 (상점주인, 대장장이)
   - ✅ 배경 타일 3종
   - ✅ 광산 배경 7종 (레벨별)
   - ✅ UI 컴포넌트 (HP바, 데미지, 버튼)
   - ✅ 이펙트 3종

3. **Framer UI 디자인** ✅ (2025-10-20 완료)
   - ✅ 텍스트 스타일 3종 (Title, ButtonText, HUDText)
   - ✅ 집 화면 (상단 HUD + 메인 컨텐츠 + 버튼 3개)
   - ✅ 마을 화면 (건물 4개 그리드 + NPC 메시지)
   - ✅ 채굴 화면 (광물 정보 + HP바 + 채굴 버튼 + 하단 네비게이션)

### 🔜 다음 단계
- [ ] 게임 개발 (HTML5 Canvas + JavaScript)
  - 씬 관리 시스템 (집/마을/광산 전환)
  - 채굴 시스템 (HP, ATK, DEF 계산)
  - 인벤토리 & 상점 시스템
  - 에너지 & 곡괭이 내구도 시스템
  - 로컬 저장 (세이브/로드)
- [ ] Cloudflare Pages 배포

## 🎨 스프라이트 미리보기

### 사용 방법
각 HTML 파일을 브라우저로 열면 제작된 스프라이트를 확인할 수 있습니다.

```bash
# 최종 완전판 스프라이트 보기
open mine-digger-all-sprites.html
```

## 🎯 게임 핵심 시스템

### 1. 채굴 시스템
- 광물마다 HP 존재
- 곡괭이로 타격하여 HP를 0으로 만들면 채굴 성공
- 광물 방어력(DEF)에 따라 데미지 차감

**데미지 계산:**
```javascript
if (pickaxe.ATK < mineral.DEF) {
  damage = Math.random() < 0.5 ? pickaxe.ATK * 0.5 : pickaxe.ATK;
} else if (pickaxe.ATK >= mineral.DEF * 2) {
  damage = pickaxe.ATK * 1.5; // 크리티컬!
} else {
  damage = pickaxe.ATK;
}
```

### 2. 월드 구조
- **집**: 휴식, 도감
- **마을**: 상점, 대장간, 광산 입구
- **광산**: Lv1~7 (티어별 다른 광물)

### 3. 경제 시스템
- 광물 채굴 → 상점에서 판매 → 골드 획득
- 골드로 곡괭이 구매/업그레이드
- 더 좋은 곡괭이 → 더 높은 레벨 광산 진입 가능

## 📱 기술 스택

- **디자인**: Framer
- **프론트엔드**: HTML5 Canvas + Vanilla JS
- **스타일**: Pixel Perfect CSS
- **배포**: Cloudflare Pages
- **데이터**: LocalStorage (세이브 시스템)

## 🎨 컬러 팔레트

```
배경: #1a1a1a (다크)
UI 배경: #2a2a2a
테두리: #ffd700 (골드)
텍스트: #ffffff, #aaaaaa
성공: #00ff00
경고: #ff8800

티어 컬러:
T1: #666666
T2: #888888
T3: #ff8800
T4: #00aaff
T5: #ffaa00
T6: #ff00ff
T7: 그라디언트 (레인보우)
```

## 📝 개발 로드맵

### Phase 1: 스프라이트 제작 ✅
- [x] 캐릭터 애니메이션
- [x] 광물 32종
- [x] 곡괭이 8종
- [x] 건물 4종
- [x] NPC 2명
- [x] 배경 타일
- [x] UI 컴포넌트
- [x] 이펙트

### Phase 2: Framer 디자인 (진행 중)
- [x] 집 화면
- [ ] 마을 화면
- [ ] 상점 UI
- [ ] 광산 선택 UI
- [ ] 채굴 화면
- [ ] 팝업 UI

### Phase 3: 게임 개발
- [ ] 씬 관리 (집/마을/광산)
- [ ] 채굴 시스템 (HP, ATK, DEF)
- [ ] 인벤토리 시스템
- [ ] 상점 시스템
- [ ] 에너지 시스템
- [ ] 곡괭이 내구도 시스템
- [ ] 로컬 저장

### Phase 4: 배포
- [ ] 모바일 반응형
- [ ] 성능 최적화
- [ ] Cloudflare Pages 배포

## 🔗 참고 링크

- [게임 기획서 상세보기](mine-digger-game-design.md)
- Framer 프로젝트: (Framer 프로젝트 URL 추가 예정)
- 배포 URL: (배포 후 추가 예정)

---

**개발 시작일**: 2025년 10월 20일
**현재 상태**: Phase 2 진행 중 (Framer UI 디자인)
