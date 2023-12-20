## Web CPA 연동 가이드 (script 방식)

1. 랜딩 페이지(이벤트 페이지)에 아래 스크립트를 추가 합니다.

```
<script src="https://api3.tnkfactory.com/tnk/js/tnk-webapi-cpatrack.1.4.js"></script>
```
2. 액션(미션)을 완료하는  페이지에 아래 스크립트를 추가합니다.

그리고 액션(미션)을 완료하는 시점에  TnkSession.actionCompleted(); 함수를 호출합니다.
```
<script src="https://api3.tnkfactory.com/tnk/js/tnk-webapi-cpatrack.1.4.js"></script>

<script>

  TnkSession.actionCompleted(); // 액션이 완료된 시점에 호출한다.

</script>
```

* 주의

쿠키를 사용하기때문에 랜딩 페이지와 미션 완료페이지의 도메인이 같아야 합니다.



<br/><br/><br/><br/><br/><br/>
참고: [S2S 방식 가이드](./S2S.md)
