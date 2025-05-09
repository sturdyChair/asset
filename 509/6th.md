# 6주차




## 스킨드 메쉬 프랙쳐    
  <img src="https://github.com/sturdyChair/asset/blob/main/509/skinnedmesh_fracture.gif" width="600" height="400"/>   

  - 멀티스레딩 이용 비동기 실행   
  - nvidia blast : 0.6초 / 자작 voronoi + mesh boolean : 1.3초
### 대안   
  - 사전 프랙쳐 -> 각 조각과 bone 연결 -> 파괴시 해당 bone 위치에서 조각 생성


---

## 캐릭터 부상
   <img src="https://github.com/sturdyChair/asset/blob/main/509/FilledWound.gif" width="600" height="400"/>

### 정점 셰이더 메쉬 클리핑  
  - 최대 두개의 타원체를 기준으로 클립  
  - 클립된 구간에 기하 셰이더 이용, 분해 효과 

### 부상 내부 구현   
1. 스텐실에 캐릭터 메쉬 뒷면 기록   
2. 스텐실에 기록된 부분에만 구체 뒷면 렌더링   



---

## 부술 수 있는 벽

### 구현 계획   
  - 사전 분할, 조각 계층화 이용
  - 입자 위치, 인접성 기반으로 조각 분할 결정
