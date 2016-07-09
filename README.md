#JAVASCRIPT Study 복습

nugurejeil.github.io/study/study_day8/index.html

- 자바스크립트 정식 명칭 ECMAScript
- 자바스크립트 기본 문법
	+ 대소문자를 구분(대문자a와 소문자 A는 다릅니다!)
	+ 유니코드를 기반, 영어 아닌 다름 언어도 코드 안에서 사용 가능
	+ 명령어는 문장(statement)을 구성함 typeof등 
	+ 한 문장은 세미콜론으로 끝맺는다.
	+ 스페이스, 탭, 줄바꿈 문자는 공백(white-space)라 부름
	
> 유니코드 - 유사이래 모든!!(고대한글도) 문자를 표현하는게 목표 

- `<script type="text/javascript">마임타입!</script>`

	+ 스크립트 코드 위치에 따라 눈에 보이는 페이지 로딩 속도가 달라보임!
	+ 스크립트가 위쪽에 있으면 아래 html문서가 랜더링되지 않아서 늦게 뜨는 것처럼 보인다. 
	+ 하지만 자바스크립트가 <head>부분에 있든 <body>안에 있든 로딩 속도는 별차이 없다.

##변수(Variables): 데이터를 담는 빈 공간(메모리 안에 들어있는 방)
- var(소문자만 사용, 대소문자 구별하므로) + 공백 + 변수이름 형태로 선언한다.
- 쉼표로 구분해서 한번에 선언 가능
	+ var num=1, num=2;
- 변수의 값은 메모리 cpu에 저장된다.
- 변수 이름 규칙 
	+ $, _ 제외 특수문자 공백 구두점(.,!?)쓸 수 없음
	+ 숫자로 시작하면 안됨
	+ 유니코드 문자도 사용(한국어도 가능, 크롬말고 다른 브라우저는 인식 못할 수도 있음)
	+ 예약어 사용 안됨.

> 레거시(유산) 브라우저: 과거에 쓰이던 브라우저 IE 6~10

##컴퓨터 구조
- cpu는 계산.처리담당(cashe는 cpu를 위한 저장공간). 직렬방식(순차적 처리방식:코드를 한개씩 처리, 연산)
- ram은 기억담당(비싼 호텔! 저장하는 주소, 방 많이 가지고 있음)-계산할 값을 저장하고 있음.
휘발성.(메모리). 용량이 많을 수록 편하게 작업할 수 있다.
- hdd/sdd는 영구적으로 데이터 저장
- casche: cpu를 위한 저장공간. 휘발성
- cpu--cache--ram--hdd 순으로 데이터가 이동함
- cpu i-5, i-7(쿼드코어: cup가 4개들어가 있음.)같은거, 노트북과 데스크탑 cpu는 좀 다름..노트북 코어가 2개, 데스트탑 코어가 4개
- Gpu: 병렬방식, 동시에 여러가지 코드를 처리함. cpu보다 속도가 빠름. 화면에 뿌려지는 그랙픽 방식, 모니터에서 랜더링되는 화면을 연산
- gpu 는 동시에 여러 코드를 처리 가능.-테슬러 자동차 처럼 여러 센서가 대규모 데이터 주는거 처리할 때 사용하기도 함
- cpu-직렬처리/ gpu-병렬처리 로 작동방식, 목적이 다름
	자바스크립트: 직렬방식
- 32bit os는 ram을 4기가 이상 쓸 수 없다.인식 못함.

##자료형(Date types)
###원시자료형 : 숫자, 문자열, Boolean, null, undefined
- 리터럴 표현
	+ 문자형의 리터럴 표현: "안녕하세요"
	+ 숫자형의 리터럴 표현: 1, 2, 3
	+ Bloon의 리터럴 표현: true, false
	+ null의 리터럴 표현: null
	+ undefind의 리터럴 표현: undefind
	+ 객체의 리터럴 표현방식: {}
	+ 배열의 리터럴 표현방식 : [] 

- 객체 : 자바스크립트는 객체지향적인 언어. 모든 것을, 객체는 propoty의 집합
	+ 자바스크립트는 모든 값을 객체처럼 다룸. 원시자료형에도 프로퍼티와 메소드가 존재하는 것처럼 보임
	+ 코드상에서 객체는 프로퍼티와 메소드의 집합. 
	+ 프로퍼티는 객체 안에 들어있는 { 이름: 값 } 이름과 값의 쌍 묶음. 
	+ 메소드는 프로퍼티의 그 값이 함수형태일 때.
	+ {이름:값}, 근데 그 값이 함수일때 메소드라 부른다.
		* var 라면={ 스프 : 넣어라;} 넣어라() 라는 함수
        			----------
					propoty -> 값이 함수면 메소드.
		* 라면.스프
        	* var 이지연 { 나이: 27; } -> 이건 프로퍼티
        	* var 영화{ 나이 : age; }  function age(){var a= Date.getYear(); var myAge= a-1990; return myAge;} -> 이건 메소드
        	* 문자열{indexOf:[];}
		문잘열{indexOf:함수}
		안녕하세요{indexOf:값(함수)}
