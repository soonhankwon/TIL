# TIL (Today I Learned) https://soonhankwon.github.io/
<details>
<summary>221024 About Json with MultipartFile</summary>
<div markdown="1">
<hr/>

**Mention** : Winter is coming🥶 아침에 춥....춥다! 시간날 때, 깃블로그로 전환해야겠다💡

**Acheivement & Problem** : 어제 구현했던 AWS S3를 이용한 이미지 업로드기능을 실제 프로젝트에 적용 & 구현해보았다.

어제는 MultipartFile만 Body에 받아서  Post API를 구현했는데, 프로젝트에서는 JSON 타입의 데이터도 받아서 

Post API를 구현해야했다. 게시글의 제목, 내용, 유저네임은 JSON MediaType, 이미지파일은 MULTIPART MediaType 이런 구조이다.

에러의 원인은 빨리 파악한 거 같은데, 적용중 Configure Bean? 적어놓진 않았는데 이러한 에러가 발생🤯

기존 자바 클래스파일을 지우고 다시 쓰고 하는 과정중에 not founded 에러로 발생한 문제인듯 싶다. 

Gradle에 들어가서 Clean -> Build를 해주면 깔끔하게 청소된다. 어째저째 해결하고 두 가지 타입의 데이터를 받아서

기능을 구현하고 Postman 테스트 & AWS S3 Bucket에 저장되는 것 까지 확인완료🔥

클라이언트에서 서버까지 데이터의 흐름 & HTTP 에 대해서 정확히 알아둬야 오늘과 같은 에러의 근본 원인을 빠르게

해결할 수 있을 것이다🛠
<hr/>

오늘 구현했던, API에서 Json과 MultipartFile을 한번에 전달 받는 방법이다. 

일반적으로 API에서 클라이언트에게 값을 전달받기 위해서 @RequestBody로 데이터를 전달받도록 구현한다.

하지만, Multipartfile은 미디어타입이 달라 @RequestBody로 데이터를 전달 받을 수가 없다.

**@RequestPart**를 사용하면 Json & MultipartFile 미디어 타입(파일)을 둘 다 받을 수 있다.

이때 API에서 **consume**할 **MediaType**을 아래의 코드와 같이 지정해줘야 한다. 만약 적절한 MediaType를 지정하지

않을 경우 415 Unsupported MediaType ERROR와 인사하게 된다🤯

```java
@PostMapping(value = "/api/article", consumes = {MediaType.APPLICATION_JSON_VALUE, MediaType.MULTIPART_FORM_DATA_VALUE})
    public ResponseEntity<?> createArticle(@RequestPart ArticleRequestDto requestDto, @RequestPart MultipartFile multipartFile) throws IOException {
        return ResponseEntity.ok(articleService.createArticle(requestDto, multipartFile));
    } 
```

</div>
</details>

<details>
<summary>221022 About Multipart</summary>
<div markdown="1">
<hr/>

**Mention** : 어제 처음으로 프론트엔드 팀원 분들과 조촐한 협업을 시작(MINI PROJECT)🤝

AM6:30 어김없는 댕댕이 순규의 모닝콜🗣로 인해 강제기상해서 코딩을 했지만, 토요일이라 낮잠도 자면서 여유를 부린 하루였다. 
  
**Acheivement & Problem** : AMAZON S3를 이용해서 클라우드에 이미지를 업로드하는 기능을 구현했다. 

이게 쉬워보였는데, 아마존 특유의 콘솔의 복잡함과 SDK 버전을 맞추고, AccessKey, SecretKey, Bucket, Region을 맞추는 과정 중

발생하는 세팅하는 과정에서의 에러가 펑펑 터져주었다. 이것저것 수정하며, 해결해서 포스트맨으로 버킷에 사진 업로드 테스트 완료.

어떤 기능을 구현할 때, 프로젝트를 새로 하나 만들어서 작은 단위로 구현을 한 다음 원래 프로젝트에 적용해주는 방법도 좋을것같다는 생각이 들었다.

이에 대한 장점은 화면에 다른 쓰잘데 없는 클래스들이 안보여서 직관적으로 로직을 만들기 편하다! 머리가 보다 잘돌아간다(**본인기준**)
<hr/>

**Multipart란?**

