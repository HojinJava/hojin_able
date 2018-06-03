## NCS기반자격 필수능력단위 (자격종목 SW개발_L3)
* 교과목명 : DB 최적화


* 교과 목표
    1. 성능 상의 문제점을 분석하고 성능개선 목표를 설정하며 성능개선 수행 방법의 정의, 성능개선 수행, 성능개선 결과를 정량적으로 평가하며, 각 단계별 산출물 및 수행 활동을 규정할 수 있다.
    2. 데이터베이스 설계와 구축 시에 필요한 데이터 정보 요소의 명칭, 정의, 형식, 규칙에 대한 정책을 수립하여 적용할 수 있다.


* 교과내용 (소요시간)
    1. 데이터베이스 성능확보 (40h)
        1. 성능 분석하기
	2. 성능 개선하기
	3. 성능개선결과 평가하기
    2. 데이터 표준화 (20h)
        1. 데이터 표준화 정책수립하기
	2. 데이터 표준 정의하기
	3. 데이터 표준 관리하기


* 습득지식 (데이터베이스 성능확보)
    1. 데이터 모델링 방법
    2. 데이터 표준 관리 방법
    3. 데이터 표준 관리를 수행하기 위한 역할과 담당 업무에 대한 특성
    4. 데이터 표준 프로세스에 대한 지식
    5. 데이터 표준화 방법
    6. 데이터베이스 설계 방법
    7. 목표 시스템의 표준화 정책에 대한 특성
    8. 비즈니스 도메인에 대한 지식
    9. 표준단어에 대한 지식
    10. 표준도메인에 대한 규칙
    11. 표준용어에 대한 지식
    12. 표준코드에 대한 규칙
    13. 표준화 정책 사례에 지식
    14. 표준화 정책 전략
    15. 표준화 지침 전략
--------

# 수업 : Application Refactoring

### 디자인패턴
* 디자인 패턴 (Design Patterns) 이란 ?
    * 객체 지향 프로그래밍 설계를 할 때 자주 발생하는 문제들을 피하기 위해 사용되는 패턴
    * 방식을 통해 소프트웨어 설계에서 얻은 세세한 경험들들을 기록 해 놓은 패턴(어떤 상황의 문제에 대한 해법)
    * 일반적으로 하나의 패턴에는 네가지 요소가 반드시 들어가 있다. [&#128209;](https://wikidocs.net/580)
        1. 패턴이름
        2. 문제 : 언제 패턴을 사용하는가를 서술하며 해결할 문제와 그 배경을 설명한다.
        3. 해법 : 설계를 구성하는 요 소들과 그 요소들 간의 관계 책임 그리고 협력 관계를 서술한다.
        4. 결과 : 디자인 패턴을 적용해서 얻는 결과와 장단점을 서술한다.
    * 생성 패턴 (추상 객체 인스턴스화) [&#128209;](http://seungdols.tistory.com/486)
    * 구조 패턴 (객체 결합) [&#128209;](http://seungdols.tistory.com/487?category=652793)
    * 행위 패턴(객체 간 커뮤케이션) [&#128209;](http://seungdols.tistory.com/490?category=652793)
>>> [좋은 예제 : http://kyejusung.com/](http://kyejusung.com/2015/09/%EB%94%94%EC%9E%90%EC%9D%B8-%ED%8C%A8%ED%84%B4-1-strategy-pattern/)

### 리팩토링 기법
* Code smell or 코드의 구린내 : 소프트웨어는 과학이 아니라 공학이다. 개발자나 기획자의 주관에 따라 쉽게 바뀌기 마련이기 때문에 리팩토링의 시점은 정확하게 정해져있지 않다.
    * Duplicated Code (중복코드)
    * Long Method(장황한 메서드)
    * Large Class (방대한 클래스)
    * Long Parameter List  (과다한 매개변수)
    * Divergent Change (수정의 산발)
    * Shotgun Surgery (기능의 상재) [&#128209;](http://blog.daum.net/bellosogno/10)
    * Feature Envy (잘못된 소속)
    * Feature Envy (데이터 뭉치)
    * Primitive Obsession (강박적 기본 타입 사용) [&#128209;](http://blog.daum.net/bellosogno/13)
    * Switch Statement
    * Parallel Inheritance Hierarchies (평행 상속 계층)
    * Lazy Class(직무유기 클래스)
    * Speculative Generality(막연한 범용 코드) : Collapse Hierarchy + Inline Class
    * 임시 필드
    * Message Chains(메시지 체인) [&#128209;](http://dj6316.torchpad.com/%EB%A6%AC%ED%8C%A9%ED%86%A0%EB%A7%81%28refactoring%29/CH.03+%EC%BD%94%EB%93%9C%EC%9D%98+%EA%B5%AC%EB%A6%B0%EB%82%B4/8.%EB%A9%94%EC%8B%9C%EC%A7%80+%EC%B2%B4%EC%9D%B8+Message+Chains)
    * Middle Man (과잉 중개 메서드) [&#128209;](https://wikidocs.net/593)
    * Inappropriate Intimacy(지나친 관여) [&#128209;](http://dj6316.torchpad.com/%EB%A6%AC%ED%8C%A9%ED%86%A0%EB%A7%81%28refactoring%29/CH.03+%EC%BD%94%EB%93%9C%EC%9D%98+%EA%B5%AC%EB%A6%B0%EB%82%B4/9.%EC%A7%80%EB%82%98%EC%B9%9C+%EA%B4%80%EC%97%AC+Inappropriate+Intimacy)
    * Alternative Class with Different Interfaces(인터페이스가 다른 대용 클래스) [&#128209;](http://dj6316.torchpad.com/%EB%A6%AC%ED%8C%A9%ED%86%A0%EB%A7%81%28refactoring%29/CH.03+%EC%BD%94%EB%93%9C%EC%9D%98+%EA%B5%AC%EB%A6%B0%EB%82%B4/9-1.%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4%EA%B0%80+%EB%8B%A4%EB%A5%B8+%EB%8C%80%EC%9A%A9+%ED%81%B4%EB%9E%98%EC%8A%A4+Alternative+Classes+with+Different+Interfaces)
    * Incomplete Library Class(미흡한 라이브러리 클래스) [&#128209;](http://dj6316.torchpad.com/%EB%A6%AC%ED%8C%A9%ED%86%A0%EB%A7%81%28refactoring%29/CH.03+%EC%BD%94%EB%93%9C%EC%9D%98+%EA%B5%AC%EB%A6%B0%EB%82%B4/10.%EB%AF%B8%ED%9D%A1%ED%95%9C+%EB%9D%BC%EC%9D%B4%EB%B8%8C%EB%9F%AC%EB%A6%AC+%ED%81%B4%EB%9E%98%EC%8A%A4+Incomplete+Library+Class)
    * 데이터 클래스
    * Refuged Bequest(방치된 상속물)
    * 불필요한 주석
>>> [좋은 예제 : https://wikidocs.net/](https://wikidocs.net/593)








