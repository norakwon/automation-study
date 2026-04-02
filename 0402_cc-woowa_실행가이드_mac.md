# 🍎 Mac에서 cc-woowa 실행 가이드 (Node.js 없어도 OK)

## ✅ 1단계: Node.js 설치 여부 확인

**터미널**을 열고 (Spotlight에서 `terminal` 검색) 아래 입력:

```bash
node --version
```

- 버전 번호(예: `v20.x.x`)가 뜨면 → **3단계로 바로 이동**
- `command not found` 가 뜨면 → **2단계 진행**

---

## 🛠️ 2단계: Node.js 설치 (없는 경우만)

### Homebrew가 있는 경우

```bash
brew install node
```

### Homebrew도 없는 경우 (완전 새 Mac)

아래 명령어를 터미널에 붙여넣고 실행:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

설치 중 비밀번호 입력 요구 시 Mac 로그인 비밀번호 입력 (화면에 안 보이는 게 정상).

> ⚠️ **M1/M2/M3 Mac이라면** 설치 후 아래 두 줄도 실행:
> ```bash
> echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
> eval "$(/opt/homebrew/bin/brew shellenv)"
> ```

그 다음 Node.js 설치:

```bash
brew install node
```

설치 확인:

```bash
node --version   # v20.x.x 이상이면 OK
```

---

## 🚀 3단계: cc-woowa 실행

```bash
npx cc-woowa
```

실행 후 아래 항목 입력:

- **참여자**: 본인 이름
- **서버 URL**: `https://cc-woowa.up.railway.app/`

---

## 💡 자주 겪는 문제

| 문제 | 해결법 |
|------|--------|
| `brew` 명령어를 못 찾음 | Homebrew PATH 설정: `eval "$(/opt/homebrew/bin/brew shellenv)"` |
| `npx` 명령어를 못 찾음 | 터미널 재시작 후 재시도 |
| 권한 오류(EACCES) | `sudo npm install -g npx` 실행 |
