---

## **1. 개요**
- 보로노이 다이어그램을 이용한 사전 분할 기법 적용  
- Nvidia PhysX를 활용한 물리 시뮬레이션과 결과 저장


---

## **2. 목표**
- 보로노이 다이어그램을 이용한 메쉬 분할 시스템 개발
  > ![img](https://github.com/sturdyChair/asset/blob/main/chaosdestruction_hero.png)
- 물리적 파괴 효과의 자연스러운 구현
- 시뮬레이트 결과를 키프레임으로 저장, 재사용 기능
- Extra) Blender의 Bisect와 같은 기능을 동적으로 구현
  > ![img](https://i.gifer.com/5S2u.gif)
---

## **3. 진행**

### **1: 메쉬 분할 시스템 개발**
- 1. 파티클 간의 관계를 이용해 정확한 보로노이 다이어그램 생성 (진행중)
	> 각 보로노이 셀을 분할하는 평면을 이용해 정점 생성
	> Voronoi Cell class 구현 중
- 2. 복셀 기반의 브루트포스를 이용한 유사 보로노이 다이어그램 생성
	> 공간을 격자로 나눈 후 각 복셀이 어떤 파티클과 가장 가까운지 계산, 각 파티클에 포함된 복셀을 기준으로 정점 생성
 	> 각 격자마다 병렬 계산이 가능
 > ![img](https://github.com/sturdyChair/asset/blob/main/VV.png)
- 3. 하나의 평면을 이용한 메쉬 양분할
	> 비교적 알고리즘이 간단

### **2: 물리 시뮬레이션 환경 구축**
- Nvidia PhysX를 프로젝트에 적용 (해결)
- 간단한 지형과 동적 액터 생성 테스트 (해결)


### **3: 데이터 저장, 재사용 구현**
- Voronoi Cell class의 정점 정보를 이용해 (1)vertex buffer 구성 / (2)재사용 가능한 Mesh로 export
- 디테일 레벨에 따라 Voronoi Cell 여러개를 하나의 Bone에 할당, 시뮬레이트 결과 저장
 > ![img](https://github.com/sturdyChair/asset/blob/main/Bone.png)
---


## **4. 향후 계획 및 과제**
- 메쉬 분할 알고리즘 최적화  
- 머터리얼에 따른 파괴 효과 테스트
- 분할 단면 텍스쳐 처리

---

