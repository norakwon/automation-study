# 맥(Mac)에서 클로드 코드(Claude Code) 처음 설치하기
> 개발 지식이 전혀 없는 분을 위한 단계별 가이드

---

## 시작 전에 알아두기

- **터미널(Terminal)** : 명령어를 입력해서 컴퓨터를 조작하는 검은 창입니다. 겁내지 마세요!
- **명령어를 입력할 때는 복사-붙여넣기를 적극 활용하세요.**
- 각 단계에서 뭔가 설치된다는 메시지가 뜨면 `y` 또는 엔터(Enter)를 누르면 됩니다.

---

## 1단계: 터미널 열기

1. 키보드에서 `Command(⌘) + 스페이스바`를 누릅니다.
2. 검색창에 `터미널` 또는 `Terminal`을 입력합니다.
3. 터미널 앱을 클릭해서 엽니다.

> 검은색(또는 흰색) 창이 뜨면 성공입니다.

---

## 2단계: Homebrew 설치 (맥의 앱스토어 같은 것)

터미널에 아래 명령어를 **복사해서 붙여넣기** 하고 엔터를 누르세요.

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

- 설치 중간에 **맥 로그인 비밀번호**를 물어볼 수 있습니다. 입력해도 화면에 아무것도 안 보이는 게 정상입니다 (보안 때문에). 그냥 비밀번호 입력 후 엔터!
- `Press RETURN/ENTER to continue` 메시지가 뜨면 엔터를 누르세요.
- 설치가 끝나면 터미널에 `==> Installation successful!` 같은 메시지가 나옵니다.

**Apple Silicon(M1/M2/M3/M4) 맥 사용자 추가 작업:**

설치 완료 후 터미널에 아래 두 줄을 각각 입력하고 엔터를 누르세요.

```
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
```
```
eval "$(/opt/homebrew/bin/brew shellenv)"
```

> 내 맥이 Intel인지 Apple Silicon인지 모르겠다면: 화면 왼쪽 위 애플 로고() → 이 Mac에 관하여 → '칩' 항목이 있으면 Apple Silicon, '프로세서' 항목이 있으면 Intel입니다.

---

## 3단계: Node.js 설치

Claude Code를 실행하려면 Node.js가 필요합니다. 터미널에 아래 명령어를 입력하세요.

```
brew install node
```

설치가 끝나면 제대로 됐는지 확인해 봅니다.

```
node --version
```

`v22.0.0` 처럼 버전 숫자가 뜨면 성공입니다!

---

## 4단계: Claude Code 설치

이제 드디어 Claude Code를 설치합니다.

```
npm install -g @anthropic-ai/claude-code
```

설치가 끝나면 확인합니다.

```
claude --version
```

버전 숫자가 뜨면 성공입니다!

---

## 5단계: Anthropic API 키 발급받기

Claude Code를 사용하려면 **API 키**가 필요합니다. API 키는 Claude Code가 AI 서버에 접속할 때 사용하는 일종의 비밀번호입니다.

1. 웹브라우저에서 `console.anthropic.com` 에 접속합니다.
2. 회원가입 또는 로그인을 합니다.
3. 왼쪽 메뉴에서 **API Keys** 를 클릭합니다.
4. **Create Key** 버튼을 클릭합니다.
5. 키 이름을 아무거나 입력하고 (예: `my-claude-code`) **Create Key** 를 누릅니다.
6. 화면에 나타난 키를 **반드시 복사해서 안전한 곳에 저장**하세요. 창을 닫으면 다시 볼 수 없습니다!

> API 키는 `sk-ant-api03-...` 형태로 시작하는 긴 문자열입니다.

> **유료 서비스 안내**: API 사용은 사용량만큼 비용이 발생합니다. 처음 가입 시 무료 크레딧을 제공하는 경우가 있습니다.

---

## 6단계: Claude Code 처음 실행하기

터미널에 아래를 입력합니다.

```
claude
```

처음 실행하면 API 키를 입력하라고 합니다. 5단계에서 저장해둔 API 키를 붙여넣기 하고 엔터를 누르세요.

설정이 완료되면 Claude Code가 시작됩니다!

---

## 7단계: 기본 사용법

Claude Code가 실행된 상태에서:

- **질문하기**: 그냥 한국어로 타이핑하면 됩니다. 예: `파이썬으로 hello world 출력하는 코드 만들어줘`
- **종료하기**: `/exit` 를 입력하거나 `Ctrl + C` 를 누릅니다.
- **특정 폴더에서 작업하기**: 터미널에서 먼저 해당 폴더로 이동한 후 `claude` 를 실행합니다.

```
cd 폴더경로
claude
```

예시:
```
cd ~/Desktop/내프로젝트
claude
```

---

## 문제 해결

### "command not found: brew" 오류
→ 2단계를 다시 시도하세요. Apple Silicon 맥이라면 추가 작업 두 줄도 꼭 실행하세요.

### "command not found: node" 오류
→ 터미널을 완전히 닫았다가 다시 열고, 3단계를 다시 시도하세요.

### "command not found: claude" 오류
→ 터미널을 완전히 닫았다가 다시 열고 `claude` 를 다시 입력해보세요.

### API 키 오류
→ API 키를 다시 확인하세요. 키 앞뒤로 공백이 들어가지 않았는지 확인하세요.

---

## 설치 완료 체크리스트

- [ ] Homebrew 설치 완료 (`brew --version` 으로 확인)
- [ ] Node.js 설치 완료 (`node --version` 으로 확인)
- [ ] Claude Code 설치 완료 (`claude --version` 으로 확인)
- [ ] API 키 발급 및 저장 완료
- [ ] `claude` 명령어로 정상 실행 확인

모든 항목이 체크되면 준비 완료입니다! 🎉
