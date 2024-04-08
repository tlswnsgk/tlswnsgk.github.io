---
title:  "ajax 배열 넘기기,동기적 통신"
excerpt: "Ajax traditional, async 통신 "

categories:
  - js
tags:
  - [js, traditional, async]

toc: true
toc_sticky: true
 
date: 2024-04-07
last_modified_at: 2020-05-25
---
- ajax

 - traditinoal

```
※ Ajax (Asynchronous JavaScript And XML)
빠르게 동작하는 동적인 웹 페이지를 만들기 위한 개발 기법의 하나. 원래 ajax는 비동기 화면을 구현하거나 웹 페이지 이동시 서버로의 데이터를 주고 받기위해 자주 사용하는데요.개발을 하다보면 배열을 넘겨야 하는 상황이 발생합니다.분명히 배열을 정확히 선언해서 서버로 보냈는데서버에서 찍히는 값은 null 또는 빈 공백으로 들어오는 경우가 있습니다.그래서 ajax에 선언해야 하는 방법중 하나가traditional
```

```
$.ajax({
    type : "get"
    , dataType : "json"
    , async: true
    , data : {"tchaidId" : tchaidId,
      "lendDe" : lendDe,
      "rturnDe" : rturnDe,
    }
    , traditional : true
    , url : "/tcha/checkTchaidRsv.json"
    , success : function(result) {
      if(result.data.reqstCnt > 0){
        selectQy = Number(result.data.nmprQy);
      }
      $('#nmpr').text(selectQy);
    }, error:function(data) {
      console.log(data);
    }
  });
```

이런 식으로 traditional : true로 넘기면 배열로 전송가능

 - async

```
function checkReturnCallFn(niceNm, dupeInfo, birth,addVar,telno) {
		$("#auth-check").show();
		$('.btn-mbl-auth').hide();
		console.log(niceNm+''+telno);
		let data = { ordrGroupNo:'${ordrInfo.ordrGroupNo}'}
		$.ajax({
			url:'/rsv/ordr/updateOrdrRqstInfo.json',
			data:data,
			type:'get',
			contentType:"application/json;charset=UTF-8",
			dataType: 'json',
			async: false,
			success:function (result) {
				if(result.success){
					$('#stlm-btn').show();
					$('#spt-stlm-btn').show();
				}else{
					openAlert(result.message);
					location.href=result.returnUrl;
				}
			}
		})
	}
```

jsp에서 서버와 통신을 해야하지만 ajax를 사용 후 새로고침이 필요한 경우
비동기 통신을 동기 통신으로 바꾸는 함수
 

---