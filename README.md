### Homebrew

https://brew.sh/index_ko



> Homebrew 은 macOS 용 패키지 관리자입니다.
>
> homebrew 을 설치하기 위해서는 macOS에 command line tools가 설치되어 있어야 합니다.



1. Appstore에서 Xcode를 설치합니다.

2. 터미널에서 아래 코드를 실행하여 homebrew을 설치합니다.

   ~~~
   ~/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
   ~~~

3. ```$ brew doctor``` 을 실행하여 에러가 있는 경우 PATH 해줍니다. (에러가 없으면 pass~~) 

   여기서는 zshell을 사용할 것이기 때문에 .zshrc 파일을 열어 PATH 설정 부분에 추가해줍니다. 

   ~~~zsh
   export PATH="/usr/local/sbin:$PATH" 
   ~~~

   PATH를 추가해 주었으면 ```$ source ~/.zshrc``` 실행하여 파일을 갱신해 줍니다.

   > 패키지 설치 후 brew link를 먼저 수정하라는 에러가 뜨는 경우 ```$ brew link {package_name}``` 해줍니다. 





### iTerm2 & Oh_My_Zsh

iTerm2: https://iterm2.com

Oh My ZSH: https://ohmyz.sh



> 아래 링크에서 폰트를 내려받아 설치합니다.

