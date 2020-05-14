# 지하철 경로 조회

## 1단계 - 캐시 적용
### 요구사항
 + [x] HTTP 캐시 적용하기
   + [x] HTTP Cache의 종류를 학습
   + [x] 지하철 노선도 조회 시 ETag를 통해 캐시를 적용
   + [x] LineControllerTest의 ETag 테스트를 성공 시키기
 + [ ] 서버 캐시 적용
 
## 2단계 - 지하철 경로 조회 1
### 요구사항
+ [x] 출발역과 도착역의 최단 경로를 조회하는 기능 구현
+ [x] 기본적인 기능 구현(Happy Case)을 목표로하고 예외 상황(Side Case)에 대한 처리는 다음 단계에서 고려
+ [x] TDD 프로세스를 따라서 개발 진행
+ [x] 인수 조건 & 인수 테스트 작성
+ [x] 기능 구현시 필요한 단위 테스트 작성
+ [x] 중복코드를 제거(테스트 코드도 마찬가지로 중복제거)
+ [ ] 객체지향 생활체조 준수

### 기능 목록
경로 조회 API
 + 출발역과 도착역을 입력
 + 최단 거리 기준으로 경로와 기타 정보를 응답
    + 총 소요시간, 총 거리 등
 + 최단 경로가 하나가 아닐 경우 어느 경로든 하나만 응답

경로 조회 화면
 + 출발역과 도착역의 경로 정보 노출
 + 총 소요시간, 정차역 등
 + 즐겨찾기 버튼과 최소시간 기준 조회는 다른 미션이므로 무시
 + 최소시간 기준은 3단계 미션
 + 즐겨찾기(별)은 3주차 미션
 
### 시나리오
 ```gherkin
Scenario: 지하철 경로 조회를 한다.
     Given 지하철역이 여러 개 추가되어있다.
     And 지하철 노선이 추가되어있다.
     And 지하철 경로가 여러 개 추가되어있다.

     When 출발역과 도착역을 입력하여 최단 경로를 조회하는 요청을 한다.
     Then 최단 거리 기준으로 경로와 기타 정보를 응답한다.
     And 소요시간과 거리등의 정보를 포함한다.
     And 최단 경로는 하나만 응답한다.
```

## 3단계 - 지하철 경로 조회 2
### 요구 사항
 + [x] Happy 케이스 이외 예외 상황에 대한 기능 구현
 + [x] 단위 테스트를 통해 Side 케이스 검증 => 인수 테스트를 통해 테스트 비용 절감

### 기능 목록
 + [x] 출발역과 도착역이 같은 경우
 + [x] 출발역과 도착역이 연결이 되어 있지 않은 경우
 + [x] 존재하지 않은 출발역이나 도착역을 조회 할 경우
 
## 4단계 - 지하철 경로 조회 3
### 요구 사항
 + [ ] 최소 시간 경로 기능을 추가
 + [ ] 최단 경로 조회 기능과의 중복 제거를 수행(테스트 코드도 마찬가지로 중복제거)