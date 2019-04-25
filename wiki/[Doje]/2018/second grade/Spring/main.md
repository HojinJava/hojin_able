## NCS기반자격 필수능력단위 (자격종목 SW개발_L3)
* 교과목명 : Spring


* 교과 목표
    1.  요구사항 확인을 통한 상세 분석 결과, 소프트웨어 아키텍처 가이드라인 및 소프트웨어 아키텍처 산출물에 의거하여 이에 따른 애플리케이션 구현을 수행하기 위해 공통모듈 설계, 타 시스템 연동에 대하여 상세 설계할 수 있다.
    2.  관계형 데이터베이스에서 SQL을 사용하여 응용시스템의 요구기능에 적합한 데이터를 정의하고, 조작하며, 제어할 수 있다.


* 교과내용 (소요시간)

    * 애플리케이션 설계(40)

        * 공동 모듈 설계하기
        * 타 시스템 연동설계하기
    * SQL응용(35)

        * 절차형 SQL 작성하기
        * 응용 SQL 작성하기
* 습득지식 (데이터베이스 성능확보)

    * 애플리케이션 설계

        * UML 작성 기술
        * 설계 모델링 기술
        * E-R 모델 작성 기술
        * IDE 및 개발환경 도구 활용
        * 프레임워크 활용
        * 기술영역별 미들웨어/솔루션 활용
    * SQL 응용

        * 그룹 내 순위함수, 행순서 함수, 비율함수, rollup, cube, groupping sets함수 사용 능력
        * 내부조인, 외부조인, 셀프조인을 구분하여 사용하는 능력
        * 뷰 생성과 삭제 명령문 작성과 사용기술
        * 사용자 생성, 역할 생성, grant와 revoke를 사용하는 능력
        * 사용자 정의함수 사용능력
        * 사용자 정의함수 작성 기술
        * 서브쿼리를 사용하는 명령문 작성기술
        * 인덱스 생서오가 삭제 명령문 작성기술
        * 집합연산자 사용 능력
        * 트리거 사용 능력
        * 트리거 작성 기술
        * 프로시저 사용 능력
        * 프로시저 작성 기술

--------

# 수업 : 어플리케이션 설계

### 공통 모듈 설계하기
* 공통모듈 설계 과정(Design Patterns) 이란 ?

    * 모듈이란
        * 프로그램을 구성하는 구성 요소의 일부
        * 하나의 기능이 될수도 있고, 하나의 메소드가 될 수도 있음
        * 크기가 아닌, 기능별로 나누어지는 것을 의미 함
    * 예제 (Ajax소스코드, submit소스코드 보여주기)

    ~~~javascript
    function ajaxSubmit2(action,ajaxType){
    	var formId = $("#formId");
    	formId.attr("method","post");
    	formId.attr("action",action);
    	if($("#ajaxType").attr("id") == undefined || $("#ajaxType").attr("id") == null)		{
    		var idx = $('<input type="hidden" value="'+ajaxType+'" id="ajaxType">');
    		formId.append(idx);
    	}
    	$("#ajaxType").val(ajaxType);

    	var options = {
            success  : success2,  // ajaxSubmit 후처리 함수
    		error : ajaxError
    	};
    	formId.ajaxSubmit(options);
    }
    ~~~

    ~~~java
    public String tempSave(HttpServletRequest request) {
    		DesignApplyVo designApplyVo = 		this.insertOrUpdateDesignApply(request,DesignApplyTypeEnum.TEMP);
    		this.insertAndUpdateTogetehrSave(request, designApplyVo.getPk());
    		return new AjaxResponeData()
    					.setStatus(true)
    					.setAlertFlag(true)
    					.setAlertMsg("임시 저장되었습니다.")
    					.setResponseData(designApplyVo.getPk()+"")
    					.setLocationReloadFlag(true)
    					.parserJsonStr();
    	}
    ~~~

    ~~~javascript
    function ajaxSuccessAlert2(jsonStr){
    	var jsonOb = JSON.parse(jsonStr);

    	var status = jsonOb.status;
    	var alertFlag = jsonOb.alertFlag;
    	var alertMsg = jsonOb.alertMsg;
    	var responseData = jsonOb.responseData;
    	var locationBackFlag = jsonOb.locationBackFlag;
    	var locationReloadFlag = jsonOb.locationReloadFlag;


    	if(status =="false" || status =="false" || status==false){
    		alertMsg = decodeURIComponent(alertMsg).replace(/\+/g, ' ');
    		responseData = decodeURIComponent(responseData).replace(/\+/g, ' ');
    	}

    	if(alertFlag =="TRUE" || alertFlag =="true" || alertFlag==true){
    		alert(alertMsg);
    	}
    	if(locationBackFlag =="TRUE" || locationBackFlag =="true" ||  		             locationBackFlag==true){
    		history.go(-1);
    		return responseData;
    	}
    	if(locationReloadFlag =="TRUE" || locationReloadFlag =="true" || locationReloadFlag==true){
    		location.reload();
    		return responseData;
    	}

    	return responseData;
    }

    function ajaxPostProcessing2(data){
    	var ajaxType = $("#ajaxType").val();
    	if(ajaxType == "STEP1PAYOK"){
    		location.reload();
    	}else if(ajaxType == "insertPatent"){
    		location.reload();
    	}else if(ajaxType=="counselWrite"){
    		history.go(-1);
    	}else if(ajaxType=="tempSaveJoin"){
    		$('.join_sns_modal').modal('show');
    	}else if(ajaxType=="snsCheck"){
    		snsCheckCallBack(data);
    	}else if(ajaxType=="showPatentInfo"){
    		print_patent_info_modal(data);
    	}else if(ajaxType=="applicantInfo"){
    		print_user_info_modal(data);
    	}else if(ajaxType=="selectMyEmail"){
    		printUserEmailForSearch(data);
    	}else if(ajaxType=="pwChange"){
    		pageMove("index");
    	}else if(ajaxType=="snedEmailCode"){
    		joinSendMailOk();
    	}
    }

    ~~~

>>> [좋은 예제 : http://kyejusung.com/2015/09/%EB%94%94%EC%9E%90%EC%9D%B8-%ED%8C%A8%ED%84%B4-1-strategy-pattern/]

### 리팩토링 기법
* 실습
    * 기존에 진행한 프로젝트에서 모듈화 적용할 수 있는 기능 아래와 같이 정리 하기
        1. 메소드 기능 설명 (메소드는 하나의 기능만 해야 함, 두가지 이상 기능을 할 경우 분리 해야 함)
        2. 인풋, 아웃풋, 메소드명 설명
        3.  모듈화 진행 계획 설명
           1. 이 함수의 기능은 무엇 인가?
           2. 인풋, 아웃풋 설명
        4. 코드 리뷰
        5. Git에 push







