---
title: "Manim Seris 01: Manim 설치 및 개발 환경 세팅 with VSCode (MacOS)"
excerpt: "Manim은 수학 그래프나 애니메이션을 만들 수 있게 해주는 파이썬 라이브러리이다."

categories:
  - Manim
tags:
  - [Manim, MacOS]

permalink: /Manim/install-manim-mac/

toc: true
toc_sticky: true

date: 2024-07-08
last_modified_at: 2024-07-09
---

해당 포스트는 MacOS에서 Manim을 설치하는 방법에 대한 포스트입니다. Window 운영체제의 경우 Manim Community 에서 Installation > Windows 메뉴를 확인하면 됩니다.
{: .notice--info}

이 01 시리즈에서는 수학 애니메이션 제작 라이브러리인 Manim 설치와 개발 환경 세팅 방법에 대해 다룰 것인데요. 기본적으로 각 운영체제에 맞는 Manim을 설치하기 위한 가이드는 [Manim Community 사이트](https://www.manim.community) 에 쉽게 설명이 되어 있습니다. 가이드를 참고해서 Manim 을 설치해볼 것입니다. 

참고로 pip3, Python은 미리 설치되어 있어야 합니다. 터미널에 `python --version` 을 입력하여 설치되어 있는지 확인해줍니다. 만약 설치되어 있지 않다면 설치해주세요! 또한, Manim을 사용하기 위해서는 파이썬 버전이 3.8 이상이여야 하기 때문에 파이썬 버전이 3.8 미만이신 분들은 파이썬 버전을 업그레이드하셔야 합니다.

pip3, Python 설치의 경우 다음 사이트를 참고해볼 수 있습니다.

**Python**
- [python 설치 공식 사이트](https://www.python.org/downloads/)
- `python --version` 을 입력했을 때
**zsh: command not found: python (Mac OS)**
다음과 같은 오류가 발생하는 경우 
[zsh: command not found: python (Mac OS) 해결](https://kingnamji.tistory.com/60)

**pip3**
- [macOS에 pip3 설치](https://www.delftstack.com/ko/howto/python/python-install-pip3-mac/#get-pippy파일을-사용하여-mac에-pip3-설치)
- pip3 명령어를 사용할 때 
**errer: externally-managed-environment (macOS)**
다음과 같은 오류가 발생하는 경우
[errer: externally-managed-environment (macOS) 해결](https://blog.naver.com/b14nc4/223418048502)


---


### 🔎 Manim 이란?

Manim 이 무엇인지에 대해서 글로 설명하는 것보다는 영상으로 봤을 때 단번에 이해할 수 있는데요.

![embedding](/assets/images/posts_gif/manim/embedding.gif)

다음은 3Blue1Brown 영상 - Attention in transformers, visually explained. Chapter 6, Deep Learning 중 임베딩을 표현하는 부분입니다. 위를 살펴보면 수학(e.g. 행렬 값)적 접근과 그래픽적 접근을 동시에 함으로써 접근 간의 간격을 줄이고 임베딩을 더욱 더 효과적으로 설명하고 있습니다. 

이처럼 Manim은 복잡한 기술 개념을 지루하면서 직관적이지 못한 설명을 하는 것에서 벗어나 애니메이션화를 통해 재밌으면서도 직관적으로 설명하는 것을 가능하게 해줍니다.

제가 Manim 에 대해 관심을 가지게 된 계기는 다름아닌 3Blue1Brown 유튜브 영상을 접하고 나서인데요. 처음 영상으로 무엇을 접했는지는 가물가물하지만 그 영상미에 매료되었던 그 감정은 아직까지 기억이 남는 것 같습니다. 

---

### ⚙️ Manim 설치 (개발 환경 세팅)

![install](/assets/images/posts_img/manim/install.png)

그럼 이제 본격적으로 Manim 을 설치하는 방법에 대해 알아봅시다. 저의 경우 MacOS 에서 Manim 을 설치할 것이기 때문에 다음 Installation 메뉴에서 에서 [macOS 가이드](https://docs.manim.community/en/stable/installation/macos.html)를 참고해보겠습니다.

#### Step1. Homebrew 설치

![homebrew](/assets/images/posts_img/manim/homebrew_description.png)

우리는 brew 명령어를 사용해서 manim을 설치하기 위해 패키지 관리자인 homebrew를 설치할 것입니다. homebrew 없이도 모든 종속성을 설치할 수 있으나, homebrew를 사용하면 설치하는 프로세스가 훨씬 쉬워집니다. 실제로 직접 종속성을 가지는 패키지나 라이브러리(FFmpeg, py3cairo etc..)를 직접 설치하는 과정에서 온갖 오류가 발생해서 그 해결하는 과정이 빡셌었습니다... 근데 바로 이 가이드를 보고 오류 없이 몇 초만에 설치가 되는 것을 보고 허탈했었죠..

![homebrew homepage](/assets/images/posts_img/manim/homebrew_homepage.png)

homebrew를 설치하기 위해서 [homebrew 홈페이지](https://brew.sh)에 들어갑니다. 

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
macOS의 경우 **터미널**에서 위 명령어를 입력해주면 됩니다. 

![install step1](/assets/images/posts_img/manim/install_brew_0.png)
설치를 진행하다가 "Press RETURN/ENTER" 이라는 문장이 뜨면 둘 중 하나 클릭해주면 됩니다.

![install step1 error](/assets/images/posts_img/manim/install_brew_0_warning.png)

위 화면과 같이 뜨면 설치가 완료된 것입니다. 하지만... 불안하게 "Warning: /opt/homebrew/bin is not in your PATH." 가 뜨는데요. 실제로 다음 step 인 `brew install py3cairo ffmpeg` 를 터미널에 입력하면 

**zsh: command not found: brew** 

다음 문구가 뜨면서 오류가 발생합니다.. 이는 다름이 아니라 저의 맥북이 M1 chip 이여서 발생한 문제입니다. 그 이유는 homebrew가 기존의 경로 **/usr/local/...** 가 아닌 **/opt/homebrew/** 로 설정되어서 생기는 에러라고 합니다. [1]

이를 해결하기위해 다음 명령어를 터미널에 입력해줍니다.


**방법1. vi를 이용한 해결**
```bash
vi ~/.zshrc
```
```
// M1 칩인 경우
export PATH=/opt/homebrew/bin:$PATH

// M1 칩이 아닌 경우
export PATH=/usr/local/bin:/usr/local/sbin:$PATH
```
vi ~/.zshrc 를 입력하면 .zshrc 파일을 열 수 있으며 
i 키를 눌러 입력 모드로 전환하고 파일을 편집할 수 있습니다.
편집이 끝난 후 Esc 키를 눌러 명령 모드로 돌아가고 :wq를 입력하여 파일을 저장하고 종료해줍니다.



**방법2. 명령어를 이용한 해결**
```bash
echo 'export PATH="/opt/homebrew/bin:$PATH"' >> ~/.zshrc
```
방법2 같은 경우는 그냥 위 명령어를 터미널에 입력해주기만 하면 끝입니다.

여기서 끝이 아니라 
```bash
source ~/.zshrc
```
위 명령어를 통해서 ~/.zshrc 파일을 다시 읽고 실행하도록 합니다. 이를 통해 .zshrc 파일에 있는 설정을 즉시 반영하게 되며 그 결과 zsh shell이 brew command를 찾아 실행할 수 있게 됩니다.

![install check](/assets/images/posts_img/manim/homebrew-check.png)

마지막으로 잘 설치되었는지

```bash
brew --version
```

위 명령어를 통해서 확인해주면 homebrew 설치는 끝이 나며 본격적으로 brew 명령어를 쓸 수 있게 됩니다!



#### Step2. 필요한 종속 라이브러리 설치

```bash
brew install py3cairo ffmpeg
brew install pango pkg-config scipy      
pip3 install manim
```
터미널에 위 명령어를 순서대로 입력해주면 됩니다. 다만 주의해야될 부분이 있는데요.

`brew install pango pkg-config scipy`

위 명령어의 경우 Apple Silicon 기반 머신(즉, M1 칩 또는 유사한 칩)일 때 입력해줘야하는 추가적인 명령어입니다. 따라서 Apple Silicon 기반 머신이 아니면 명령어를 입력할 필요가 없습니다.

혹시나 만약 사용 중인 프로세서를 모를 경우에 "Apple 메뉴 > 이 Mac에 관하여" 에서 칩 옆에 있는 항목에서 확인할 수 있습니다.

![chip](/assets/images/posts_img/manim/mac-chip.png)

다음과 같이 창이 뜨게 되며 저의 경우 M1 chip 에 해당하기 때문에 터미널에 명령어를 입력해주었습니다.


#### Step3. (선택) 종속 라이브러리 설치
```bash
brew install --cask mactex-no-gui
```
다음 명령어의 경우 방정식 렌더링을 위해 LaTeX도 설치해야 되기 때문에 진행하는 것입니다. 따라서 LaTeX를 사용하지 않을 거라면 설치할 필요는 없습니다. 

---

### 🧪 VScode 에서 Manim 제대로 동작되는지 테스트

Manim 이 제대로 동작되는지 테스트해보기 위해서 VScode 에서 간단한 Manim 코드를 작성해봅시다.


#### Step1. Manim 개발 환경 세팅

VScode Extensions 메뉴에서 Python, Manim sideview 프로그램을 설치해줍니다. 


![chip](/assets/images/posts_img/manim/vscode_1.png)

설치하려면 다음과 같이 "Manim Sideview" 라고 검색한 후 install 버튼을 눌러주면 됩니다.

![chip](/assets/images/posts_img/manim/vscode_2.png)

위 화면과 같이 뜨게 되면 프로그램 설치가 완료가 된 것입니다.

#### Step2. Manim 코드 작성 

![chip](/assets/images/posts_img/manim/vscode_3.png)

다음과 같이 test.py를 생성해주고 저장해줍니다. 코드는 아래 코드를 복사하시면 됩니다! [2]

```python
from manim import *

class hello(Scene):
    def construct(self):
        t = Tex("Hello")
        self.play(Write(t))
        self.wait(3)

```

만약 이때
![chip](/assets/images/posts_img/manim/vscode_6.png)
다음과 같이 Manim 라이브러리가 인식이 안된다면 이것은 Interpreter 문제입니다. 위 이미지에서 오른쪽 하단을 살펴보시면 3.12.4  64-bit 라고 되어 있는데 이 부분을 클릭해줍니다.

![chip](/assets/images/posts_img/manim/vscode_7.png)
클릭해주게 되면 다음과 같이 Interpreter 선택 창이 뜨게 되고 여기서 **/opt/homebrew/bin/python3** 경로에 해당하는 Interpreter 을 선택해줍니다. 

#### Step3. 코드 실행

![chip](/assets/images/posts_img/manim/vscode_4.png)
VSCode 에서 실행 버튼 '▷' 을 눌러주게 되면 Manim 코드 media가 생성됩니다.

![chip](/assets/images/posts_img/manim/vscode_5.png)
이후 실행 버튼 '▷' 옆에 있는 빨간색 버튼을 눌러주면 오른쪽에 Manim Sideview 를 통해서 생성된 영상을 확인할 수 있습니다.

---

### 마무리 
이때까지 MacOS에서 Manim을 설치하고 VSCode를 사용하여 개발 환경을 설정하는 방법에 대해 알아보았습니다. 다음 포스팅에서는 본격적으로 Manim을 사용하여 애니메이션을 만드는 방법을 다룰 예정입니다.

궁금한 점이나 추가적인 도움이 필요하면 댓글로 남겨주세요. 감사합니다:)
그리고 잘못된 내용 피드백 댓글도 환영합니다!

---

[1] [Mac Error | Homebrew 설치 후 zsh: command not found: brew 경로 설정 오류 해결](https://psip31.tistory.com/119)
[2] [How To Install Manim On Mac (Step By Step)](https://www.youtube.com/watch?v=sX8BpkGsLIk)