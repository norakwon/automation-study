# 🪟 Windows 새 컴퓨터에 Gemini CLI 설치 가이드

## ✅ 사전 준비 — Node.js 설치

Gemini CLI는 Node.js 위에서 동작합니다. 먼저 Node.js를 설치해야 합니다.

### 1단계: Node.js 다운로드 및 설치

1. 브라우저에서 **https://nodejs.org/ko/download** 접속
2. 페이지 **하단 드롭다운**에서 아래와 같이 설정
   - 아키텍처: **x64**
   - OS: **Windows**
   - 항목: **Windows 설치 프로그램 (.msi)**
3. 다운로드된 `.msi` 파일 실행 → 기본 설정 그대로 **Next** 클릭하며 설치 완료

### 2단계: 설치 확인

설치 완료 후 **Windows Terminal** 또는 **PowerShell**을 열고 확인:

```powershell
node --version   # v20.x.x 이상이어야 함
npm --version    # 함께 설치됨
```

---

## 📦 Gemini CLI 설치

### 3단계: 글로벌 설치

```powershell
npm install -g @google/gemini-cli
```

> ⚠️ **실행 정책 오류가 날 경우** (PowerShell 보안 정책):
> PowerShell을 **관리자 권한으로 실행**한 뒤 아래 명령어 입력 후 재시도
> ```powershell
> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
> ```

### 4단계: 설치 확인

```powershell
gemini --version
```

버전 번호가 출력되면 성공입니다.

---

## 🔑 인증 설정

Gemini CLI를 사용하려면 Google 계정 또는 API 키가 필요합니다.

### 방법 A — Google 계정으로 로그인 (간편, 무료 플랜 포함)

```powershell
gemini
```

처음 실행 시 자동으로 브라우저가 열리며 Google 로그인 화면이 뜹니다.

### 방법 B — API 키 직접 사용

1. **https://aistudio.google.com/apikey** 에서 API 키 발급
2. 환경 변수 설정:

```powershell
# 현재 세션에만 적용
$env:GEMINI_API_KEY="발급받은_API_키"

# 영구 적용 (시스템 환경 변수)
[System.Environment]::SetEnvironmentVariable("GEMINI_API_KEY", "발급받은_API_키", "User")
```

---

## 🚀 실행 테스트

아무 디렉토리에서 아래 명령어 실행:

```powershell
gemini
```

프롬프트 입력창이 뜨면 완료! 예시:

```
> 안녕! 파이썬으로 Hello World 코드 짜줘
```

---

## 💡 자주 겪는 문제

| 문제 | 해결법 |
|------|--------|
| `gemini` 명령어를 못 찾음 | PowerShell 재시작 또는 PATH에 npm 글로벌 경로 추가 |
| 실행 정책 오류 | `Set-ExecutionPolicy RemoteSigned` 실행 |
| Node.js 버전이 낮음 | nodejs.org에서 최신 LTS 재설치 |
| API 키 오류 | Google AI Studio에서 키 재발급 확인 |
