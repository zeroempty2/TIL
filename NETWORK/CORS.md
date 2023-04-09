## CORS(Cross-Origin Resource Sharing)
>CORS는 함축 단어로써 이를 풀면 Cross-Origin Resource Sharing 이라는 단어로 이루어 져 있다. 이 문장을 직역하면 "교차 출처 리소스 공유 정책"이라고 해석할 수 있는데, 여기서 교차 출처라고 하는 것은 (엇갈린) 다른 출처를 의미하는 것으로 보면 된다.


<br>

## ▶️ 동일 출처 정책 SOP(Same-Origin Policy)
CORS를 알아보기전에 먼저 SOP라는 것에 대해 알아야한다.
SOP(Same Origin Policy)는 다른 Origin으로 요청을 보낼 수 없도록 금지하는 브라우저의 기본적인 보안 정책이다. <br>
즉, 동일한 Origin으로만 요청을 보낼 수 있게 하는 것이다. 실제로 아주 옛날에는 이것이 절대적인 규칙이었기 때문에, 다른 Origin으로 요청을 보내는 건 애초에 불가능하였다. 그러나 기술이 발달하면서 서로 다른 Origin끼리 데이터를 주고받아야 하는 일이 많아졌고, 이로 인해 SOP는 별도의 예외 사항을 두게 되었다.<br> 즉, 몇 가지 예외 상황에 대해서는 다른 Origin으로도 요청을 보낼 수 있게 하는 것이다.


<br>

## ▶️ 자유롭게 다른 Origin으로 요청을 보낼 수 있다면?
만약 SOP가 없어서 자유롭게 다른 Origin으로 요청을 보낼 수 있다면 어떻게 될까? 즉, SOP의 필요성에 대한 본질적인 물음이다. 이 물음에 답하기 위해서는, 다음과 같은 상황을 상상해보면 된다.<br>
<br>
악의적인 마음을 품은 해커가 자신의 웹사이트를 구축해놓고, 이 웹사이트를 가리키는 링크를 담은 메일을 사용자에게 보내는 것이다. 그리고 이 사용자는 A라는 웹사이트에 로그인이 되어 있어서 브라우저 단에 인증 정보가 존재한다고 해보자. 만약 그 사용자가 실수로 해당 링크를 클릭하여 해커의 웹사이트에 접속하면, 해커가 심어둔 JavaScript 코드가 실행되어 자기도 모르게 A 웹사이트로 개인 정보를 조회하는 API 요청을 보낼 것이다. 이 사용자의 브라우저 단에는 인증 정보가 존재하기 때문에, 이것이 해당 요청에 함께 실어서 전송되면 서버는 인증된 요청이라 생각하여 개인 정보를 응답해줄 것이다. 그러고 나면 그 개인 정보를 해커가 빼돌릴 수 있게 된다. (이것이 바로 CSRF 공격이다.)<br>
 

그런데 만약 다른 Origin으로의 요청을 막는 정책, 즉 SOP가 존재한다면 이러한 문제를 어느 정도 예방할 수 있다. 해커가 구축한 웹사이트와 A 웹사이트는 당연히 Origin이 다르기 때문에, 해커의 웹사이트에서 A 웹사이트로 API 요청을 보낼 수 없기 때문이다. 따라서 SOP는 브라우저의 아주 기본적인 보안 정책으로서 기능한다.


<br>

## ▶️ 교차 출처 리소스 공유 (Cross-Origin Resource Sharing)를 사용하는 이유
아무리 보안이 중요하지만, 개발을 하다 보면 기능상 어쩔 수 없이 다른 출처 간의 상호작용을 해야 하는 케이스도 있으며, 또한 실무적으로 다른 회사의 서버 API를 이용해야 하는 상황도 존재한다.<br> 따라서 이와 같은 예외 사항을 두기 위해 CORS 정책을 허용하는 리소스에 한해 다른 출처라도 받아들인다는 것이다.<br>
결국 웹개발자를 괴롭히던 시뻘건 에러 메세지는 사실 브라우저의 SOP 정책에 따라 다른 출처의 리소스를 차단하면서 발생된 에러이며, CORS는 다른 출처의 리소스를 얻기위한 해결 방안 이었던 것이다.<br>
요약하자면 SOP 정책을 위반해도 CORS 정책에 따르면 다른 출처의 리소스라도 허용한다는 뜻이다.


<br>

## ▶️ CORS 기본 동작
* 클라이언트에서 HTTP요청의 헤더에 Origin을 담아 전달
    * 클라이언트에서 HTTP요청의 헤더에 Origin을 담아 전달
* 서버는 응답헤더에 Access-Control-Allow-Origin을 담아 클라이언트로 전달한다.
    * 이후 서버가 이 요청에 대한 응답을 할 때 응답 헤더에 Access-Control-Allow-Origin이라는 필드를 추가하고 값으로 '이 리소스를 접근하는 것이 허용된 출처 url'을 내려보낸다.
* 클라이언트에서 Origin과 서버가 보내준 Access-Control-Allow-Origin을 비교한다.
    * 이후 응답을 받은 브라우저는 자신이 보냈던 요청의 Origin과 서버가 보내준 응답의 Access-Control-Allow-Origin을 비교해본 후 차단할지 말지를 결정한다.


<br>