웹 클라이언트가 요청을 보낼 때, HTTP 프로토콜의 **바디** 부분에 **데이터를 여러 부분**으로 나워서 보내는 것

웹 클라이언트가 서버에게 파일을 업로드 할 때, http프로토콜의 바디 부분에 파일 정보를 담아서 전송을 하는데, 파일을 한번에 여러개 전송을 하면 Body 부분에 파일이 여러개의 부분으로 연결되어 전송되는 것이 Multipart data라고 한다.
	
왜 멀티라는 단어를 굳이 쓸까라는 생각이 의문이 들었는데 하나 이상의 데이터 세트가 단일 본문에 결합되있으며
	
여러유형의 데이터(바이너리, 텍스트)가 포함되어 멀티파트 사용이라고 한다. 
	
As the official specification says, "one or more different sets of data are combined in a single body". So when photos and music are handled as multipart messages as mentioned in the question, probably there is some plain text metadata associated as well, thus making the request containing different types of data (binary, text), which implies the usage of multipart.

Usage : 보통 파일을 전송할 때 사용

**MultipartFile 이란?**

사용자가 업로드한 File을 핸들러에서 손쉽게 다룰 수 있게 도와주는 매개변수 중 하나
MultipartFile 인터페이스는 스프링에서 업로드 한 파일을 표현할 떄 사용되는 **인터페이스**

MultipartFile 인터페이스를 이용해 업로드한 파일의 이름, 실제 데이터, 파일 크기등을 구할 수 있다. 

**Method**

```java
String getName() //파라미터의 이름을 구함
String getOriginalFilename() //업로드한 파일의 이름을 구함
String isEmpty() // 업로드한 파일이 존재하지 않는 경우 true 리턴
long getSize() //업로드한 파일 크기를 구함
byte[] getBytes() throws IOException //업로드한 파일 데이터를 구함
InputStream getInputStream() throws IOException 
//업로드한 파일 데이터를 읽어오는 InputStream을 구함
//InputStream의 사용이 끝나면 알맞게 종료해주어야 한다.
void transfer To(File dest) throws IOException 
// 업로드한 파일 데이터를 지정한 파일에 저장

```

📄 Reference

https://antstudy.tistory.com/308
	
https://stackoverflow.com/questions/16958448/what-is-http-multipart-request

</div>
</details>
<details>

<summary>221020 Soul-searching</summary>
<div markdown="1">
<hr/>	
항해 99 부트캠프를 수강한지 벌써 한달이 된 이 시점, 산책같지 않은 산책을 하는 도중 생각나는 것이 있어서 써보려고 한다.
	
나는 청담대교 건너에 있는 대학의 경제학과를 졸업한 무늬만 경제학도이다. 경제학과에서 뭘 배웠느냐 하면❓...

지금 생각나는 건 "공짜 점심은 없다" 라는 기회비용에 관한 것인데, 이는 나라는 사람의 사고 방식을 나도 모르게 지배하고 있는 부분인것 같다.
	
그건 그렇고, 대학교를 다닐 때 내가 빠져있던건 다름 아닌 스노우보드이다. 정말 스노우보드에 미친듯이 빠져있었는데, 
	
겨울에는 11월 부터 3월까지 스키장에 시즌방을 잡아놓고 스노우보드만 주구장창 미친듯이 탔었었다. 친구들이 겨울에는 항상 사라진다고 할 정도로. 평생 보드타고 싶어서 스노우보드 의류 브랜드도 런칭했었었다.🥶
	
대략 20살때부터 33살까지 이러한 패턴으로 탔는데, 하루에 10시간을 넘게 타도 정말 재미있었다.
	
왜 갑자기 뜬금없이 스노우보드타던 생각이 났냐하면, 지금 배우는 프로그래밍과도 과정적으로 비슷한 맥락이 있기 때문이다.

사실, 어느 전공자 분의 벨로그에서 요즘 열풍인 코딩학원에 대한 뼈 때리는 게시글을 봤는데 공감되는 부분이 꽤나 있다.

https://velog.io/@mowinckel/%EC%BD%94%EB%94%A9-%ED%95%99%EC%9B%90-%EA%B4%91%EA%B3%A0%EC%99%80-%EB%B9%84%EC%A0%84%EA%B3%B5-%EA%B0%9C%EB%B0%9C%EC%9E%90	

