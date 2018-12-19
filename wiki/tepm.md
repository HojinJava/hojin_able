## mysqldump

1. 환경변수에 mysql.exe 등록 혹은 해당 파일이 있는 위치에서 실행
   * 번거로울 시 mysql.exe 폴더 위치에서 작업 해도 가능
   * 기본 경로 :C:\Program Files (x86)\MySQL\MySQL Server 5.7\bin  ( x86아니면 그냥 Program Files에 있을 확률이 높습니다.)
2. 명령어 실행(dump 받기) (관리자 권한을 받은 cmd에서 가능 합니다.)
   * mysqldump -u[userId] -p[생략] databaseName > outputFileName
     * 예 : mysqldump -uroot -p ideaconcert > out.sql
   * 위 명령어 실행 시 비밀번호 입력하는 명령어가 뜹니다. 그 이후 입력 하시면 됩니다.
     * 위 상황이 번거로우면 -p password('실제 비밀번호') 쳐도 될거 같긴 합니다. (한번도 안해봤습니다 ㅎㅎ)
3. sql 파일로 백업 받기
   * mysql -u[userId] -p[생략] databaseName < inputFileName 
     * 예) mysql -uroot -p ideaconcert < inputFileName