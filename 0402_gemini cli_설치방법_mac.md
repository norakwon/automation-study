# 🍎 Mac 새 컴퓨터에 Gemini CLI 설치 가이드

## ✅ 사전 준비 — Homebrew 및 Node.js 설치

Gemini CLI는 Node.js 위에서 동작합니다. Mac에서는 패키지 관리자 Homebrew를 통해 설치하는 것이 가장 편리합니다.

### 1단계: Homebrew 설치

**터미널**을 열고 (Spotlight에서 `terminal` 검색) 아래 명령어 붙여넣기:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

설치 중 비밀번호를 물으면 Mac 로그인 비밀번호 입력 (입력해도 화면에 표시 안 됨).

> ⚠️ **Apple Silicon(M1/M2/M3) Mac의 경우** 설치 완료 후 아래 안내 문구가 뜰 수 있음:
> ```bash
> echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
> eval "$(/opt/homebrew/bin/brew shellenv)"
> ```
> 터미널에 그대로 복붙해서 실행하면 됩니다.

### 2단계: Node.js 설치

```bash
brew install node
```

### 3단계: 설치 확인

```bash
node --version   # v20.x.x 이상이어야 함
npm --version    # 함께 설치됨
```

---

## 📦 Gemini CLI 설치

### 4단계: 글로벌 설치

```bash
npm install -g @google/gemini-cli
```

> ⚠️ **권한 오류(EACCES)가 날 경우**:
> ```bash
> sudo npm install -g @google/gemini-cli
> ```
> Mac 로그인 비밀번호 입력 후 재시도

### 5단계: 설치 확인

```bash
gemini --version
```

버전 번호가 출력되면 성공입니다.

---

## 🔑 인증 설정

Gemini CLI를 사용하려면 Google 계정 또는 API 키가 필요합니다.

### 방법 A — Google 계정으로 로그인 (간편, 무료 플랜 포함)

```bash
gemini
```

처음 실행 시 자동으로 브라우저가 열리며 Google 로그인 화면이 뜹니다.

### 방법 B — API 키 직접 사용

1. **https://aistudio.google.com/apikey** 에서 API 키 발급
2. 환경 변수 설정:

```bash
# 현재 세션에만 적용
export GEMINI_API_KEY="발급받은_API_키"

# 영구 적용 (~/.zshrc에 추가)
echo 'export GEMINI_API_KEY="발급받은_API_키"' >> ~/.zshrc
source ~/.zshrc
```

---

## 🚀 실행 테스트

아무 디렉토리에서 아래 명령어 실행:

```bash
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
| `gemini` 명령어를 못 찾음 | 터미널 재시작 또는 `source ~/.zshrc` 실행 |
| 권한 오류(EACCES) | `sudo npm install -g @google/gemini-cli` 로 재설치 |
| `brew` 명령어를 못 찾음 | Homebrew PATH 설정 (`eval "$(/opt/homebrew/bin/brew shellenv)"`) |
| Node.js 버전이 낮음 | `brew upgrade node` 실행 |
| API 키 오류 | Google AI Studio에서 키 재발급 확인 |
