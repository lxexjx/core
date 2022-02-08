# springMVC
# 좋은 객체 지향 
  객체들의 모임.협력, 유연,변경 용이,
  유연,변경 용이? 컴포넌트를 쉽고 유연하게 변경-다형성!!
# 다형성
  역할+구현으로 분리 ,역할의 인터페이스를 따라서 구현했기때문에 역할에만 의존해->무한히 확장 가능해
  역할+구현으로 분리했기에 <b>클라이언트</b>에 영향을 주지 않고 새로운 기능 제공
  클라이언트는 인터페이스만 알면됨.역할=인터페이스, 구현=인터페이스를 구현한 클래스
  역할과 구현을 명확히 분리. 설계 역할이 더 중요해!!
  클라이언트 변경 없이 서버의 변경 구현을 유연하게
# spring과 객체지향
  스프링은 다형성을 극대화해서 이용할 수 있도록 도와줘, 
  ioc,di이런거는 다형성을 통해 역할과 구현은 편리하게 다루도록 지원하는 것
  
  # SOLID
  1.단일 책임원칙: 하나의 클래스는 하나의 책임만갖는다.기준은 변경!! 변경시 파급 효과가 적으면 단일책임원칙을 잘 따름.
  2.개방폐쇄 원칙: 확장에는 열려있으나 변경에는 닫혀있어야됨. 코드의 변경없이 기능추가? 다형성에서 역할과 구현을 잘 분리.
    기존코드 변경 없이 인터페이스 의 구현 클래스를 만들뿐 
    but구현 객체를 변경하려면 클라이언트 코드를 변경해야됨->다형성을 못지킴 =>스프링이 객체를 생성하고 관계를 별도 조립.
  3.리스코르 치환 원칙:컴파일에서의 문제가 아닌 인터페이스를 구현시 옳게 구현해야됨
  4.인터페이스 분리 원칙: 맞게 적당한 크기로 인터페이스를 분리해 인터페이스가 변해도 클라이언트에 영향안줌대체가능높아짐
  5.의존 관계 역전 원칙: 추상화에 의존하지 구체화에 의존하면 ㄴㄴ. 클라이언트 코드가 구현클래스말고 인터페이스에 의존해야됨. memberService->memberRepositoryInterface만 바라봐 memorymemberrepo나 jdbc~는 몰라 . 역할에 의존 (추상화에 의존해야지 구체화에 의존하면 안된다.)
  
  =>>역할과 구현을 철저히 분리.인터에 의존해라 구현에 의존하면 변경이 힘들어져
  객체지향의 핵심은 다형성!하지만 다형성만으로 구현 객체 변경시 클라이언트 코드도 변경돼->개방폐쇄와 의존관계역전원칙 못지켜->스프링의 di컨테이너와 di로 클라 코드 변경없이 확장 가능
  di컨테이너: 자바객체를 컨테이너에 넣어놓고 의존관계 연결과 주입해줌
  *역할과 구현을 분리하자. 유연하게 교체 변경가능하게 하는게 다형성과 ocp,di를 지켜야됨.그게 바로 스프링컨테이너다
  인터페이스를 먼저 만들자? 간단한 인터 만들고 진행하고 구현은나중에 갈아껴
   
  
 # 도메인 설계
 도메인 협력관계: 협력자들도 볼수있음, 
 클래스 다이어그램:개발자가 구체화 해서 클래스 다이어그램을 만듦, 실제 서버 실행없이 클래스 분석 
 객체 다이어그램: 서버 실제 떠서 실제로 사용하는 인스턴스끼리의 참조. 실제로 new해서 생성해서 서버 띄워서동적으로 객체   들의 연관관계가 맺어지는 그림
 
 # 흐름 정리
  다형성으로 정률할인 정책으로 추가클래스를 만듦, but 적용시에 클라이언트 코드인 주문서비스도 변경해야됨.
  추상화에만 의존해야 하는데 구체화에도 의존함
  
  # 좋은 객체 지향 설계 5원칙(srp,dip,ocp) 정리
  srp:한 클래스는 한 책임만 가짐. 관심사를 분리해->구현 객체를 생성하고 연결은 appconfig가 담당. 클라는 실행만
  dip:추상화에 의존. 구체화에 의존안함. 객체(추상화에 의존)에 대한 의존관계를 외부에서 app에서 생성해서 넣어줌
    의존관계에 대한 구체적인 클래스 선택은 외부에서 넣어줌. 
  ocp:애플리케이션을 사용과 구성으로 나눔. 변경시에도 클라이언트 코드는 변경안해도 됨, 새롭게 확장해도 변경에는 닫힘.
  
  # ioc 제어의 역전
  프레임워크가 코드를 대신 호출. 제어권이 뒤바뀜. appconfig는 제어 흐름을 가져감.orderserviceImpl은 어떤게 호출될지 모름. 제어권은 appconfig는에게.외부에서 관리
  
  # 프레임워크와 라이브러리
  프레임워크:Junit ,내가 제어권을 가지고 있는게 아닌 필요 부분만
  라이브러리: 작성 코드가 직접 제어 흐름 담당
  # 정적, 동적 의존 관계
  
  # 컨테이너
  의존관계 역전을 일으켜,AppConfig가 의존관계 주입을 대신해줘, DI컨테이너=AppConfig
  
  #  스프링 컨테이너
  @Bean 이라 적인 메서드 모두 호출해서 스프링 컨에이너에 등록
  이전:필요 객체 AppConfig에서 직접 조회->스프링컨테이너에서 필요 스프링객체 찾아(applicationContext.getBean()로 찾아)
  # 스프링 컨테이너 생성
  ApplicationContext applicationContext =new AnnotationConfigApplicationContext(AppConfig.class); 로 객체를 생성
  ApplicationContext: 스프링 컨테이너이자 인터페이스
  1.new AnnotationConfigApplicationContext()로 AppConfig의 정보를 주면 스프링 컨테이너가 만들어짐
    스프링컨테이너는 저장소(빈이름, 빈객체)가 만들어짐(구성정보:AppConfig.class 지정 필요),
  2.컨테이너가 AppConfig.class정보를 보고 저장소에 빈등록해 @Bean~보고 호출해서 빈이름, 빈객체를 등록
  3.스프링 빈 의존관계 설정:객체 생성하고 의존관계를 넣어줌. 생성과 
  
  # 스프링 빈 상속 관계
  빈 부모타입 조회시 자식이 여러개다 자식들 다 죄회됨
  
  # BeanFactory 
  BeanFactory(최상위)를 상속받은 ApplicationContext
  # ApplicationContext
  BeanFactory기능 상속 받아 제공,+부가기능    , ApplicationContext를 구현한 것중에 하나가 AnnotationConfig를 설정정보로 사용하는 ApplicationContext(AppConfig.class사용)
  
  # GenericXml
  xml문서를 설정정보로 사용, 컴파일 없이 빈설정정보를 변경가능
  
  # 빈 설정 메타 정보
  BeanDefinition: 빈 정보 추상화->q빈생성
  스프링컨테이너가 BeanDefinition정보만를 가지고 동작(추상화에만 의존하도록 설계)
  
  
  
  