## ▶️ CORS 작동 방식 3가지 시나리오
* 단순 요청 (Simple Request)
    * 단순 요청(Simple Request)은 공식 용어가 아닌, MDN에서 사용한 용어를 가져온 것이다. 그런데 이름이 의미하는 것과 달리, 단순 요청은 흔한 유형의 요청이 아니다. 단순 요청이 되기 위한 조건이 매우 까다롭기 때문이다. 그 조건은 대략 다음과 같다.<br>
        * 요청의 메소드는 GET, HEAD, POST 중 하나여야 한다.<br>
        * Accept, Accept-Language, Content-Language, Content-Type, DPR, Downlink, Save-Data, Viewport-Width, Width 헤더일 경우 에만 적용된다.<br>
        * Content-Type 헤더가 application/x-www-form-urlencoded, multipart/form-data, text/plain중 하나여야한다. 아닐 경우 예비 요청으로 동작된다.<br>
    이처럼 다소 까다로운 조건들이 많기 때문에, 위 조건을 모두 만족되어 단순 요청이 일어나는 상황은 드물다고 보면 된다.<br>
    왜냐하면 대부분 HTTP API 요청은 text/xml 이나 application/json 으로 통신하기 때문에 3번째 Content-Type이 위반되기 때문이다.<br>
    따라서 대부분의 API 요청은 그냥 예비 요청(preflight)으로 이루어진다 라고 이해하면 된다.<br>

    <br>

* 프리플라이트 요청 (Preflight Request)
    * 단순 요청의 조건에 벗어나는(= 안전하지 않은) 요청의 경우, 서버에 실제 요청을 보내기 전에 예비 요청에 해당하는 프리플라이트 요청(Preflight Request)을 먼저 보내서 실제 요청이 전송하기에 안전한지 확인한다. 만약 안전한 요청이라고 확인이 된다면, 그때서야 실제 요청을 서버에게 보낸다. 따라서 총 두 번의 요청을 전송한다.<br>
    프리플라이트 요청의 특징은 다음과 같다.<br>
        * 메소드로 OPTIONS를 사용한다.<br>
        * Origin 헤더에 자신의 Origin을 설정한다.<br>
        * Access-Control-Request-Method 헤더에 실제 요청에 사용할 메소드를 설정한다.<br>
        * Access-Control-Request-Headers 헤더에 실제 요청에 사용할 헤더들을 설정한다.<br>

    * 서버는 이러한 프리플라이트 요청에 대해 다음과 같은 특징을 가진 응답을 제공해야 한다.<br>
        * Access-Control-Allow-Origin 헤더에 허용되는 Origin들의 목록 혹은 와일드카드(*)를 설정한다.<br>
        * Access-Control-Allow-Methods 헤더에 허용되는 메소드들의 목록 혹은 와일드카드(*)를 설정한다.<br>
        * Access-Control-Allow-Headers 헤더에 허용되는 헤더들의 목록 혹은 와일드카드(*)를 설정한다.<br>
        * Access-Control-Max-Age 헤더에 해당 프리플라이트 요청이 브라우저에 캐시 될 수 있는 시간을 초 단위로 설정한다.<br>

    이러한 응답을 받고 나면 브라우저는 이 응답의 정보를 자신이 전송한 요청의 정보와 비교하여 실제 요청의 안전성을 검사한다. 만약 이 안전성 검사에 통과하게 된다면, 그때서야 실제 요청을 서버에게 보낸다. 단, 이때는 Access-Control-Request-XXX 형태의 헤더는 보내지 않는다.<br>


<br>

* 인증 정보를 포함한 요청 (Credentialed Request)
    * 인증 정보(Credential)란 쿠키(Cookie) 혹은 Authorization 헤더에 설정하는 토큰 값 등을 일컫는다. 만약 이러한 인증 정보를 함께 보내야 하는 요청(Credentialed Request)이라면, 별도로 따라줘야 하는 CORS 정책이 존재한다.<br>

    

    * 우선, 쿠키 등의 인증 정보를 보내기 위해서는 클라이언트 단에서 요청 시 별도의 설정이 필요하다. 이는 Ajax 요청을 위해 어떠한 도구를 사용하느냐에 따라 달라진다. 만약 XMLHttpRequest, jQuery의 ajax, 또는 axios를 사용한다면 withCredentials 옵션을 true로 설정해줘야 한다. 반면, fetch API를 사용한다면 credentials 옵션을 include로 설정해줘야 한다. 이러한 별도의 설정을 해주지 않으면 쿠키 등의 인증 정보는 절대로 자동으로 서버에게 전송되지 않는다.<br>


    * 위와 같은 설정을 통해 인증 정보를 요청에 포함시켰다면, 이 요청은 이제 인증 정보를 포함한 요청이 된다. 그리고 서버는 이러한 요청에 대해 일반적인 CORS 요청과는 다르게 대응해줘야 한다. 응답의 Access-Control-Allow-Origin 헤더가 와일드카드(*)가 아닌 분명한 Origin으로 설정되어야 하고, Access-Control-Allow-Credentials 헤더는 true로 설정되어야 한다. 그렇지 않으면 브라우저에 의해 응답이 거부된다<br>

[참조1](https://inpa.tistory.com/entry/WEB-%F0%9F%93%9A-CORS-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC-%ED%95%B4%EA%B2%B0-%EB%B0%A9%EB%B2%95-%F0%9F%91%8F#2._xmlhttprequest,_fetch_api_%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8) - 악명 높은 CORS 개념 & 해결법 - 정리 끝판왕 / Inpa Dev <br>[참조2](https://it-eldorado.tistory.com/163) - CORS (Cross Origin Resource Sharing) 이해하기 / IT엘도라도