어떤 분야든 대부분 마찬가지지만, 스노우보드 나 스케이트보드🛹 도 기초적인 부분이 약하면 실력이 늘지 않는다. 

최근 몇년은 스케이트보드에 미쳐있었어서 스케이트보드에 비유하면 쫌 괜찮을 것 같다.

스케이트 보드에서 알리가 되지않는데, 트레플립부터 돌리는 상황? 이런 것이 위의 글에서 나타는는 요즘 코딩학원의 현실인듯 싶다.
	
하지만, 여기서 흥미를 느껴야 하는 점이 중요하다고 생각하는데, 입문자들은 이러한 멋있는 것에 대한 상상이 나중에 정말로
	
트레플립을 스타일있게 구사할 수 있는 원동력이 된다고 생각한다. 흥미 자체가 없는 지루한 과정을 하게된다면, 원동력도 사라진다. 

때문에, 처음에 멋도 모르고 예쁜 데크를 사고, 유명 스케이트 비디오를 보면서 기술을 따라하고 그러면서 자기 것이 되는것이다.
	
무엇을 하나 미친듯이 파서 거의 끝을 본 사람의 경험으로써 프로그래밍(코딩)도 이와 마찬가지인 것 같다.
	
학원의 수강 코스를 따라가면서 정말 많은 지식을 주입받는데, 사실 수박 겉핣기라고 생각한다. 스케이트보드로 따지면 **포져**
	
**BUT** 프로그래밍을 처음 접하는 나라는 사람이 무엇을 설계하고 만들수있고, 
	
내가 원하는 분야의 회사에서 서비스를 만들어 공헌하고 싶어진 목표 및 이 분야에 대한 흥미유발을 제대로 했다는 점에 대해서는 RESPECT 하는 부분이다. 
	
조급해지는 나 자신을 보면서, 스노우보드나 스케이트보드를 처음 타던 그 때가 생각났다. 프로그래밍에 관한 여러 유튜브 나 글들을 보고있는 나자신을 보며 
	
스노우보드나 스케이트보드 영상을 보며 열광하고 연구하던 내가 생각난다. 본다고 다 이해되고 바로 할 수 있었던가? 
	
절대 조급해하지 말고 하나를 알아도 제대로 알고 로직적으로 생각하는게 중요하다. 이렇게 써도 정말 어려운 부분이다. 
	
사실 스케이트보드도 제대로 된 알리를 하기 전까지 고난의 행진이다. 
	
그냥 알리스러운 점프를 하는 것은 하루만해도 할 수 있다. 하지만, 제대로 간지나는 자기 몸같은 알리를 하기위해선 신경써야할 기초, 
	
디테일이 너무 많다.(스케이트 보드만큼 발 감각의 사소한 차이에 따라서 결과가 달라지는 것도 없는 것 같다.)
	
그래서 개인적으론 샤빗도 해보고 팝샤빗도해보고 그러면서 돌파했고, 첫 알리를 했을 때 성취감은 경험해본 사람만 안다.

주저리 주저리 두서도 없는 자기성찰이다. 하지만 기초가 탄탄하고 재미까지 느끼는 사람이 항상 미친듯이 실력이 폭발해서 
	
별로 노력하지 않고 짬으로만 타고있던 보더들을 금방 따라오더라...🔥 **화이팅**
	
그리고, ANOTHER CLASS의 사람들을 보면서 자기 비하를 하지말자 그들은 프로선수라고 생각하면된다, 그들이 하고 있는 기술 
	
흉내내는 정도만해도 성공한거다. 롤모델이라고 생각하고 따라가면 비슷하게는 간다, 비교는 하지 말자! 출발점이 너무나 다르다(FACT!)
	
</div>
</details>

<details>	
<summary>221019 About @RequiredArgsConstructor Annotation</summary>
<div markdown="1">
<hr/>

**Acheivement** : SPRING 심화과정 팀 프로젝트END👏

숙련과정 프로젝트를 다시 한번 복기하는 중이다. 그리고, 백준 기초 알고리즘 문제 7문제 COMPLETED. 시간이 되면 매일 꾸준히 GOGO
  
**Problem** : 현재 단순히 강의를 듣고 따라서 프로그래밍을 하는 부분이 많다(흐름이나 왜 이렇게 쓰는지는 최대한 이해하고 하지만).  

