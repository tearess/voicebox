# Voicebox 실행 설명서

이 문서는 Voicebox를 아주 쉽게 켜는 방법입니다.

Voicebox는 컴퓨터 안에서 목소리를 만들고, 목소리를 따라 하게 하고, 음성 파일을 만드는 앱입니다.

## 제일 쉬운 말로 설명하면

Voicebox는 이런 일을 합니다.

- 글을 쓰면 목소리로 읽어 줍니다.
- 짧은 목소리 샘플을 넣으면 비슷한 목소리를 만들 수 있습니다.
- 만든 목소리에 효과를 줄 수 있습니다.
- 내 컴퓨터에서 실행되므로 목소리 파일이 밖으로 나가지 않습니다.

주의할 점:

- 다른 사람 목소리는 꼭 허락을 받고 사용하세요.
- 처음 사용할 때는 큰 AI 모델을 다운로드하므로 시간이 오래 걸릴 수 있습니다.

## 지금 이 컴퓨터에서 실행하기

이 컴퓨터는 이미 기본 설정이 끝나 있습니다.

터미널을 열고 아래 명령어를 차례대로 입력하세요.

```bash
cd /Users/tearess-mac/gpters/voicebox
just dev-web
```

조금 기다리면 터미널에 이런 주소가 나옵니다.

```text
http://localhost:5173/
```

브라우저에서 위 주소를 열면 Voicebox 화면이 나옵니다.

중요:

- 화면 주소는 보통 `http://localhost:5173/`입니다.
- 만약 터미널에 `http://localhost:5174/`처럼 다른 숫자가 나오면, 터미널에 나온 주소를 열면 됩니다.

## 포트 번호가 왜 두 개일까?

Voicebox는 두 개가 같이 움직입니다.

```text
http://localhost:5173/
```

이 주소는 사람이 보는 화면입니다.

```text
http://localhost:17493/
```

이 주소는 화면 뒤에서 일하는 서버입니다.
목소리 만들기, 파일 저장, 모델 확인 같은 일을 합니다.

그래서 평소에 브라우저로 여는 주소는 `5173`입니다.
`17493`은 직접 사용할 일이 거의 없습니다.

## 이미 켜져 있다면

이미 Voicebox가 켜져 있으면 명령어를 다시 입력하지 않아도 됩니다.

브라우저에서 이것만 열면 됩니다.

```text
http://localhost:5173/
```

단, `just dev-web`을 실행했을 때 터미널에 다른 주소가 나왔다면 그 주소를 여세요.

뒤에서 일하는 서버가 잘 켜졌는지 확인하고 싶으면 이 주소를 열어 보세요.

```text
http://localhost:17493/health
```

개발자용 API 설명서는 여기에서 볼 수 있습니다.

```text
http://localhost:17493/docs
```

## 앱 끄기

터미널에서 실행 중인 Voicebox를 끄려면 터미널 창에서 다음 키를 누릅니다.

```text
Control + C
```

혹시 여러 개가 켜져 있어서 정리하고 싶으면 아래 명령어를 입력합니다.

```bash
cd /Users/tearess-mac/gpters/voicebox
just kill
```

## 처음부터 다시 설정해야 할 때

보통은 이 단계가 필요 없습니다.

하지만 컴퓨터를 새로 바꾸거나, 폴더를 새로 받은 경우에는 아래처럼 합니다.

```bash
cd /Users/tearess-mac/gpters/voicebox
just setup
```

설정이 끝나면 실행합니다.

```bash
just dev-web
```

브라우저에서 엽니다.

```text
http://localhost:5173/
```

## 데스크톱 앱으로 실행하기

웹 브라우저가 아니라 진짜 맥 앱 창처럼 실행하고 싶으면 아래 명령어를 씁니다.

```bash
cd /Users/tearess-mac/gpters/voicebox
just dev
```

이 명령어는 백엔드 서버와 Tauri 데스크톱 앱을 같이 켭니다.

## 첫 음성 만들기

처음에는 이렇게 해보세요.

1. 브라우저에서 `http://localhost:5173/`를 엽니다.
2. 화면에서 사용할 목소리를 고릅니다.
3. 읽게 하고 싶은 문장을 씁니다.
4. Generate 버튼을 누릅니다.
5. 처음에는 AI 모델을 다운로드하느라 오래 걸릴 수 있습니다.

짧은 문장으로 먼저 시험해 보는 것이 좋습니다.

예시:

```text
Hello, this is my first Voicebox test.
```

## 자주 생기는 문제

### 주소가 열리지 않을 때

먼저 Voicebox를 켰는지 확인하세요.

```bash
cd /Users/tearess-mac/gpters/voicebox
just dev-web
```

### 포트가 이미 사용 중이라고 나올 때

이미 켜진 Voicebox가 있을 수 있습니다.

먼저 끄고 다시 켭니다.

```bash
just kill
just dev-web
```

### 처음 생성이 너무 오래 걸릴 때

정상일 수 있습니다.

처음에는 Hugging Face에서 AI 모델을 다운로드합니다.
모델은 몇 GB일 수 있어서 인터넷 속도에 따라 오래 걸립니다.
한 번 받은 뒤에는 다음부터 더 빨라집니다.

### Python이나 just가 없다고 나올 때

이 컴퓨터에는 이미 설치해 두었습니다.

다른 컴퓨터에서 실행하는 경우에는 README.md의 설치 설명을 보고 필요한 프로그램을 먼저 설치해야 합니다.

필요한 것:

- Bun
- Python 3.11 이상
- Rust
- just

## 기억할 것

평소에는 이것만 기억하면 됩니다.

```bash
cd /Users/tearess-mac/gpters/voicebox
just dev-web
```

그리고 브라우저에서 엽니다.

```text
http://localhost:5173/
```
