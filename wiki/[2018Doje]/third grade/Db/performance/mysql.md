## dNCS기반자격 필수능력단위 (자격종목 SW개발_L3)
* 교과목명 : DB 최적화

--------

# 수업 : Mysql 퍼포먼스 최적화

### Mysql의 특징
* Mysql 구조
  * 서버엔진 : 사용자가 쿼리를 날렸을 때, DB가 SQL을 이해할 수 있도록 쿼리를 재구성하는 '쿼리파싱'과 디스크나 메모리 같은 물리적인 저장장치와 통신하는 스토리지 엔진에 데이터를 요청하는 업무를 담당한다.
  * 스토리엔진 [&#128209;](http://12bme.tistory.com/72) : 서버 엔진이 필요한 데이터를 물리 장치에서 가져오는 역할을 담당.
    * 스토리 엔진의 종류
      * InnoDB [&#128209;](http://www.mysqlkorea.com/gnuboard4/bbs/board.php?bo_table=community_03&wr_id=1702) : 트랜잭션을 지원하며, 일반적인 서비스에 가장 만힝 사용되는 엔진 '다중 버전 동시성 제어 메커니즘'을 제공하고 행 단위 잠금으로 데이터 변경 작업을 수행함 메모리에 인덱스와 데이터가 적재되어있기 때문에 메모리 버퍼 크기가 DB 성능에 큰 영향을 미친다.

* 처리방식 : 기본적인 스토리이 엔진은 단일코어로만 데이터를 처리 한다(병렬 처리를 하지 않는다.) 따라서 CPU코어 개수를 늘리는 Sacle-Out보다는 단위 처리량이 좋은  CPU로 Scale-Up 하는 것이 더욱 효율 적

* BNL(Block Nested Loop) [&#128209;](http://blog.naver.com/PostView.nhn?blogId=parkjy76&logNo=221069454499&categoryNo=14&parentCategoryNo=0&viewDate=&currentPage=1&postListTopCurrentPage=1&from=postView)

* 쿼리 성능 진단

  * 쿼리 실행 계획 [&#128209;](http://multifrontgarden.tistory.com/149)

    ~~~mysql
    EXPLAIN
    SELECT 2*3 FROM DUAL;
    ~~~

* WHERE 조건 이해

  * 묵시적 형변환

    * 정의 : 조건절의 데이터 타입이 다를 때 우선순위가 높은 타입으로 형변환이 내부적으로 되는 것을 말함

    * 예제 : 문자열과 정수값을 비교하면, 우선순위가 낮은 문자열은 자동으로 정수 타입으로 형변환 처리 됨.

      ~~~mysql
      create table test(
      inti int unsigned not null auto_increment,
      intj int unsigned not null,
      str varchar(64) not null,
      d datetime not null,
      primary key(inti)
      );
      
      alter table test add key(intj), add key(str), add key(d);
      
      insert into test(intj, str, d)
      values(
      	crc32(rand()),
          crc32(rand()*12345),
          date_add(now(), interval -crc32(rand())/5 second)
      );
      ~~~



      * 위 코드를 17번 실행하면 약 1만건 row가 insert 됨
      * 위 쿼리문 이해하기
      * 실행 계획에서 intj를 문자열로 검색해보고, 정수형으로 검색 해보기
      * 실행 계획에서 str를 문자열로 검색해보고, 정수형으로 검색 해보기
        * 결과를 리포트랑 이유 리포트를 작성하기

* 용어 찾아보기
  * 클러스터 인덱스(Cluster Index)  [&#128209;](http://mee2ro.tistory.com/2)  : 









