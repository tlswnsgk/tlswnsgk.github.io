---
title:  "fremarker에 대해 알아보자"
excerpt: "fremarker에 대해 알아보자"

categories:
  - fremarker
tags:
  - [fremarker]

toc: true
toc_sticky: true
 
date: 2024-06-23
last_modified_at: 
---                                          
---
<h1>✔️FreeMarker란?</h1>
- "자바 템플릿 엔진인 프리마커는 FTL이라는 언어를 통해 템플릿을 작설할 수 있도록 한다.<br>
  FTL에는 간단한 데이터 치환 뿐만 아니라 조건문이나 반복문 같은 다양한 문법과 기능이 구현되어 있다.<br>
  따라서 FTL 문법을 잘 알고 있으면 효율적으로 템플릿을 작성할 수 있다."<br>

<h1>✔️assign</h1>
>템플릿 작성시 변수를 사용하고 싶을 때, assign 디렉티브를 사용할 수 있다. 예를 들어

```
<#assign name="Dave">

<#assign codeBlock>
     this code block assigned
</#assign>

```

assign 디렉티브를 이용해 'name'이라는 변수에 "Dave"라는 값을 저장할 수 있다. 이후 ${name}을 사용하면 name 변수에 저장된 "Dave"라는 값이 ${name} 부분에 치환된다.<br>
간단한 문자열, 단어뿐아니라 <#assign>과 사이에 있는 코드 블럭을 변수처럼 할당해서 사용할 수도 있다.<br><br>

<h1>✔️attempt, recover</h1>
>자바에서 사용하는 try-catch 블럭과 유사한 개념이다.<br><br>

```
<#attempt>
    attempt block
<#recover>
    recover block
</#attempt>
```

attempt block의 템플릿이 우선 해석된다. 그러다가 예외가 발생하거나 문제가 생기면 attempt block에서 진행되던 작업은 모두 롤백되고 recover block의 내용이 해석된다.<br>
자바의 try-catch 구문처럼 여러 번 중첩해서 사용할 수 있다.<br>

<h1>✔️autoesc</h1>
>오토 이스케이핑(Auto escaping)과 관련된 기능이다.<br>

```

<#autoesc>
    ...
</#autoesc>

```

웹 페이지와 관련된 데이터를 다루다보면 XML,HTML 같은 문서에서 이스케이핑 해야하는 문자들이 있다. 예를 들어 '<' 문자나 '>' 문자는 XML,HTML 문서에서 특수한 역할을 한다.
만약 이 문자를 문자 그대로 사용하고 싶은 경우라면 별도로 이스케이핑을 해야한다. (이런 문자들은 이스케이핑해서 엔티티로 만들어 사용하야한다.)<br><br>
일반적으로는 freemarker,core,OutputFormat에 HTML,XML,XHTML 등을 설정하거나 text/html, application/xml 같은 MIME 타입을 설정해주면 자동으로 Excaping이 실행되기 때문에 이 디렉티브는 잘 사용하지 않는다.<br><br>

```
${expression?esc}
```

참고로 Auto Escaping 기능이 활성화 되지 않은 상황에서 하나의 interpolation을 Escaping 하려면 "?esc"를 붙여주면 된다.<br><br>

<h1>✔️compress</h1>
불필요한 공백문자(White-space)를 결과에서 제거하는데 사용된다.<br><br>

```
<#compress>
...
</#compress>
```

HTML이나 XML 같이 공백 문자가 주요하게 사용되는 경우 사용자 데이터에서 불필요한 공백문자를 지울 필요가 있는데, 이 때 '<#compress>' 디렉티브를 사용하면 된다.<br><br>
이 디렉티브를 사용하면 <#compress> 블럭 내에서 2개 이상의 공백 문자가 반복해서 등장하는 경우를 감지해서 하나의 공백문자로 줄여준다. 줄바꿈 문자도 여러개가 등장하면 하나로 줄여준다.<br>
줄바꿈 문자도 여러 개가 등장하면 하나로 줄여준다. 맨 처음과 맨 마지막에 등장하는 공백과 줄바꿈 문자들은 제거된다.<br>


<h1>✔️flush</h1>
템플릿 파일의 맨 처음부분에 사용되는 디렉티브다. 템플릿 파일에 대한 정보를 프리마커 엔진에 알려주는 역할을 한다.<br>

```
<#fcl param1 = value1 param2=value2 ...>

```

param1,param2 같은 특정 파라미터의 값을 설정하는 디렉티브로 'encoding', 'strip_whitespace', 'strip_text' 등이 사용될 수 있으며, 값으로는 'ISO-8859-5' 같은 게 사용될 수 있다.<br><br>

<h1>✔️function, return</h1>

