##  Java - OOP
 ### 기본지식

  * 정의 : 프로그래밍 패러다임 중 하나, 컴퓨터 프로그램을 명령어 목록으로 보는 시각에서 객체들의 모임으로 파악하자
  * OOP 설계의 5대 원칙
      * 단일 책임의 원칙( SRP : Single Responsibity Principle): 낮은 결합도와 높은 응집도
      * 의존 관계 역전의 법칙(DIP : Dependency Inversion Principle) : 확장 이슈가 있는 부분은 추상화로
      * 인터페이스 분리의 원칙(ISP : Internet SegreGation Principle) : 하나의 범용 인터페이스보다 여러개의 인터페이스 낫다
      * 리스 코프 대체 원칙(LSP : Liskov Substitution Principle) : 상위 클래스는 파생 클래스로 대체 가능 해야 함
      * 개방 폐쇄 원칙 (Open-Closed Principle) : 확장에는 열려 있어야 하고, 변경에는 닫혀있어야 함, 기존 클래스를 수정하지 않고, 상속 또는 구현으로 확장을 해야 함.
* 출처 : [:bookmark_tabs:](https://m.blog.naver.com/PostView.nhn?blogId=hsyoo1990&logNo=220653778093&proxyReferer=https%3A%2F%2Fwww.google.com%2F)

---







### 용어정리

---

* 응집도 :  하나의 클래스가 하나의 기능을 순도 높게 담당하고 있는 정도
  * 예 : 청소라는 클래스가 존재, 청소기 사용, 빗자루 사용 메소드를 갖고 있다. 이때 걸레질 사용 메소드를 수정하고 싶을 때, 이 메소드가 다른 클래스에 있다면 응집도가 낮다고 볼 수 있다.
* 결합도 :  클래스 간의 서로 다른 책임들이 얽혀 있는 상호 의존도
  * 예 :  A라는 클래스를 상속받았을 경우, A클래스의 수정이 상속받은 모든 클래스에 영향을 끼칠 수 있다.