[Meslo LG M for Powerline 폰트](https://github.com/powerline/fonts/blob/master/Meslo%20Slashed/Meslo%20LG%20M%20Regular%20for%20Powerline.ttf)



>  ```shift + command + . ``` 로 숨겨진 파일이 파인더에 표시되도록 합니다.



~~~ console
# iTerm2 설치
$ brew cask install iterm2

# zsh 설치
$ brew install zsh

# zsh 설치 경로 확인
$ which zsh

# 기본쉘을 zsh로 바꾸어 줍니다.
$ cash -s $(which zsh)

# Oh My Zsh 설치
$ sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

# Powerlevel9k 테마팩 설치
$ git clone https://github.com/bhilburn/powerlevel9k.git ~/.oh-my-zsh/custom/themes/powerlevel9k

# zshell 설정 파일을 열고 테마를 powerlevel9k 으로 변경해 줍니다.
$ vim ~/.zshrc
ZSH_THEME="powerlevel9k/powerlevel9k" 
~~~



- iTerm2.app을 실행한 후 Perferences > Profiles > Colors 탭으로 이동합니다.
- 오른쪽 하단의 Presets... 리스트에서 Solarized Dark 컬러를 적용합니다.
- Profiles > Text 탭으로 이동합니다.
- change Font 버튼을 클릭하고 위에서 설치한 Meslo LG M for Powerline 폰트를 선택해 줍니다.
- echo "\ue0b0 \u00b1 \ue0a0 \u27a6 \u2718 \u26a1 \u2699"를 입력해 깨진 글자가 없으면 잘 된것입니다.



~~~zsh
# 터미널에서 계정 이름을 제거합니다.
$ echo "prompt_context () { }" >> ~/.zshrc && source ~/.zshrc
~~~





### Visual Studio Code

https://code.visualstudio.com



> 설치 및 확장기능

~~~zsh
# homebrew VSC 설치
$ brew cask install visual-studio-code

# VSC 확장프로그램 설치
Git

# VSC 확장기능 설치
Sublime Text Keymap
React Extension Pack
Prettier Javascript Formater
Python Extension Pack
~~~



> iTerm2를 VSC에서 사용하려면 VSC 설정 파일을 열어서 아래에 해당하는 기본설정을 덮어 씁니다.

~~~zsh
# Command + , 을 눌러 User Settings 파일을 엽니다.
# '기본 사용자 설정'에서 아래 항목을 찾아 '사용자 설정'으로 덮어 씁니다.
"terminal.external.osxExec": "iTerm.app",
"terminal.explorerKind": "external",
"terminal.integrated.fontFamily": "Meslo LG M for Powerline",
~~~





### .zshrc 에 Python3, pip3 별칭 등록

> MacOS에는 Python2.7이 내장되어 있습니다. 버전을 높여도 Mac은 여전히 Python2를 Default로 유지하기 때문에 Python3을 Default로 사용하기 위해서는 ~/.zshrc을 이용해 zshell이 항상 Python3를 사용하도록 해주어야 합니다.
>
> 이 설정은 python3 을 python으로 사용할 수 있도록 해줍니다.

~~~zsh
$ vim ~/.zshrc

# 파일 하단의 Example alias 아래에 다음을 입력
$ alias python='python3'
$ alias pip='pip3'

# 시스템 등록
$ source ~/.zshrc
~~~





### Android StudioGenymotion

https://developer.android.com/studio/



> 이 소프트웨어는 PC에서 스마트폰 연동 없이 안드로이드를 이용할 수 있게 합니다. 
>
> VirtualBox라는 가상화 기술을 이용한 지니모션은 속도가 빠르고 무료로 사용할 수 있습니다.



~~~zsh
$ brew cask inatall android-studio
~~~





### expo(XDE)

https://github.com/expo/xde/releases



> 이 소프트웨어는 리액트 네이티브를 크로스 플랫폼으로 개발하기 위한 빌드 도구입니다.
>
> 네이티브 모듈을 보다 쉽고 편하게 사용할 수 있도록하며, 실제 기기에서 테스트가 가능한 XDE입니다.



~~~zsh
$ brew cask install expo-xde
~~~





### Postgres (Postgres.app / pgAdmin)

https://www.postgresql.org



> PostgreSQL은 객체-관계형 데이터베이스 관리 시스템(ORDBMS)의 하나 입니다.
>
> 소규모 단일 애플리케이션에서부터 많은 동시 접속자가 있는 대형 인터넷 애플리케이션에 이르기까지 여러 부하를 관리할 수 있으며 macOS 서버의 경우 기본데이터베이스로 사용되고 있습니다.



~~~zsh
$ brew cask install Postgres
~~~





### Nodejs & npm

Nodejs: https://nodejs.org/en/

npm: https://www.npmjs.com



> Nodejs는 Chrome V8 JavaScript 엔진으로 빌드된 JavaScript 런타임입니다.
>
> npm(Node Package Manager)은 JavaScript Program Language를 위한 패키지 관리자이며, nodejs의 기본 패키지 관리자 입니다. **Nodejs를 설치하면 함께 설치됩니다.**



~~~zsh
$ brew install node
~~~





### Yarn

https://yarnpkg.com/lang/en/



> 얀(Yarn)은 npm의 핵심 이슈를 해결하기 위한 새로운 패키지 매니져입니다. npm과 비교하여 빠르고 안정적이며 보안성이 뛰어납니다. 



~~~zsh
$ brew install yarn --without-node
~~~

nodejs가 설치되어 있을 경우 ``--without-node`` 옵션 으로 nodejs를 제외하고 설치합니다.





### Python3 & pip3 & pipenv

> 파이썬은 C언어로 구현된 고급 프로그래밍 언어로, 플랫폼이 독립적이며 인터프리터식 객체지향적 동적 타이핑(dynamically typed) 대화형 언어입니다. **C 컴파일러를 사용하기 위해 Xcode가 사전 설치되어 있어야 합니다.**

https://www.python.org

~~~zsh
# python 최신버전이 설치되며 pip도 함께 설치합니다.
$ brew install Python
$ python --version
~~~



> pip는 Python으로 작성된 패키지 소프트웨어를 설치, 관리하는 패키지 관리 시스템입니다. PyPI(Python Package Index)에서 많은 파이썬 패키지를 찾을 수 있습니다.

https://pypi.org/project/pip/

~~~zsh
# pip 버전 확인
$ pip -V
$ pip --version
~~~



> pipenv는 가상환경 패키지 설치 툴입니다.

https://docs.pipenv.org

~~~zsh
# pip를 사용해 pipenv를 설치합니다.
$ brew install pipenv
~~~



### Expo Client (iOS / Android)

> 이 소프트웨어는 앱 스토어 승인이나 Xcode 사용 없이 개발중인 앱을 바로 테스트할 수 있습니다

















