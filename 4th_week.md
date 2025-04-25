# 4주차

## 정적 메쉬 파괴  

### 프렉쳐 모드  
  <img src="https://github.com/sturdyChair/asset/blob/main/fracturemod%20web.gif" width="600" height="400"/>
  <img src="https://github.com/sturdyChair/asset/blob/main/fracturemod%20comb.gif" width="600" height="400"/>
  <img src="https://github.com/sturdyChair/asset/blob/main/fracturemod%20voxel.gif" width="600" height="400"/>
  
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
- PxArticulation 사용([https://nvidia-omniverse.github.io/PhysX/physx/5.1.3/docs/Articulations.html])  
- 절단된 객체에 래그돌 적용
- 절단면에 따라 래그돌 분리

### 조각 처리  
  <img src="https://github.com/sturdyChair/asset/blob/main/dissolve.gif" width="600" height="400"/>
- 절단 횟수에 따라 수명 적용 (부모 수명 * 0.5)  
- 수명이 다한 조각은 dissolve 이후 제거

### 절단면  
-

### TODO
- 절단면 구현  
  새로 생긴 정점들 간의 단방향 간선 그래프 구성 => cycle 마다 하나의 절단면 생성
  
- 조각 처리