- 원시자료형(숫자,문자열, 불리언, 널, 언디파인드)은 값 자체가 복사됨. 복사된 변수를 변경해도 원래 변수는 변하지 않음
    + var a=1; var b=a; var b=2; 하면 a=1, a=2 // 변수 a와 b는 아예 다른 방을 쓰므로
    + 배열과 같은 객체자료형은 변수의 공간(방)을 따로 만들어주는 게 아니라, 주소만 알려주는거라서 방을 공유함. 같은 주소 가진 변수의 값을 바꿔주면 다 바뀜.
- typeof이용해서 타입 확인하기 쉬움 : 함수같은거 만들 때 typeof()연산자 이용해서 문자열만 받을거야! 이럴 때 씀.

####숫자
- NaN: typeof 쓰면 number로 뜸, "안녕"*12 하면 NaN 뜸
- isNaN() 이거 숫자가 아니니? :  숫자가 아니야 true/ 숫자야 false로 뜸 :  isNaN("안녕"*12) = true
    + 숫자면 false, 숫자가 아니면(NaN) true
- 단항연산자 +, - 기호 바꾸는 용도
	```
	isNaN("안녕");
	ture
	```

	```
	isNan(123);   123은 숫자가 아닌거니?
	false         아니야 숫자야.
	```

	```
	typeof(NaN);
	"numer"
	```

	> 나머지 연산 : %
	> 단항연산자 : +, - (기호를 바꿀수 있다)

####문자열
- 문자열의 원시타입 "", ''둘 다 쓸 수 있음- ''쓰는 사람은 SHIFT누르기 귀찮아서...
    + ''영어권에서 구어적 표현,""가 좀 더 정의적
    + 자바스크립트의 표준이 "", 이걸 권장함!
    + 영어의 축약 I'm 이런 문장과 같이 쓰기에 작은 따옴표는 불편, 오류 날수도 있음
    + JSON에서도 문자열 다룰 때 큰 따옴표 사용. 자바스크립트 코드 안에 JSON데이터 가져와서 같이 쓰기엔 큰 따옴표가 편리
    + 리터럴 : '코드상'에서 데이터 표현하는 방식
- []연산자로 특정 인덱스의 글자만 가져오기 "hello"[1] =='e'; 자바스크립트는 문자열을 배열로 인식하는듯 하다 ["h","e","l","l","o"]
- "hi" + null(null) =="hinull"
- "hi" + NaN(number) =="hiNaN"
- 문자열 ->정수 parseInt, parseFloat
    + parseInt("30",16) 16진수로
    + parseFloat("30.5") 30.5
- +"30살이야" -> NaN
- +"30" ->30 숫자로 바뀜
- 코드는 줄바꿈 하면 오류남. 한 코드 내에서 줄바꿈하고싶을 때 이스케이프문자 
    + var a="안녕하\n세요";
    + 문자이지만 문자열로 해석하지 않는 이스케이프 문자들. \n:줄바꿈 \t:들여쓰기 \x:16진수로 바꿔줌 \u:유니코드해석
- 백틱backtick 문자 ``로 묶으면 템플릿 문자열이 됨
    + var name="하하" ``안녕하세요`,${name}님` -> 안녕하세요,하하님

####boolean
- true/ false 값 가짐
- ! 이건 반대 의미. true, false에만 쓸 수 있음
- 문자열 중 빈문자열만 boolean값은 false
- 숫자 0, NaN은 false

####undefined, null
- 둘 다 빈 값.
- type만 다름
- undefined는 예약어 아님. 변수이름으로 쓸 수 있지만 값이 실제로 담기지는 않음

	+ 변수마다 각 방을 만든다.
	  a의 값을 B에 할당하고 B의 값을 바꾸면 B의 값은 바뀌지만 a는 원래 값 그대로다.

	+ 객체자료형의 특징(방을 공유한다.)
	  var a=[1,2,3]
	  var b=a;
	  b=[3,2,1]
	  방을 공유하기 때문에 값이 a,b 둘다 바뀐다.	
	
	메소드의 리터럴 표현방식 : 함수가 값에 들어	

####문자열
	0개 이상 연속된 문자집합
	"" 또는 ''이다. 자바스크립트의 표준방식은 ""이다.
	영어권 사람이 말할때 ''(예: I'm)
	오류 예: var a='I'am a boy' --> I까지만 읽어준다.
	자바스크립트 코드안에 JSON을 가져올때 ""를 사용한다.
	개발자가 ''쓰는 이유는 단지 쓰기 편해서. 하지만 ""권장

	```
	"30살야야"
	NaN
	```

	```
	이스케이프 문자
	\t : tab(들여쓰기)
	\u :  유니코드로 해석
	```
	
	``` 
	var a="안녕하\n세요";
	a
	"안녕하
	세요"
	```

	* 자바스크립트 코드는 한줄에 써야한다. 두줄로 하면 에러

	```
	Boolean
	ture, false
	'!'는 '반대'이다. 
	```

	```
	null -> object
	undefined -> undefined
	```
