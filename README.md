## 리눅스 tutorial
### 0. 리눅스 환경 구축하기
- 리눅스를 직접 설치하는 것은 번거롭다. 따라서 웹 서비스를 이용해 즉각적으로 리눅스를 사용할 수 있도록 환경을 구축한다.
- 방법
    1. CodeOnWeb에서 실습환경을 구축한다. 좌측의 실행환경에서 Linux shell을 선택하면 linux사용환경이 구축된다.
    2. C9.io에서 linux환경을 구축한다.
    3. 가상머신을 이용한다.
### 1. 명령어(CLI환경 : command line interface, 명령어로 조작하는 환경)
- 명령어는 현재 디렉토리를 대상으로 하여 실행된다.
- 명령어(parameter를 이용해 해당 명령어의 실행 방식을 다룰 수 있다.)
    - ls : 현재 목록을 확인한다.(아래는 parameter)
        - -l : 현재 디렉토리의 파일 및 하위 디렉토리를 자세히 보여준다.
            - 제일 좌측의 d는 directory를 의미하며, -는 file을 의미한다.
            - 중간의 4096과 같은 숫자는 용량을 의미한다.
        - -a : .으로 시작하는 파일도 모두 보여준다.(.으로 시작하는 것은 숨김파일)
        - -S : file size에 따라 정렬한다.
    - pwd : 현재 위치를 확인한다.
    - mkdir directory_name : 지정한 name의 directory를 만든다.
    - touch 파일명 : 비어있는 해당 name의 file을 생성한다.
    - rm : 파일을 삭제한다.
    - cp : 파일을 복사한다.
    - mv : 파일을 이동시킨다., 파일 이름을 변경시킬 때도 이를 사용
    - cat file_name : 파일 이름을 출력
    - grep <정보> <파일명> : 특정 정보가 포함된 행을 찾는 명령
    - ps : 실행중인 process를 보여준다.
        - ps ax : 모든 프로세스를 볼 수 있다.(u까지 넣으면 자세하게 보여줌)
        - -o : 실행시 특정 칼럼만 출력시킬 수 있다.
    - history | awk '{a[$2]++}END{for(i in a){print a[i] " " i}}' | sort -rn | head -10 : 내가 쳤던 명령어 history를 빈도수에 따라 정렬해서 보여줌
- 명령어 사용법을 확인하는 방법
    - --help를 특정 명령어 뒤에 지정한다.
        - ex) `ls --help` : ls명령어의 manual을 확인가능
    - man
        - `man ls` 와 같이 사용한다.
        - 새로운 페이지로 들어가서 확인한다.
        - 방향키를 이용해 이동할 수 있으며, 특정 내용을 찾고 싶은 경우 명령환경에서 `/내용`를 사용한다.
        - n키를 이용해 찾는 내용의 다음내용으로 이동 가능, shift+n을 통해 이전 검색 내용으로 이동 가능
        - q를 사용해 나올 수 있다.
    - man과 help의 차이 : man은 전용페이지로 이동해 상세한 메뉴얼을 보이며, help는 간략하다.
    - ex) `mkdir --help`
        - `Usage: mkdir [OPTION]... DIRECTORY...` : 사용법을 의미하며, option을 줄 수 있고 그 뒤에 DIRECTORY를 지정하는 것.
        - OPTION은 바로 아래의 arguments들을 지정가능
            - 해당 예로 -p를 OPTION으로 주면, 필요시 부모 디렉토리를 생성한다.
            - `mkdir -p dir1/dir2/dir3/dir4` : 부모디렉토리로 계속 생성
            - OPTION은 -p처럼 축약형 혹은 --parents와 같이 full로 지정가능
- 필요한 명령어를 검색하여 찾기
    - google 검색엔진에서 검색한다.
         - ex) create directory in linux와 같이 검색해보면 된다.
    - <a href="https://maker.pro/linux/tutorial/basic-linux-commands-for-beginners">참조</a>
- sudo
    - sudo : super user do, 즉 super user가 하는 일이라는 것.
    - unix 계열의 운영체제는 다중 사용자 시스템이라는 특징을 가진다. 하나의 운영체제를 여럿이 사용해서 공동체가 형성된다.
    - 그래서, 파일의 권한을 지정하는 것이 중요하다.(permission)
    - 근데, 항상 슈퍼유저로써 권한을 가진 상태에서 명령을 실행하다 보면 매우 위험한 상황이 일어날 수 있다. 그래서 평시에는 일반유저로, 필요시에 sudo를 사용해 권한을 얻는것이다.
    - `apt-get install git` : 이를 실행해보면 permission이 denied된다. root유저가 아니기 때문
    - 이 때, `sudo apt-get install git`으로 하면 가능하다.
