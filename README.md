**top: 리눅스에서 현재 실행 중인 프로세스를 실시간으로 모니터링하는 유용한 도구이다. 이 명령어를 사용하면 CPU 사용률, 메모리 사용률, 실행 시간 등의 정보를 확인할 수 있다.**

top 명령어를 친 결과이다.
![스크린샷 2024-06-02 024619](https://github.com/kangs00/kangs00/assets/171443557/bccbb633-24c8-4d22-bef7-488a33123123)
|명령어|내용|
|--|--|
|PID|프로세스 Id|
|USER|사용자 이름|
|PR|우선순위|
|NI|우선순위 값|
|%CPU|CPU 사용률|
|%MEN|메모리 사용률(RES)|
|TIME+|실행 시간|
|COMMAND|명령어 이름|

top 명령어는 top -c로 프로세스의 전체 경로를 표시할 수 있다.

**ps: 리눅스에서 현재 실행 중인 프로세스의 상태를 나타내는 유용한 도구이다. 이 명령어를 사용하면 다양한 정보를 확인할 수 있다**
- -A: 모든 프로세스 출력
- -a: 세션 리더와 터미널과 연관된 프로세스를 제외한 모든 프로세스를 출력
- -e: 커널 프로세스를 제외한 모든 프로세스를 출력
- -f: 상세 정보를 포함하여 출력을 풀 포맷으로 표기
- -ps -ef: 모든 프로세스의 상세 정보를 확인
- ps -aux: 다양한 정보를 포함하여 모든 프로세스를 출력
- ps -t: 특정 TTY에서 실행되는 프로세스를 출력

다음은 ps -aux를 실행한 결과이다.
![스크린샷 2024-06-02 034326](https://github.com/kangs00/kangs00/assets/171443557/e21d52c5-c115-44f2-8fbf-dcb8273e240d)

|명령어|내용|
|--|--|
|PID|프로세스 고유 식별 번호|
|VSZ|가상 메모리 사용량|
|RSS|실제 메모리 사용량|
|TTY|프로세스와 연결된 터미널|
|STAT(BSD)|현재 프로세스의 상태 코드|
|TIME|총 CPU 사용 시간|

**jobs: 리눅스에서 셸 세션 내에서 실행 중인 백그라운드 작업의 상태를 표시하는 유용한 도구이다. 이 명령어를 사용하면 현재 쉘 프로세스의 자식 백그라운드 프로세스 목록을 확인할 수 있다.**


다음은 jobs를 실행한 결과이다.
![스크린샷 2024-06-02 040507](https://github.com/kangs00/kangs00/assets/171443557/634aa021-b55f-4900-9da5-b79ce912b9b3)

여기서 [1]+는 잡ID를 나타내며, Running은 해당 프로세스가 실행 중인 상태를 의미한다.

- -l: 프로세스 ID와 함께 잡 목록을 출력
- -n: 마지막 알림 이후 변경된 잡만 출력
- -p: 잡의 프로세스 ID만 출력
- -r: 실행 중인 잡만 출력
- -s: 중지된 잡만 출력

**kill: 리눅스에서 프로세스를 종료하는 데 사용되는 유용한 도구이다. 프로세스가 비정상적으로 작동하거나 많은 시스템 리소스를 소모할 때 종료해야 할 때 유용하다.**

kill 명령어는 kill [OPTIONS] [PID]... 과 같은 형식을 가진다.
[PID: 고유 식별 번호)

*주요 신호: 
- -1(HUP): 프로세스를 다시 로드함
- -9(KILL): 프로세스를 강제로 종료함
- -15(TERM): 프로세스를 정상적으로 중지함
- 모든 사용 가능한 신호 목록은 kill -ㅣ 명령으로 확인할 수 있다.

기본적으로 -15 (또는 -TERM) 신호를 보내며, 이는 프로세스를 정상적으로 중지시킨다.

*PID 지정 방법
PID>0: 해당 ID와 동일한 프로세스로 신호를 전송한다.
PID=0: 현재 프로세스 그룹의 모든 프로세스로 신호를 전송한다.
PID=-1: 사용자와 동일한 UID를 가진 모든 프로세스로 신호를 전송한다.
PID<-1: 절대값이 해당 PID와 동일한 프로세스 그룹의 모든 프로세스로 신호를 전송한다.
