# 5주차


## Ear Clip  
  <img src="https://github.com/sturdyChair/asset/blob/main/earClip.png" width="600" height="400"/>   

  
1. n번 정점 기준, n-1, n, n+1 정점의 convexity(winding order가 cw인지)   
2. convex하다면, 다른 정점이 해당 정점 내부에 존재하지 않는지   
3. 두 조건을 모두 만족하면 출력 face에 n-1, n, n+1 추가   
4. 정점 n을 리스트에서 제거, 1. 반복   

## 정적 메쉬 파괴  

### 조각 재분할
  <img src="https://github.com/sturdyChair/asset/blob/main/430/refracture.gif" width="600" height="400"/>   
  
### TODO  
- 조각 분할 단계 새분화(실시간 2중, 3중 분리)  

- 얇은 벽면(ex. 유리, 담장) 분할
  <img src="https://github.com/sturdyChair/asset/blob/main/430/ranbow%20six%20destruction.PNG" width="800" height="400"/>
  <img src="https://github.com/sturdyChair/asset/blob/main/430/ranbow%20six%20destruction%20result.PNG" width="800" height="400"/>  
  
  [The Art of Destruction in Rainbow Six: Siege (Julien L’Heureux)](https://media.gdcvault.com/gdc2016/Presentations/LHeureux_Julien_Art_Of_Destruction.pdf)
---

## 동적 메쉬 절단


### 메쉬 스냅샷  
  <img src="https://github.com/sturdyChair/asset/blob/main/430/static_slice.gif" width="600" height="400"/>   
  
  - 스킨드 메쉬의 현제 상태를 정적 메쉬로 저장, 절단
  - 일정 시간 후 각 조각에 물리 시뮬레이션
  - 절단시 새로 생성된 정점 위치에 파티클 생성


### TODO
  - 메쉬 스냅샷 -> 프랙쳐
    > 사전 분할 불가능 = 최적화 필요  
    > 비동기 실행 목표, 3프래임(약 0.5초)까지 최적화


---

## 캐릭터 부상
   <img src="https://github.com/sturdyChair/asset/blob/main/430/hand_hit.gif" width="600" height="400"/>
   <img src="https://github.com/sturdyChair/asset/blob/main/430/head_hit.gif" width="600" height="400"/>

### 정점 셰이더 메쉬 클리핑  
  - 최대 두개의 타원체를 기준으로 클립  
  - 클립된 구간에 기하 셰이더 이용, 분해 효과 

### 투사체 반응  
  <img src="https://github.com/sturdyChair/asset/blob/main/430/colliders.PNG" width="600" height="400"/>
  <img src="https://github.com/sturdyChair/asset/blob/main/430/projectile%20reaction.png" width="600" height="400"/>


