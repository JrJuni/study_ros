# ROS 학습 저장소 백로그

마지막 갱신: 2026-08-02 (Asia/Seoul)

## 프로젝트 목표

ROS 2, URDF와 NVIDIA Isaac Sim을 단계적으로 학습하고, 최종적으로 ROS 2에서
보낸 목표 각도로 Isaac Sim 안의 1자유도 회전 관절을 움직인다.

## 현재 위치

- 현재 장: **3장 ROS 2 워크스페이스 준비**
- 마지막으로 완료한 실습: CLI에서 `/chatter` 문자열을 직접 발행하고
  listener에서 수신
- 마지막으로 확인한 환경: `colcon`이 `/usr/bin/colcon`에 설치됨
- 다음 한 단계: `/home/junibecky/study_ros/ros2_ws/src` 생성 및 경로 확인

## 학습 환경

| 항목 | 현재 상태 |
| --- | --- |
| 운영체제 | Ubuntu 24.04.4 LTS, x86_64 |
| CPU | AMD Ryzen 5 7500F, 6코어 12스레드 |
| GPU | NVIDIA RTX 4070 Ti SUPER, VRAM 약 16GB |
| NVIDIA 드라이버 | 595.84 |
| RAM / Swap | 약 32GB / 8GB |
| 저장 공간 | 루트 디스크 450GB 여유 |
| Python | 3.12.3 |
| ROS 2 | Jazzy, `/opt/ros/jazzy` |
| colcon | `/usr/bin/colcon` |

## 완료한 학습

### 0장 학습 안내

- [x] 전체 목표와 단계별 학습 경로 정리
- [x] ROS 2, URDF, Omniverse와 Isaac Sim의 역할 구분

### 1장 설치와 환경 점검

- [x] 운영체제, CPU, GPU, VRAM, RAM과 저장 공간 확인
- [x] ROS 2 Jazzy 설치와 터미널 환경 확인
- [x] Isaac Sim 4.5, 5.0, 6.0 계열 비교
- [x] Isaac Sim 6.0 계열을 우선 시험하는 것으로 결정

### 2장 ROS 2 노드와 토픽

- [x] 노드, 토픽, 메시지, 발행자와 구독자 개념 학습
- [x] C++ talker와 Python listener 통신
- [x] `ros2 node list`로 실행 중인 노드 확인
- [x] `ros2 topic list -t`와 `ros2 topic info`로 토픽 관찰
- [x] `ros2 topic echo`로 실제 메시지 구조 확인
- [x] `ros2 interface show`로 메시지 필드 확인
- [x] CLI에서 `/chatter` 메시지 직접 발행
- [x] 실제 메시지와 ROS 로그의 부가 정보 구분

### 3장 ROS 2 워크스페이스 준비

- [x] `colcon` 설치 위치 확인
- [ ] `ros2_ws/src` 디렉터리 생성
- [ ] 워크스페이스의 `src`, `build`, `install`, `log` 역할 확인
- [ ] 첫 `ament_python` 패키지 생성
- [ ] `colcon build`로 패키지 빌드
- [ ] 빌드 결과 환경 불러오기

## 다음 학습 순서

### 가까운 목표

1. ROS 2 워크스페이스 생성
2. Python 패키지 구조 확인
3. Python publisher 노드 작성
4. Python subscriber 노드 작성
5. 직접 만든 두 노드의 토픽 통신 확인

### 이후 목표

1. 좌표계와 TF 기초
2. URDF의 `link`와 `joint`
3. 1자유도 회전 관절 모델 작성
4. Isaac Sim Compatibility Checker 실행
5. Isaac Sim 설치와 기본 장면 확인
6. URDF 가져오기와 관절 직접 제어
7. ROS 2 Bridge 연결
8. ROS 2 목표 각도로 관절 제어

## Isaac Sim 선택 기록

- 우선 후보: **Isaac Sim 6.0 계열**
  - Ubuntu 24.04와 ROS 2 Jazzy 조합이 현재 환경과 가장 잘 맞는다.
  - RTX 4070 Ti SUPER가 공식 최소 GPU보다 낮으므로 호환성 검사를 통과한 뒤
    설치를 확정한다.
- Isaac Sim 5.0은 GPU 최소 기준이 낮아지지 않고 내부 Python 3.11 때문에
  사용자 정의 ROS 패키지 연동이 더 복잡해 우선 후보에서 제외한다.
- Isaac Sim 4.5는 GPU 요구사항은 낮지만 Ubuntu 22.04와 ROS 2 Humble 조합이
  필요하므로 별도 환경을 마련할 때만 검토한다.

## 문서 작성 규칙

- 날짜 문서는 `docs/lesson_YYMMDD.md` 형식을 사용한다.
- 큰 카테고리는 `0장`, `1장`으로 나누고 세부 절은 `0-1`, `0-2`,
  `1-1` 형식으로 번호 매긴다.
- 각 장은 **장의 학습 목표 → 세부 주제 → 내용 설명 → 예제 또는 실습** 구조를
  따른다.
- 0장의 학습 목표에는 전체 과정의 목표와 학습 경로를 적는다.
- 대화 내용을 시간순으로 복사하지 않고 같은 개념과 실습을 통합한다.
- 실제 출력은 성공 판단에 필요한 핵심 부분만 남긴다.
- 특정 컴퓨터나 Codex에만 해당하는 문제는 ROS 교재 본문에서 제외한다.
- 버전과 설치 정보는 공식 문서를 확인하고 확인 날짜를 남긴다.

## 저장소 관리

- 개인 학습 저장소이므로 기본적으로 `main`에서 직접 작업하고 푸시한다.
- 날짜별 교재 갱신 스킬은 `.agents/skills/update-ros-lessons/`에 있다.
- 문서와 스킬의 장–절 구조 규칙은 2026-08-02에 정리했다.
- 초기 Codex/AppArmor 문제는 해결됐으며 ROS 학습 내용이 아니므로 상세 과정은
  날짜별 교재에서 제외했다. 필요하면 Git 이전 기록에서 확인할 수 있다.

## 다음 세션 재개 방법

```text
BACKLOG.md를 먼저 읽고 현재 위치의 미완료 항목부터 이어서 진행해줘.
기존 파일을 보존하고 완료한 항목은 체크해줘.
```

저장소 상태 확인:

```bash
cd /home/junibecky/study_ros
git status --short --branch
```
