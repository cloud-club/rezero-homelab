# 클라우드 클럽 7기 스터디 - RE:Zero부터 시작하는 HomeLab 생활

## 1. Introduction

> [!NOTE]
>
> ### 스터디 소개
>
> 홈서버를 직접 구축하고 운영하고 싶은 사람들을 위한 스터디입니다.

---

<br>

### 🕑 Schedule & Members

- **기간**: 2025.03 ~ 2025.05 (8회)
- **시간**: 매주 일요일 (1군) 오후 12시 ~ 3시 (2군) 오후 3시 ~ 6시
- **장소**: 서초 부근 어딘가 (오프라인)
- **PR 제출 마감**: 스터디 1일 전 **토요일 오후 12:00**까지

<br>

### Who need this study?

- 홈서버를 운영하고 싶은 사람
- 클라우드 도움없이 a~z까지 직접 구축하고 싶은 사람
- 리눅스, 네트워크, 가상화 등에 관심이 많은 사람

> [!IMPORTANT]
>
> **이 스터디를 신청하기 전 알아두세요**
>
> - 엔지니어링을 위한

---

<br>

## 2. 👽 Our Squad

<table>
  <tr>
    <td align="center"><a href="https://github.com/yureutaejin"><img src="https://avatars.githubusercontent.com/u/85734054?v=4" width="100px;" alt=""/><br /><sub><b>
진윤태</b></sub></a><br /></td>
    <td align="center"><a href="https://github.com/Cybecho"><img src="https://avatars.githubusercontent.com/u/42949995?v=4" width="100px;" alt=""/><br /><sub><b>
소병욱</b></sub></a><br /></td>
    <td align="center"><a href="https://github.com/window9u"><img src="https://avatars.githubusercontent.com/u/121847433?v=4" width="100px;" alt=""/><br /><sub><b>문찬규</b></sub></a><br /></td>
    <td align="center"><a href="https://github.com/charlie3965"><img src="https://avatars.githubusercontent.com/u/19777578?v=4" width="100px;" alt=""/><br /><sub><b>
박천수</b></sub></a><br /></td>
    <td align="center"><a href="https://github.com/seoyeon0201"><img src="https://avatars.githubusercontent.com/u/125520029?v=4" width="100px;" alt=""/><br /><sub><b>
박서연</b></sub></a><br /></td>
    <td align="center"><a href="https://github.com/tmddus2"><img src="https://avatars.githubusercontent.com/u/49530253?v=4" width="100px;" alt=""/><br /><sub><b>
이승연</b></sub></a><br /></td>
  </tr>
  <tr>
    <td align="center"><a href="https://github.com/pinetree2"><img src="https://avatars.githubusercontent.com/u/79689822?v=4" width="100px;" alt=""/><br /><sub><b>
이해송</b></sub></a><br /></td>
    <td align="center"><a href="https://github.com/KimMinWoooo"><img src="https://avatars.githubusercontent.com/u/122437698?v=4" width="100px;" alt=""/><br /><sub><b>
김민우</b></sub></a><br /></td>
    <td align="center"><a href="https://github.com/yucori"><img src="https://avatars.githubusercontent.com/u/110710238?v=4" width="100px;" alt=""/><br /><sub><b>
장지원</b></sub></a><br /></td>
    <td align="center"><a href="https://github.com/hong-sile"><img src="https://avatars.githubusercontent.com/u/32128848?v=4" width="100px;" alt=""/><br /><sub><b>
홍혁준</b></sub></a><br /></td>
    <td align="center"><a href="https://github.com/seheonnn"><img src="https://avatars.githubusercontent.com/u/101795921?v=4" width="100px;" alt=""/><br /><sub><b>
호세헌</b></sub></a><br /></td>
    <td align="center"><a href="https://github.com/mjttong"><img src="https://avatars.githubusercontent.com/u/145860909?v=4" width="100px;" alt=""/><br /><sub><b>
권민정</b></sub></a><br /></td>
  </tr>
</table>

<br>

## 3. ⛳ Curriculum (Season - 1)

### Season 1 : 25.03.02 ~ 25.05.05

커리쿨럼은 매주 달라집니다. 당일에 모여 1) 목표를 정하고 2) 계획을 세우고 3) 진행하고 4) 정리합니다.

<br>

---

## 4. GitHub Collaboration Guidelines

> [!TIP]
> PR 및 Commenting on PR 예시는 이 [PR](https://github.com/yureutaejin/homelab-pg-monitoring/pull/1)을 참고해주세요

개인 GitHub Repository를 사용하고, 본 Repo는 아카이빙 용도로 사용합니다.
각자의 GitHub Project로 Issue를 생성하고 Issue에 대한 PR을 만든 후, 해당 PR 링크 및 요약을 본 Repo에 PR로 제출합니다.

@yureutaejin과 @Cybecho는 PR을 리뷰하고 comment를 남깁니다. 완전히 논의가 끝난 경우 Merge를 리뷰어가 승인합니다.

### a. 디렉토리 구조

사이트 목차를 기반으로 디렉토리 구조를 구성합니다:

```
root
├── README.md
├── week1
│   ├── yuntae
│   │   ├── README.md
│   │   └── ...
├── week2
│   ├── yuntae
│   │   ├── README.md
│   │   └── ...
```

### b. 브랜치 규칙

- 브랜치명: `ZHLAB-{이름 대문자}/week{주차}`
- 예시: `ZHLAB-YUNTAE/week1`

### c. PR(Pull Request) 규칙

> [!TIP]
> 간략하게 써주시고 자세한 내용은 ./week[n]/[user]/README.md에 작성해주세요.
> 리뷰어에게 README.md에 대한 부가적인 설명/질문이 필요하다면 이 [docs](https://docs.github.com/ko/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/commenting-on-a-pull-request)를 참고하여 comment를 남겨주세요

- PR 제목: `[ZHLAB-YUNTAE] - week1` 형식으로 작성
- PR 내용은 아래에 따라 작성:

  ```markdown
  # Description

  여기에 개인 Repo PR 링크를 붙여 놓고 간단히 무엇을 어떻게 진행했는지 리스트 3줄로 써주시면 됩니다.  
  질문/부가 설명은 comment on pr로 남겨주세요.

  ## Question

  PR comment 외에 추가적으로 요약가능한 질문
  ```

## 5. Reference

- [HomeLab SubReddit](https://www.reddit.com/r/homelab/)
- [SelfHosted SubReddit](https://www.reddit.com/r/selfhosted/)
- [Jeff Geerling](https://www.youtube.com/c/JeffGeerling)

> [!WARNING]
>
> **출석 규정**
>
> 3회 이상 불참 시 7기를 수료할 수 없습니다.  
> 각 스터디 모임에 참여하지 못할 경우, 사전에 Slack으로 사유를 작성해주세요
