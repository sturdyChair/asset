# 7주차




## 스킨드 메쉬 프랙쳐    
  <img src="https://github.com/sturdyChair/asset/blob/main/516/SkinnedFracture%20-%20Trim.gif" width="600" height="400"/>   
 
  - 실시간 비동기 실행시 -> 20조각에 약 0.6초   
  - preskinned pose로 사전 프랙쳐    
  - 각 프랙쳐의 geometry를 적절한 Bone과 연결   


---

## 캐릭터 부상
   <img src="https://github.com/sturdyChair/asset/blob/main/516/wound%20-%20Trim.gif" width="600" height="400"/>


### 부상 내부 구현   
1. 스텐실에 캐릭터 메쉬 뒷면 기록   
2. 스텐실에 기록된 부분에만 구체 뒷면 렌더링   
3. 구체를 3 * 3 * 3 큐브로 분할, 각 조각을 적절한 Bone에 연결   



---

## 부술 수 있는 오브젝트   

   
### 조각 + Breakable Joint      
   <img src="https://github.com/sturdyChair/asset/blob/main/516/Break_Proto%20-%20Trim.gif" width="600" height="400"/>   

  - 출렁거림   
  - 피해량 커스텀이 어려움   


### 단일 액터 + Bond   
   <img src="https://github.com/sturdyChair/asset/blob/main/516/BreakBetter%20-%20Trim_1.gif" width="600" height="400"/>   
   <img src="https://github.com/sturdyChair/asset/blob/main/516/BreakBetter%20-%20Trim_2.gif" width="600" height="400"/>    

  - 출렁임 해결   
  - 물리적 상호작용 이외의 커스텀 가능   



