# Github 사용법

- Git hub : 분산형 버전 관리 시스템
    - 브랜치 : 브랜치에서 실험적으로 개발 후 merge 가능
    - 객체: Commit > Tree > Blob
        • Blob: 파일 하나의 내용에 대한 정보 <-vim으로  파일 수정
        • Tree: Blob이나 subtree의 메타데이터(디렉토리 위치, 속성, 이름 등) <- $git add로 스테이지에 올리기 
        • Commit: 커밋 순간의 스냅샷<- $git commit으로 local repository에 올림
    - commit 한 단위 = 작업의 한 단위 = 하나의  동작
    - push : 하나의 기능이 모두 구현 되었을 때 한 번에 하는 것을 권장

- Shell :  커널과 사용자를 이어주는 소프트웨어. 명령어로 컴퓨터에게 작업을 지시하는 걸 도와주는 프로그램. vs code의 power shell에서도 동작
- CLI(Command-Line Interface / Character User Interface) : 글자를 입력하여 컴퓨터에 명령을 내리는 방식

1. Shell 열기 : git bash  오픈
2. 원하는 디렉토리로 이동 
    - $pwd 현재 디렉토리 확인
    - $ls : list segments. 디렉토리 내의 목록 확인
    - $cd 폴더명: change directory
    - $mkdir 폴더명: make directory 폴더 생성
