# 파이썬 초보자를 위한 실습 환경 준비 가이드

안녕하세요! 험블데이터 워크샵에 오신 것을 환영합니다.
워크샵 당일 실습에 집중하실 수 있도록, 약 20분만 투자해서 파이썬 실습 환경을 미리 준비해 주세요.

**가장 먼저 할 일:**
워크샵 실습에 필요한 파일들이 GitHub 저장소에 있습니다.
[여기](https://github.com/HumbleData/beginners-data-workshop/archive/refs/heads/korean.zip) 을 눌러 파일 전체를 다운로드하고, 원하는 폴더에 압축을 풀어주세요.

숙련자는 https://github.com/HumbleData/beginners-data-workshop/ 의 korean branch 를 찾아주세요.


---

## 💻 1. 왜 '가상환경'부터 만드나요? (비유로 설명하기)

파이썬으로 멋진 걸 만들기 전에, 딱 하나 '준비운동'이 필요합니다. 바로 **'프로젝트 전용 방'**을 만드는 일입니다.

* **이걸 왜 하나요?**
    * 여러분의 컴퓨터를 '커다란 아파트'라고 생각해 보세요.
    * A 프로젝트('데이터 분석 공부')와 B 프로젝트('간단한 게임 만들기')를 동시에 한다고 상상해 봅시다.
    * 모든 도구(레고, 물감, 가위)를 거실 바닥(여러분의 컴퓨터)에 다 쏟아 놓고 쓰면 어떻게 될까요?
        * A 프로젝트에 쓰던 1번 레고가 B 프로젝트의 2번 물감이랑 섞여서 엉망이 되겠죠?
        * 나중에 A 프로젝트를 다시 하려는데, B가 쓰던 2번 물감 때문에 1번 레고가 망가져서 실행이 안 될 수도 있어요.

* **'가상환경(Virtual Environment)'이란?**
    * 이런 재앙을 막기 위해, **'프로젝트마다 깨끗한 개인 방'**을 하나씩 주는 거예요.
    * '데이터 분석 공부' 방에는 데이터 도구만, '게임 만들기' 방에는 게임 도구만 둡니다.
    * 서로 섞이지 않으니 깨끗하고, 한쪽 방이 지저분해져도 다른 방은 안전하죠!

* **오늘 우리가 쓸 도구**
    * `Miniconda`: 방 관리, 도구 설치는 물론, 아파트(컴퓨터) 전체를 관리해주는 **만능 관리사무소** 🧑‍🔧.  (이걸로 먼저 시도해 볼게요!)
    * `uv`: 방을 만들고 도구를 설치하는 **최신형 초고속 엘리베이터** 🚀. 엄청 빠르고 간편합니다.

---

## 🧑‍🔧 2. 'Miniconda'로 설치하기 

### 1단계: Miniconda 설치하기

1.  [Miniconda 설치 페이지](https://www.anaconda.com/download/success) 으로 이동합니다. 
2.  자신의 운영체제(Windows/macOS)에 맞는 Miniconda 최신 버전을 우측에서 다운로드하여 설치합니다.
    1. [윈도우](https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe)
    2. [맥 M1,M2 이상](https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.pkg)
    3. [인텔 맥](https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.pkg)
3.  설치 중 묻는 질문은 대부분 기본값(Enter)으로 넘어가시면 됩니다.

### 2단계: '터미널' 열기

  * **Windows:** 시작 메뉴에서 `Anaconda Prompt` 를 검색해서 실행합니다.
  * **macOS:** `Terminal`을 엽니다.

### 3단계: '프로젝트 방' 만들고 들어가기

1.  **방 만들기 (`conda create`):**

      * `humble`이라는 이름의 방을 만들고, 파이썬 3.10 버전을 지정해 줍니다.

    <!-- end list -->

    ```bash
    conda create -n humble python=3.10
    ```

      * 중간에 `[(a)ccept/(r)eject/(v)iew] 라고 물어보면 `a`를 누르고 Enter를 칩니다. 3번 물어봅니다.
      * 중간에 `Proceed ([y]/n)?` 라고 물어보면 `y`를 누르고 Enter를 칩니다.

2.  **방 들어가기 (`conda activate`):**

    ```bash
    conda activate humble
    ```

      * **(성공하면\!)** 명령어 맨 앞에 `(humble)` 이라고 표시가 바뀝니다.

### 4단계: 도구 설치하기 (Conda 방식)

1.  **워크샵 자료가 있는 폴더로 이동합니다.** 

      * `cd C:\...` (Windows 예시)
      * `cd /Users/...` (macOS 예시)

2.  **도구 설치하기:**

      * Conda는 `requirements.txt` 파일을 이용해 설치하는 명령어가 있습니다.

    <!-- end list -->

    ```bash
    pip install -r requirements.txt
    ```

### 5단계: 방 나오기 (Deactivate)

여기까지 준비해오시면 제일 좋습니다.

```bash
conda deactivate
```

## 🚀 3. 'uv'로 초고속 설치하기

`uv`는 정말 빠르고 쉬운 파이썬을 관리하기 위한 최신 도구입니다.

### 1단계: '터미널' 열기 (명령어를 입력할 창)

앞으로 모든 작업은 '명령어 창'에서 합니다.

* **Windows:**
    1.  시작 버튼 클릭
    2.  `PowerShell` 이라고 검색해서 `Windows PowerShell` 에 마우스 우측 클릭후에 "관리자 권한으로 실행" 을 누릅니다. (파란색 배경의 창)
* **macOS:**
    1.  `Cmd (⌘)` + `Space` 키를 눌러 Spotlight 검색을 엽니다.
    2.  `Terminal` 이라고 검색해서 실행합니다. (검은색 배경의 창)

### 2단계: 'uv' 설치하기

방을 만드는 도구(`uv`)를 설치합시다. 아래 명령어를 '터미널'에 복사 + 붙여넣기 하세요.

* **Windows (PowerShell에서):**
    ```powershell
    powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
    ```
    실행후에 창을 끄고 시작버튼을 누르고 cmd 를 검색해서 앞으로는 "명령 프롬프트" 창을 실행한다.
* **macOS (Terminal에서):**
    ```bash
    curl -Lsfs [https://astral.sh/uv/install.sh](https://astral.sh/uv/install.sh) | sh
    ```

### 3단계: '프로젝트 방' 만들고 들어가기

1.  **워크샵 자료가 있는 폴더로 이동합니다.**
    * (아까 GitHub에서 다운로드하고 압축 푼 그 폴더입니다. 예: `beginners-data-workshop-main`)
    * `cd` 명령어를 씁니다. (`cd`는 'Change Directory'의 약자예요)
    * `cd C:\Users\YourName\Documents\beginners-data-workshop-main` (Windows 예시)
    * `cd /Users/YourName/Documents/beginners-data-workshop-main` (macOS 예시)
    * **(팁: `cd `를 치고 한 칸 띈 다음, 폴더를 터미널 창으로 끌어다 놓으면 주소가 자동 완성됩니다!)**

2.  **방 만들기 (`uv venv`):** (터미널에서 해당 폴더에 들어온 상태로 실행)
    ```bash
    uv venv humble --python 3.10
    ```
    * 이 명령을 실행하면 현재 폴더에 `humble` 라는 이름의 '비밀 방'이 생깁니다.

3.  **방 들어가기 (Activate):**
    * **Windows (Commandline):**
        ```cmd
        humble\Scripts\activate
        ```
    * **macOS (Terminal):**
        ```bash
        source .venv/bin/activate
        ```
    * **(성공하면!)** 명령어 맨 앞에 `(humble)` 라는 표시가 생깁니다. 이제 '방' 안에 들어오신 겁니다!

### 4단계: '방' 안에 도구 설치하기

워크샵에 필요한 도구 목록(`requirements.txt`)을 보고 한 번에 설치합니다.

```bash
uv pip install -r requirements.txt
```

### 5단계: 방 나오기 (Deactivate)

워크샵이 끝나고 방에서 나올 땐 이 명령어를 쓰세요. 

```bash
deactivate
```