### 2. editor
- 파일 편집(nano editor)
    - `nano`를 입력하면 editor를 열 수 있다.
    - editor아래 쪽에는 ^G, ^O와 같이 있는데 ^는 ctrl을 의미한다.
    - 따라서, ctrl + O는 WriteOut이므로 누르면 fileName을 지정하라고 하는데 hello.html로 입력하고 enter를 누르면 `Wrote n lines`라고 나온다.
    - 그것은, 저장되었다는 것을 의미한다. ctrl+X를 누르고 나가서 ls로 확인가능
    - 다시 해당 파일을 수정하고 싶다면 `nano hello.html`로 하면 된다.
    - ctrl + k로 잘라내고 ctrl + u로 붙여넣을 수 있다.(capslock이 반드시 꺼져 있어야 한다. 켜있으면 shift도 눌러야함)
    - ctrl+shift(안눌러도 되는 경우도 있는 듯)+6으로 markset을 사용가능. markset을 이용해 block을 지정할 수 있고 그를 통해 특정 문구를 잘라내고 붙여넣을 수 있다.
    - ctrl+w로 검색할 수 있다.(c9환경에서는 ctrl+alt+shift를 누르고 명령을 수행하라.)
- vi editor
### 3. package manager
- package란 프로그램, app과 같은 것을 의미한다. package를 이용하여 컴퓨터의 다양한 처리를 한다.
- package manager는 app store와 같이 package를 다운로드받거나 관리할 수 있는 것이다.
- apt(패키지 매니저)
    - sudo apt-get update : apt라는 manager를 이용하여 다운받을 수 있는 목록을 최신상태로 update한다.
    - sudo apt-cache search name : name에 해당하는 다운로더블한 패키지를 확인 가능
        - top : window에 있는 작업관리자와 같은 것이다. 이를 좀 더 graphical하게 볼 수 있도록 htop설치
    - sudo apt-get : 설명서 나옴
    - sudo apt-get install htop : htop설치가능
    - sudo apt-get upgrade : 모든 package를 다 upgrade(특정 패키지만 업그레이드 하고 싶은 경우 이름을 주면 된다.)
    - sudo apt-get remove name : 특정 package 삭제
    - sudo apt-get dist-upgrade : 의존성 검사 후 업그레이드
    - sudo apt-get --reinstall install <package name> : 패키지 재설치
    - sudo apt-get --purge remove <package name> : 설정파일까지 모두 지움
    - sudo apt-get source <package name> : 패키지 소스코드 다운로드
    - sudo apt-get build-dep <package name> : 소스코드를 의존성 있게 빌드
    - sudo apt-cache show <package name> : 패키지 정보 보기
### 4. File download
- wget url : url을 통해서 파일을 다운로드받을 수 있다.
    - -O를 통해서 직접 이름을 지정할 수 있다.
    - wget --help를 이용해 manual을 확인하자
- git을 이용한 github url의 source를 받기
    - git clone url을 이용해 다운로드 받을 수 있다.
### 5. GUI vs CLI
- CLI를 사용하는 이유
    - GUI는 사용하기 편리하지만 computer의 resource를 매우 많이 잡아먹는다.
    - GUI는 순차적으로 진행되는 일을 자동화하기 어렵다.
- 순차적 실행?
    - mkdir why; cd why : why디렉토리를 만들고 거기로 이동한다.
    - 따라서, 이 명령어를 통해 거둘 수 있는 효과는 앞으로 필요한 process를 자동적으로 수행하고 최종 결과를 사용자에게 가져다준다는 것
    - 만약 매우 복잡하고 시간이 오래 걸릴 수 있는 명령어가 있는 경우 순차적으로 실행후 결과만 볼 수 있다.
- pipeline
    - 하나의 명령(프로그램, 프로세스)의 출력을 다른 명령(프로그램, 프로세스)의 입력으로 준다.
    - 예를 들어, grep을 이용해 특정 정보를 가진 행만을 화면에 보여주고 싶은 경우
    - `ls --help | grep sort` : ls의 manual 결과를 가지고 해당 내용에서 sort라는 정보를 가진 행만 출력해준다.
### 6. IO Redirection