3. 깃허브 환경 시작
    - 깃허브 오픈해서 시작하기 : $git init
        - 초기 설정
            - $git config —global core.autocrlf true(input)  
            - $git config —global user.name ‘사용자명’  : 아이디 설정
            - $git config —global [user.email](http://user.email) : ‘이메일’ 이메일 설정
            - $git config --global core.pager "cat”  : viewer 설정
            - $git config --global core.editor "vim” : vim으로 입력하기로 설정
            - $git config —global —list : 설정값 확인
            - $vi ~/.gitconfig : 설정 파일 수정
    - 복제 및 repository에서 가져오기
        1. github repository 내부 오른쪽 ‘code’버튼을 눌러 주소 복사
        2. 터미널에서 파일을 열 디렉토리로 이동
            - $dir  : 현재 폴더 내부의 네임스페이스 확인
            - $cd .. : 상위 디렉토리로 진입
            - #cd ./ : 현재 디렉토리 명시
            - $cd ./폴더명/  : 폴더로 진입
            - $code . -r  : vs code에서 코드 실행
        3. $git clone 주소 위치: 복제
        4. $git checkout -t origin 브랜치명  # 원하는 브랜치 가져오기(기본적으로 master만 있음)
        5. $git branch -d 브랜치명  # 브랜치 삭제(해당 브랜치 밖에서 삭제 가능)
4. 브랜치 진입(VS code 왼쪽 하단/Shell 표시됨) : 기본 브랜치 master
    1. $git branch : 브랜치명  : 브랜치 생성
    2. $git branch  : 브랜치명 확인
    3. $git checkout 브랜치명  : 브랜치 내로 진입
    4. $git checkout -b 브랜치명  : 브랜치 생성과 동시에 진입
5. 버전 관리 방법
    1. 추적 제외 정보 설정
        1.$touch .gitignore : gitignore파일 생성
        2.$vim .gitignore : 파일 열어서 gitignore.io 사이트에서 생성한 무시할 파일 정보 붙여넣기. 그외 폴더나 파일명 기입.(한 번 commit한 파일은 ignore 불가능)
        3.$ls -a : all list 확인(앞에 .이 붙은 보이지 않는 파일까지 보임)
    1. $git status  : stage에 올라와 있는 파일 확인(빨강 : 추적 안 됨 / 초록 : 추적됨)
    2. 스테이지로 올리기
        $git add 파일명: 스테이지로 파일 올리기  
        $git .  : 현재 디렉토리 전체를 스테이지에 올리기(권장하지 않음)
        $git restore --staged 파일명 : 스테이지로 올린 것 취소
        (VS code) 파일명 오른쪽 표시자 : 수정된 파일 M, 새로 생성된 파일 U, 버전 관리된 파일 A
    3. #git commit : 로컬 registory에 저장. commit 설명에 들어가야 할 것들은 다음과 같다.
            header 'prefix : 구/절' ->필수
                - feat: 기능 개발 관련
                - fix: 오류 개선 혹은 버그 패치
                - docs: 문서화 작업
                - test: test 관련
                - conf: 환경설정 관련
                - build: 빌드 작업 관련
                - ci: Continuous Integration 관련
                - chore: 패키지 매니저, 스크립트 등
                - style: 코드 포매팅 관련
            body  상세내용
            footer  부가 정보(이전 버전과 달라진 내용 따위)
        $git commit -m "버전이름" : vim으로 열지 않고 저장. 권장하지 않음
    4. commit 사항 수정
        - $git commit --amend : 바로 직전 commit 설명 수정
        - $git reset —hard HEAD~숫자  : 돌아가고 싶은 만큼의 숫자 입력하여 버전 되돌리기
        - $git reset —hard ORIG_HEAD  : 버전 되돌리기한 것을 다시 되돌리기(기존의 head로)
    5. $git log  : 버전 기록 확인 (HEAD : 최신 버전)
5. repository로 보내기 (github에 repository를 만들고 주소 복사(licence는 MIT가 좋음)
    1. $git remote add origin 주소 : repository에 연결
    2. $git push origin 브랜치명  : 업로드(기존 repository 안에서 설치하지 않도록 주의)

- 파일과 폴더 관리
    - $cat : 파일 내용 프린트해서 보기
    - $rm 파일명 : 파일 삭제
    - $rm -rf 폴더명 : 폴더 삭제 recursive function
    - $mv 원래위치/파일명 옮길위히 : 지정 폴더로 파일 이동
    - $mv 원래파일명 바꿀파일명 : 파일명 변경
    - $mv 파일명 변경할이름 : 파일명 변경
    - $cp 원래위치/파일명 복사할위치 : 지정 위치로 파일 복사
    - $cp 원래위치/파일명 복사할위치(+)변경할이름 : 이름을 변경하며 파일 복사
    - 주의 사항
        - 공백으로 명령어 구분을 하기 때문에 파일명에 공백 넣지 말자
        - *.py  : 모든.py 별표(wildcard,asteriscus)의 위치는 다양하게 적용해서 사용해볼 수 있음
        - [a-i]* : a부터 i까지 모든 문자로 시작하는 글자
        (remove : 논리적 삭제 / delete : 물리적 삭제)

- vim으로 파일 편집 : cui가 gui보다 더 빠름. 모든 걸 키보드로 입력해야 함. 비어있으면 ~로 차있음.
    $vim 파일명 : vim으로 파일 열기
    $vi 파일명 : vim으로 파일 열기
    - mode : 모드 진입은 normal에서 가능
        - normal   ‘esc’
        - insert   ‘i’
        - visual   ‘v’
        - commend   ‘:’
            :wq 저장하고 나가기
            :q 그냥 나가기
            :q! 저장하지 않고 나가기(override)
            :w : write
            :{num} : Go to {num}th line
        - vim을 켜놓고 그냥 껐을 때 :  rm ~/파일명.swp (swap파일 삭제)
        - normal 모드 명령어
            h j k l : left, down, up, right
            d : delete
            dd : delete a line
            y : yank
            yy : yank a line
            p : paste
            u : undo
            a : append
            A : append from end of line
            o : open line(under)
            O : open line(upper)
            H : move to the top of the screen
            L : move to the bottom of the screen
    [vim cheet sheet]("https://external-preview.redd.it/iigrixvxp5aYN9ox7Gr1dfI_rhLRotWlLsCafjJqjEQ.png?width=1080&crop=smart&auto=webp&s=78fdf6e9b02082dda1c810224a9e3940f2a55197")

- 메인 md 파일  README.md : 프로젝트의 첫인상이므로 신경 써야 함

- jupyter notebook 파일
    1. jupyter notebook에서 편집 후 저장
    2. shell에서 올려주기
        1. $git add 파일명.ipynb
        2. $git commit
        3. $git push origin 브랜치명
    4. repository에서 commits 기록 비교 확인 가능

- pre-commit 설정 방법 : commit하기 전 파일의 오류를 잡아주는 기능 'https://pre-commit.com'
    1. $pip install pre-commit :  pre-commit 파이썬에 설치(한 번만 설치하면 됨)
    1. $pre-commit sample-config > .pre-commit-config.yaml: 프로젝트 시작할 때마다 정의
    3. $vi .pre-commit-config.yaml : 파일 열어서 id : 뒤에 기능이름 추가. repo주소가 다르면 repo 추가해주고 다음 줄에 id: 추가
    4. $pip install hook이름 : 새롭게 추가할 훅 설치
    2. $pre-commit run : .yaml에 추가한 게 있으면 설치해줘야 함 
    1. $pre-commit run -a : 설치 사항 테스트
    1. $pre-commit install : 위의 설정을 commit할 때마다 실행하도록 설정
    1. pre-commit에 걸려서 fail 메시지가 뜨면 한 번 더 add 하여 pre-commit이 수정한 파일을 통합해주면 됨

- 브랜치 병합
    1. 브랜치 업데이트 내용을 repository로 업로드
    2. repository > Pull requests > ’New pull request’ 버튼
    3. 화살표 오른쪽에 병합될 브랜치로 설정 > ‘Create pull request’버튼
    4. Pull requests 옆에 숫자가 하나 증가. (open 상태) > ‘Merge pull request’ 버튼 > ‘Confirm Merge’ 버튼 (merged 상태)

- 버전 충돌 상황
    1. push를 하면 ‘reject’ 당함
    2. git pull origin master  # git의 저장 내용 당겨오기→’conflict’ 발생→ 로컬의 내용과 비교하며 내용 선택해서 저장

- $git blame 파일명 : 누가 언제 파일을 수정했는지 확인하고 비난할 수 있음
- Netlify : github의 파일을 자동으로 웹페이지로 만들어주는 사이트
