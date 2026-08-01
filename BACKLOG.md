# ROS 학습 저장소 작업 백로그

마지막 갱신: 2026-08-02 (Asia/Seoul)

## 프로젝트 목표

로봇 입문 학생이 ROS 2, URDF, NVIDIA Isaac Sim과 Omniverse를 단계적으로
학습하고, 최종적으로 Isaac Sim 안의 1자유도 관절을 ROS 2로 움직인다.

## 문서 작성 결정 사항

- Codex 표준 지침 파일은 저장소 루트의 `AGENTS.md`로 만든다.
- 날짜별 학습자료는 `docs/lesson_YYMMDD.md` 형식으로 작성한다.
- 날짜는 Asia/Seoul을 기준으로 한다.
- 2026년 8월 2일 문서 이름은 `docs/lesson_260802.md`다.
- 같은 날짜에 학습을 이어 가면 새 파일을 만들지 않고 기존 파일을 갱신한다.
- 모든 학습 주제는 다음 네 부분을 순서대로 포함한다.
  1. 주제
  2. 학습 목표
  3. 내용 설명
  4. 예제 또는 실습
- 독자는 로봇과 리눅스를 처음 접하는 고등학생 수준으로 가정한다.
- 문서는 한국어로 쓰고, 새로운 영어 용어는 처음 등장할 때 설명한다.
- 코드와 명령에는 초보자용 주석, 실행 위치, 예상 결과, 성공 확인 방법을 넣는다.
- 실제로 실행한 실습과 아직 예정인 실습을 명확하게 구분한다.
- 바뀔 수 있는 버전·지원 환경·설치 정보는 공식 문서를 확인하고 출처와 확인일을 남긴다.

## 예정된 학습 카테고리

1. 학습 안내와 프로젝트 관리
2. 설치와 환경 점검
3. 터미널, Git과 Python 기초
4. ROS 2 기본 개념과 CLI
5. ROS 2 Python 프로그래밍
6. 좌표계, TF와 로봇 모델링
7. URDF와 Xacro
8. Omniverse, USD와 Isaac Sim 기초
9. Articulation과 관절 제어
10. ROS 2 Bridge 연동
11. 검증과 문제 해결
12. 1자유도 관절 종합 프로젝트

## 완료된 작업

- GitHub 저장소 `JrJuni/study_ros`를 `/home/junibecky/study_ros`에 복제했다.
- 원격 저장소의 기본 브랜치는 `main`이며 첫 학습자료를 병합했다.
- 프로젝트 로컬 학습자료 스킬을 다음 위치에 완성했다.
  - `.agents/skills/update-ros-lessons/`
- `docs/` 디렉터리를 만들었다.
- Codex Linux 샌드박스 오류의 원인을 진단했다.
  - 이전 오류: `bwrap: loopback: Failed RTM_NEWADDR: Operation not permitted`
  - 원인: AppArmor가 `bwrap`의 `net_admin`과 `setpcap` capability를 거부함
- `apparmor-profiles`와 `apparmor-utils`를 설치했다.
- `/etc/apparmor.d/bwrap-userns-restrict` 프로파일을 설치하고 로드했다.
- 현재 Codex 0.146.0에 맞는 다음 테스트가 성공했다.

```bash
codex sandbox -- /usr/bin/true
```

## 아직 완료되지 않은 작업

- [x] 저장소 루트에 `AGENTS.md` 작성
- [x] `README.md`에 프로젝트 목표와 학습자료 링크 추가
- [x] `docs/README.md`에 카테고리, 파일명, 네 단계 문서 규칙 작성
- [x] 오늘까지 진행한 내용을 `docs/lesson_260802.md`로 작성
- [x] `.agents/skills/update-ros-lessons/SKILL.md`의 TODO 템플릿을 실제 규칙으로 교체
- [x] 스킬에 날짜별 교재 템플릿 reference 추가
- [x] `agents/openai.yaml` 메타데이터 확인
- [x] skill-creator의 `quick_validate.py`로 스킬 검증
- [x] 전체 Markdown 구조와 Git 공백 오류 검토
- [x] 변경사항을 사용자에게 보여주고 커밋·푸시 요청 확인

## 오늘 학습자료에 포함할 내용

