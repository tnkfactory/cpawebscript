## Web CPA 연동 가이드 (S2S 방식)

1. 랜딩 페이지 URL에 파라미터가 &adkey={adkey} 추가 전달 됩니다.

```
   https://your_url?adkey={adkey}
```
```    
ex) https://www.tnkfactory.com/?adkey=85d75c07f20bf447f1e09efe88163864f4fe0684124fd2
```

2. 유저가 액션(사전예약완료, 개좌개설완료 등 이벤트 완료)을 완료하면 아래 Postback URL을 호출해주시면 됩니다.
```
 https://ads.tnkad.net/tnk/psb.postback.main?lb=s2s&cbid={adkey}&event=action_complete
```
```
ex) https://ads.tnkad.net/tnk/psb.postback.main?lb=s2s&cbid=85d75c07f20bf447f1e09efe88163864f4fe0684124fd2&event=action_complete
```

