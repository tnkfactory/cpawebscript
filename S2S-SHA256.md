## Web CPA 연동 가이드 (Server to Server 방식) (SHA-256)


### 1. 개요

본 문서는 TNK 네트워크을 통한 CPA(미션달성) 광고 진행시 구현해야 할 내용을 설명하고 있습니다.

<br/><br/>



### 2. 흐름도

![흐름도](https://cdn4.tnkfactory.com/tnk/shop/12334.jpg)






<br/><br/>



### 3. 광고 URL 

 TNK 네트워크 APP 내 지면에서 광고의 배너를 클릭하면 TNK 서버를 거쳐 광고 URL로 이동을 합니다.  
 이때 URL 뒤에 TNK 서버에서 생성한 클릭ID가 함께 전달 됩니다.  
 클릭ID는 매체,광고,기기정보를 암호화한 100 byte이내의 영문,숫자의 조합입니다.  
 클릭ID는 미션완료시 TNK 서버로 전송해야 하므로 중간에 유실 되지않도록 구현해야 합니다.  
  <br/> 
- URL : 광고 URL
- Method : GET
- Parameters :  

| 파라미터 명 | 최대길이 | 설명 |
| --- | --- | --- |
| adkey | 100 | 100 byte 이내의 영문,숫자의 조합의 암호화 된 문자열 |

- Response : redirect
- Example :  
https://your-site-url?a=1&b=2&adkey={클릭ID} 
```
https://your-site-url?a=1&b=2&adkey=85d75c07f20bf447f1e09efe88163864f4fe0684124fd2
```
<br/><br/>

### 4. Postback 

 유저가 광고참여 후 미션을 완료 했을때, 광고주 서버에서 TNK 서버로 클릭ID를 전송합니다.  
 추후 실적 비교 및 CS 확인 등을 위해 클릭ID는 DB에 참여 데이터와 함께 저장 해주세요.
<br/>

- Method : GET,POST
- Postback URL (HTTPS) :  
https://ads.tnkad.net/tnk/psb.postback.main  
- Parameters :  

| 파라미터 명 | 최대길이 | 설명 |
| --- | --- | --- |
| cbid | 100 | 광고URL에 전달된 {클릭ID} 값. (광고 URL에 adkey로 전달된 값) |
| chk\_cd | 64 | sha256(TNK + 클릭ID) 파라미터 검증 코드 (sha-256 hash string) |
| lb | 4 | 상수 = s2s3 |
| event | 15 | 상수 = action\_complete |

  
- Example :  
https://ads.tnkad.net/tnk/psb.postback.main?lb=s2s3&event=action_complete&cbid={클릭ID}&chk_cd={검증코드} 
```
https://ads.tnkad.net/tnk/psb.postback.main?lb=s2s3&event=action_complete&cbid=85d75c07f20bf447f1e09efe88163864f4fe0684124fd2&chk_cd=ca3cea5163068cb2e355886f0d12ce3b541f5cff76013c25a496927d25b2ff58  
```

- Response Type : text/html  
- Response Value :  S 또는 F
- Example :    
```
S
```
   
| 응답값 | 설명 |
| --- | --- |
| S | 성공 |
| F | 실패 |

<br/><br/>

### 5. 기술 문의
연동 중 문의사항이나 지원이 필요한 경우 아래 이메일 또는 연락하고 계신 담당자에 문의 바랍니다.  
tech@tnkfactory.com  
support@tnkfactory.com  




