2023년 8월 1일

문제발생 : 며칠 전 "iterm2, oh-my-zsh" 를 설치하고부터 기존에 사용하던 커맨드를 입력할 때마다 
        "zsh: command not found: ..." 라는 메시지가 나왔다.

원인 : 기존에 사용하던 쉘은 "Bash"인데, oh-my-zsh를 설치하며 "Zsh"쉘로 활성화 되면서 PATH 
        변수 설정과 관련하여 해당 문제가 발생.

해결방법 :  기존 Bash 쉘에서는 잘 작동하던 명령어를 Zsh에서도 사용하고 싶다면, Zsh의 PATH에 
        기존 Bash 쉘의 PATH 값을 추가해야한다.
        
        1. " 터미널: echo &PATH " - 명령어 실행하여 기존 BASH 쉘의 PATH 변수 확인.
            결과 : /usr/.../bin 

        2. " .zshrc " - $HOME에 있는 숨긴 파일 찾기

        3. 파일 처음 열었을시 맨 위.
# If you come from bash you might have to change your $PATH.
# export PATH=$HOME/bin:/usr/local/bin:$PATH 

# Path to your oh-my-zsh installation.
# ..생략..
        이처럼 "export PATH=$HOME/bin:/usr/local/bin:$PATH" 부분을 1번에서 확인한 값으로 변경해야됨.

        export PATH="'여기에 1번 값 넣기':$PATH" => export PATH="/usr/.../bin:$PATH"

        4. 파일 수정 부분 "# export PATH=$HOME/bin:/usr/local/bin:$PATH"
# If you come from bash you might have to change your $PATH.
export PATH="/usr/.../bin:$PATH"

# Path to your oh-my-zsh installation.
# ..생략..
        위처럼 주석을 지우고 문장도 수정 변경 저장

        5. " 터미널: source ~/.zshrc " - 명령어 실행
        
        6. 해결
--------------------------------------------------------------------------

        + 나는 flutter의 경로가 $HOME/development/ 파일안에 flutter파일이 있기에 .zshrc 파일 추가 변경해야됨.
        
# If you come from bash you might have to change your $PATH.
export PATH="/usr/.../bin:$PATH"
export PATH="$HOME/development/flutter/bin:$PATH"

# Path to your oh-my-zsh installation.  
        
        저장 후 닫고 터미널에 source ~/.zshrc 명령어 실행하여 해결.