템플릿 파일 내부에서 사용할 함수를 정의한디. 'marco' 디렉티브와 비슷하지만 function 디렉티브에서는 반드시 return 디렉티브로 반환 값을 명시해야 한다.<br>

```
<#function name param1 param2 ... paramN>
  ...
  <#return returnValue>
  ...
</#function>

```

function 디렉티브 내에서 만들어내는 문서 출력은 모두 무시가 된다. 내부 로직에 의해서 값을 계산하고 reutrn 디렉티브로 결과를 반환하는 작업만 수행된다.<br>
function 디렉티브 내부에서 if, list 등의 다른 디렉티브는 사용할 수 있다.<br><br>

<h1>✔️global</h1>

전역 변수를 만들어낸다.<br>

```
<#global name=value>
or
<#global name1=value1 name2=value2 ... nameN=valueN>
or
<#global name>
    capture this
</#global>

```

<#assign> 디렉티브와 비슷한 역할을 한다. 다만 assign 디렉티브로 만들어진 변수는 모든 네임스페이스(namespace)에서 보이게 된다.<br>
global 디렉티브로 정의한 변수의 이름이 assign으로 정의한 변수의 이름과 같다면 assign으로 정의한 변숙 유효한 네임스페이스에서는 global 디렉티브로 정의한 변수 대신 assign으로 정의한 변수가 보이게 된다.<br>
변수의 스코프에 대해서 잘 알고 사용해야 한다.<br>

<h1>✔️if, else, elseif </h1>
템플릿에서 사용할 수 있는 조건문이다.

```
<#if condition>
   ...
<#elseif condition2>
   ...
<#elseif condition3>
   ...
<#else>
   ...
</#if>
```

조건문에서 값의 비교를 할 때 주의해야 할 점이 있다. 바로 "x>0" 혹은 "x>=0" 같은 조건식을 사용할 때 ,에러가 발생한다. '>' 문자는 프리마커에서 디렉티브를 나타내는 특수문자이기 떄문이다. 크다 작다를 '>' ,'<' 문자대신 gt,gte,lt,lte 로 표현해야 한다.
즉, <#if x ft 0> 혹은 <#if x gte 0>로 작성해야 한다.

<h1>✔️list, else, items, seq, break, continue(반복문) </h1>
데이터 모델의 자식 노드들을 순회하는 반복문과 관련된 디렉트브들이다.<br>

```
<#list sequence as item>
    list block here
</#list>
```

```
<#list users as user>
    ${user}
</#list>

```

```
<#list hash as key, value>
    list block here
</#list>
```

```
<#list sequence as item>
    Part repeated for each item
<#else>
    Part executed when there are 0 items
</#list>
```

```
<#list sequence>
Part executed once if we have more than 0 items
<#items as item>
Part repeated for each item
</#items>
Part executed once if we have more than 0 items
<#else>
Part executed when there are 0 items
</#list>
```

<h1>✔️seq </h1>
List 디렉티브 내부에서 사용할 수 있는 디렉티브 중에 seq 디렉티브가 있다. 컬렉션 데이터를 출력할 때, 구분자로 사용하고 싶은 문자를 넣을 때 사용된다.<br>

```
<#list users as user>
${user}<#sep>, </#sep>
</#list>
```

이렇게 명시하면 각 user의 출력 사이에 ',' 문자를 준다. seq 디렉티브가 편한 이유는 마지막 항목에서는 자동으로 구분자를 빼주기 때문이다.<br>

<h1>✔️marco, nasted, return </h1>
매크로(macro) 변수를 생선한다. 매크로는 템플릿 파일의 조각으로 사용자 정의 디렉티브(User-defined directive)로 사용될 수 있다.

```
<#macro name param1 param2 ... paramN>
...
<#nested loopvar1, loopvar2, ..., loopvarN>
...
<#return>
...
</#macro>
```

매크로의 사용처가 매크로의 정의보다 먼저 등장해도 상관없다. 하지만 매크로의 정의가 include 디렉티브에 의해서 포함되는 경우라면, 매크로의 사용처보다 include 디렉티브가 먼저 등장해야한다.<br><br>

<h2>naster</h2>
naster 디렉티브는 <#macro>와 </#macro> 사이에 있는 템플릿 조각을 실행하는데 사용된다.<br>

```
<#macro foo >
  * <#nested>
  * <#nested>
</#macro>

<@foo>Hello</@foo>
```

이 템플릿의 경우, naster 부분에 Hello가 대체되어서 출력된다.<br>

naster는 loop 변수를 포함할 수 있다.<br>
예를 들어<br>

