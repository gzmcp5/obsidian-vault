
# 터미널 단축키 설정

Automator 실행 > 새로운 문서 > 빠른 동작 > AppleScript 실행 > 스크립트에 다음 내용 복사

```
on run {input, parameters}
    tell application "Terminal"
        if it is running then
            do script ""
        end if
        activate
    end tell
end run
```



iTerm의 경우,

Automator 실행 > 새로운 문서 > 빠른 동작 > 응용 프로그램 실행 > iTerm 선택
Command + s 로 저장
시스템 환경설정 > 키보드 > 단축키 > 서비스 > 단축키 설정



## Homebrew 설치
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"

echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /Users/giljong-in/.zprofile

eval "$(/opt/homebrew/bin/brew shellenv)"
```

## zsh 설치 및 세팅

- zsh 설치 (shell 이름 확인 : echo $0)
```
brew install zsh git wget curl
```

- 설치경로 확인
```
which zsh
#=> /usr/bin/zsh
```

- 기본 sh 변경
```
chsh -s $(which zsh)
```

- oh-my-zsh 설치
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
vim ~/.zshrc

테마를 agnoster로 변경
```

- 폰트 설치
```
git clone https://github.com/powerline/fonts.git fonts
./install.sh
cd ..
rm -rf fonts 

# iTerms2 - Settings - Profiles - Text - Font - Ubuntu Mono Derivative Powerline
```

## 플러그인 설치
  
  - Auto suggestions
```
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

- Syntax highlighting
```  
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

- fzf
```  
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install
```

- vim ~/.zshrc에 추가
```  
plugins=(git zsh-autosuggestions zsh-syntax-highlighting fzf)
```


## Iterm2 설치

https://iterm2.com/downloads.html

iTerm에서 Command + ,(콤마) > Profile > Text > ‘Ubuntu Mono derivative Powerline’으로 폰트 변경