**Feedback** : **내가 만들고 싶은 것이 무엇인지?** 생각하여 내가 만들고 싶은 것을 구현해야겠다. 생각한 아이디어를 구현하고, 배운것을 응용하는 과정에서 부족한 부분을 배워서 발전하는 과정을 가져야겠다🔥
<hr/>

생성자 주입의 단점은 생성자를 만들기 번거롭다는 것이다. 하지만 이를 보완하기 위해 롬복(lombok)을 사용하여 

간단한 방법으로 생성자 주입 방식의 코딩을 할 수 있다. **초기화 되지 않은 final 필드**나, **@NotNull이 붙은 필드**의 생성자를 자동 생성해주는 
롬복 어노테이션이다. DI 편의성을 위해서 사용되곤 한다. 

어떠한 빈(Bean)이 생성자가 오직 하나만 있고, 생성자의 파라미터 타입이 빈으로 등록 가능한 존재라면 이 빈은 @Autowired 어노테이션 없이도 의존성 주입이 가능하다. 

```
@Service
@RequiredArgsConstructor
public class RequiredArgsConstructorDIServiceExample {
	private final First Repository firstRepositorty;
	private final Second Repository secondRepositorty;
	private final Third Repository thirdRepositorty;
}
----> //컴파일 시 아래와 같이 생성됨
@Service
public class RequiredArgsConstructorDIServiceExample {
  @ConstructorProperties({"firstRepository", "secondRepository", "thirdRepository"})
  public RequiredArgsConstructorDIServiceExample(FirstRepository firstRepository, SecondRepository secondRepository, ThirdRepository thirdRepository) {
    this.firstRepository = firstRepository;
    this.secondRepository = secondRepository;
    this.thirdRepository = thirdRepository;
  }
}
```

</div>
</details>
<details>
<summary>221018 About ORM Relationship Mapping Basic</summary>
<div markdown="1">
<hr/>

**Acheivement** : PRING 팀 프로젝트ING🤝 거의 대부분의 기능 구현 완료!

GIT **Merge**과정에서 **Conflict** 해결을 해보았다. 백준 아이디 생성 및 기초 알고리즘 문제 10문제 COMPLETED.
  
**Problem** : Service Business Logic을 짜는데 아직 미숙한 점이 많다. 심화과정들어와서 JPA 영속성 및 데이터베이스, HTTP 등

공부가 꽤나 필요한 이론들을 한꺼번에 많이 접하게되어 두뇌가 어지럽다🤯
    
**Feedback** : 같은 조 팀원분에게 그림으로 로직을 먼저 짜보라는 조언을 받았다. 실제로 많은 도움이 됨👍🏽

**Many to One, One to Many** 에 대한 정확한 이해 필요! -> 엔티티 매핑 관련

하루에 하나정도의 주제로 정확히 숙지해주는 것이 중요하다 생각하고 꼭 실행하자🔥
<hr/>

| 관계 | 코드선언 | Entity | Example | 
| --- | --- | --- |--- |
| 일대다 | @OneToMany | Order(1) : Food(N) | 배달 주문 1개에 음식 여러개 선택 가능
| 다대일 | @ManyToOne | Owner(N) : Restaurant(1) | 음식점 주인 여러명이 하나의 음식점을 소유 가능
| 일대일 | @OneToOne | Order(1) : Coupon(1) | 배달 주문 1개 주문 시, 쿠폰 1개만 할인 적용 가능
| 다대다 | @ManyToMany | User(N) : Restaurant(N) | 고객은 음식점 여러개 찜 가능, 음식점은 고객 여러명에게 찜 가능

<hr/>
  방향 관계를 매핑할 때 둘 중 어떤 것을 사용해야 할지는 <u>반대편 관계</u>에 달려있다. 

반대편이 일대다 관계면 다대일을 사용하고, 반대편이 일대일 관계면 일대일을 사용하면 된다.

다대다 관계는 **지양**하고 다대다 관계에 **연결(조인) Entity**를 생성하여 일대다, 다대일의 명확한 관계를 쓰는것을 **지향**하는 것이 좋다.

WHY❓ : 관계형 데이터베이스는 정규화된 테이블 2개로 다대다 관계를 표현할 수 없기 때문이다. 따라서 연결 테이블을 추가해서 일대다, 다대일 관계로 풀어내야 한다. 
</div>
</details>