```
<#macro foo>
   <#list 1..5 as i>
      <#nested i, i * 2, i/2>
   </#list>
</#macro>

<@foo ; first, second, thrid>
i = ${first}
i * 2 = ${second}
i / 2 = ${third}
</@foo>
```

<h2>return</h2>
return 디렉티브를 만나면 macro, function의 실행을 종료한다.<br>

<h1>✔️noautoesc</h1>
오토 이스케이핑 기능을 사용하지 않는 구역을 만든다. autoesc 디렉티브의 반대 개념.<br>

```
<#noautoesc>
...
<#/noautoesc>
```

하나의 interpolation에만 적용하려면 ${expression?no_esc}로 사용하면 된다.<br>

<h1>✔️noparse</h1>
프리마커 언어로 해석되지 않는 구역을 만든다.<br>

```
<#noparse>
...
</#noparse>
```

noparse 구역에서는 프리마커 언어의 문법이 해석되지 않는다. 다만 </#noparse> 구문은 해석된다.<br>

<h1>✔️nt</h1>
No-Trim의 약자, 이 디렉티브가 있는 라인은 공백 문자를 Stripping을 하지 않는다.<br>

<h1>✔️outputformat</h1>
출력 포맷 설정을 변경한다.<br>

```
<#outputformat formatName>
...
<#/outputformat>
```

formatname으로는 "HTML","XML" 등이 사용될 수 있다. output 포맷을 적절하게 설정하면, 그 포맷에서 사용하는 특수 문자들을 자동으로 이스케이핑 해준다.<br>
outputformat 디렉티브가 끝나면, 이전에 설정되었던 outputformat으로 자동 복귀된다.<br><br>

<h1>✔️setting</h1>
이후 프로세싱에 영향을 미칠 설정 값들을 변경한다.<br>

```
<#setting name=value>
```

이 설정값들은 프리마커 엔진의 해석 방식에 영향을 주게 된다.<br>

예를 들어, 이 디렉티브로 locale, number_format, bollean_format, date_format 등을 변경하게 되면, 이 후에 프리마커 엔진이 데이터를 처리할 때마다 여기에서 바꾼 설정값에 따라 움직이게 된다.<br>

<h1>✔️stop</h1>
템플릿의 프로세싱을 종료한다.<br>

```
<#stop>
or
<#stop reason>
```

에러메시지를 줄 수도 있다. 일반적이지 않은 에러 상황에서만 사용해야 한다.<br>

<h1>✔️switch, case, default, break</h1>

```
<#switch value>
<#case refValue1>
...
<#break>
<#case refValue2>
...
<#break>
...
<#case refValueN>
...
<#break>
<#default>
...
</#switch>
```

value의 값에 따라 수행해야하는 블럭이 결정된다.<br>

<h1>✔️t, lt, rt</h1>

공백 문자의 Trim 동작에 대한 디렉티브이다. 이 디렉티브가 있는 라인은 다음과 같이 동작한다.<br>
- t : 앞 뒤 공백문자를 제거한다.<br>
- lt : 왼쪽에 있는 공백 문자를 제거한다.<br>
- rt : 오른쪽에 있는 공백 문자를 제거한다.<br>

<h1>✔️사용자 정의 디렉티브(User-defined directive)</h1>
매크로에서 설명한 내용과 동일하다. 시스템 디렉티브와 다르게 골뱅이(@)로 시작한다.<br>

<h2>visit, recurse,fallback</h2>
재귀적인 방법으로 트리를 순회하며 데이터를 처리하고 싶을 때 사용하는 디렉티브, 실제로는 XML데이터를 다룰 때 많이 사용한다.<br>

```
<#visit node using namespace>
or
<#visit node>
<#recurse node using namespace>
or
<#recurse node>
or
<#recurse using namespace>
or
<#recurse>
<#fallback>
```

- <#visit node>를 호출하면 node?node_name에 해당하는 매크로를 찾아서 실행시켜준다. 만약 node_name에 해당하는 매크로가 없으면, @node_type 이름을 갖는 매크로를 찾아서 실행한다. 만약 이것도 없으면 템플릿 프로세싱은 에러를 내면서 종료한다.<br><br>
- <#recurse node using ns>는 <#list node?children as child><#visit child using ns><#list>와 동일한 동작을 한다. 짧게 쓰기 위해 사용한다.<br><br>
- visit 디렉티브에 의해서 사용자 정의 디렉티브가 찾아진다. 이 때, fallback 디렉티브를 만나면, 다른 네임스페이스에서 node?node_name에 해당하는 매크로를 찾아보도록 프리마커 엔진에게 알려준다. 같은 이름의 매크로를 오버라이드해서 사용하는 경우 적당한 처리를 위해서 사용할 수 있다.<br><br>


---