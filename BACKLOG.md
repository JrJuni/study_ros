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
- 원격 저장소는 `main` 브랜치이며 최초 커밋 상태다.
- 프로젝트 로컬 스킬 골격을 다음 위치에 초기화했다.
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
- 위 버전 조합은 학생 컴퓨터 사양을 확인한 뒤 최종 확정한다는 주의사항
- Codex `bwrap`/AppArmor 오류의 원인과 해결 과정

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

`.agents/skills/update-ros-lessons/`는 초기화 도구가 만든 미완성 골격이므로
삭제하지 말고 내용을 완성해야 한다.
