# 4주차

## 정적 메쉬 파괴  

### 프렉쳐 모드  
  <img src="https://github.com/sturdyChair/asset/blob/main/fracturemod%20web.gif" width="600" height="400"/>
  <img src="https://github.com/sturdyChair/asset/blob/main/fracturemod%20comb.gif" width="600" height="400"/>
  <img src="https://github.com/sturdyChair/asset/blob/main/fracturemod%20voxel.gif" width="600" height="400"/>

  - 알고리즘에 따라 규칙적으로 파티클 생성, 보로노이 분할
  
### 내부 머터리얼 선택  
  <img src="https://github.com/sturdyChair/asset/blob/main/material.gif" width="600" height="400"/>

### 프렉쳐 옵션  
- 조각 뭉치기  
  <img src="https://github.com/sturdyChair/asset/blob/main/cluster.gif" width="600" height="400"/>
- 크기 비율  
  <img src="https://github.com/sturdyChair/asset/blob/main/fracture%20scale.gif" width="600" height="400"/>
  
### TODO  
- 단계적 조각 파괴

---

## 동적 메쉬 절단


### 래그돌  
  <img src="https://github.com/sturdyChair/asset/blob/main/cut_0.gif" width="600" height="400"/>   
  
  - PxArticulation 사용[https://nvidia-omniverse.github.io/PhysX/physx/5.1.3/docs/Articulations.html]       
  - 절단된 객체에 래그돌 적용   
  - 절단면에 따라 래그돌 분리   

### 조각 처리  
  <img src="https://github.com/sturdyChair/asset/blob/main/dissolve.gif" width="600" height="400"/>   
  
  - 절단 횟수에 따라 수명 적용 (부모 수명 * 0.5)   
  - 수명이 다한 조각은 dissolve 이후 제거   

### 절단면  
  - 비볼록 평면 문제
   <img src="https://github.com/sturdyChair/asset/blob/main/non-convex%20face%20error.PNG" width="400" height="400"/>

  - Ear Clipping
    
    <img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjA7jQ25bCjYeFm7hlblz1l1u1x7xM6qwtI8bnW_Ca4_QCBBX0V-QvR1LjrBVUqQsxkNgbcpiJjix2Dbo7yEYBNqVCm8f_f2CKuunF1DFdI2nFyyu7_Kw6PKIyZ3fqLIkPgfaRg4CKctihv/s512/99..jpg" width="600" height="400"/>
   
  - 긴 삼각형

    <img src="https://github.com/sturdyChair/asset/blob/main/long%20triangle%20problem.png" width="400" height="400"/>

  
### 한계점
  - Solid Mesh에만 적용 가능   
  - 새로운 절단면에서 긴 삼각형이 등장하면 보기 좋지 않음

### 대안
  - Mesh Snapshot   
    메쉬의 현재 상태를 통해 static mesh 생성, 절단


---

## 캐릭터 부상
   <img src="https://github.com/sturdyChair/asset/blob/main/wound_prototype.PNG" width="600" height="400"/>

### 정점 셰이더 메쉬 클리핑
  - 스키닝 이전 정점을 가상의 타원체 local space로 전달, 타원체 내부에 포함되면 clip(혹은 다른 처리)   

### 스킨드 데칼
  - 가상 타원체 공간의 x, y 좌표를 데칼 UV로 사용