- ROS 2, URDF, Omniverse와 Isaac Sim의 역할
- 최종 목표까지의 단계별 학습 로드맵
- 설치 전 운영체제와 하드웨어 점검이 필요한 이유
- Ubuntu 및 Windows 환경 확인 명령
- 현재 검토 중인 기본 조합
  - Ubuntu 24.04
  - ROS 2 Jazzy
  - NVIDIA Isaac Sim 6.0.1
- Python 3.12
- Isaac Sim 4.5, 5.0, 6.0 계열의 운영체제·ROS 2·Python·GPU 요구사항 비교
- 현재 환경에서는 Isaac Sim 6.0 계열을 우선 시험하고 호환성 검사 뒤 확정한다는 주의사항
- Codex `bwrap`/AppArmor 오류의 원인과 해결 과정

## 현재 환경 점검 진행

- [x] Ubuntu 24.04.4 LTS 및 x86_64 확인
- [x] AMD Ryzen 5 7500F, 6코어 12스레드 확인
- [x] RTX 4070 Ti SUPER, VRAM 약 16GB, 드라이버 595.84 확인
- [x] RAM 약 32GB, Swap 8GB 확인
- [x] 루트 저장 공간 450GB 여유 확인
- [x] Python 3.12.3 확인
- [x] ROS 2 실행 파일 `/opt/ros/jazzy/bin/ros2` 확인
- [x] `ROS_DISTRO=jazzy` 및 설치 경로 `/opt/ros/jazzy` 확인
- [x] Isaac Sim 4.5, 5.0, 6.0 계열의 공식 요구사항 비교
- [x] ROS 2 talker/listener 기본 통신 실습
- [x] 실행 중인 노드와 토픽을 ROS 2 CLI로 관찰하는 실습
- [x] 메시지 인터페이스 확인 및 CLI에서 `/chatter` 직접 발행
- [ ] ROS 2 워크스페이스와 패키지 구조 학습
- [ ] Isaac Sim 공식 호환성 검사 실행
- [ ] 호환성 검사 결과에 따라 Isaac Sim 6.0 계열 설치 여부 확정

## Isaac Sim 버전 선택 기록

- 우선 후보: Isaac Sim 6.0 계열
  - Ubuntu 24.04와 ROS 2 Jazzy가 공식 권장 조합이다.
  - Python 3.12 기반 ROS 라이브러리를 사용하므로 현재 환경과 잘 맞는다.
  - RTX 4070 Ti SUPER는 공식 최소 GPU인 RTX 4080보다 낮으므로 설치 전
    Compatibility Checker를 실행하고 단순한 1관절 장면부터 시험한다.
- 제외 후보: Isaac Sim 5.0
  - Ubuntu 24.04와 Jazzy는 지원하지만 최소 GPU 요구사항이 6.0과 같은
    RTX 4080이어서 GPU 부담을 줄이는 대안이 아니다.
  - Isaac Sim 내부 Python 3.11과 시스템 Python 3.12의 차이 때문에 사용자 정의
    ROS 패키지를 연동할 때 추가 작업이 필요하다.
- 조건부 대안: Isaac Sim 4.5
  - 최소 GPU가 RTX 3070 8GB라서 하드웨어 요구사항은 더 낮다.
  - Ubuntu 24.04와 Jazzy는 공식 조합이 아니며 Ubuntu 22.04와 ROS 2 Humble이
    권장된다. 필요할 경우 현재 환경을 바꾸지 않고 별도 운영체제나 별도 컴퓨터에서
    검토한다.

## 다음 세션 재개 방법

새 Codex 세션에서 저장소를 연 뒤 다음과 같이 요청한다.

```text
BACKLOG.md를 먼저 읽고, 미완료 작업부터 이어서 진행해줘.
기존 사용자 파일을 보존하고 완료한 항목은 체크해줘.
```

재개할 때 먼저 확인할 명령:

```bash
cd /home/junibecky/study_ros
git status --short --branch
```

이 저장소는 개인 학습 노트이므로 기본적으로 `main`에서 직접 작업하고 푸시한다.
별도 브랜치와 Pull Request는 사용자가 명시적으로 요청할 때만 사용한다.
