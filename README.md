# ![header](https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=20&height=200&animation=twinkling&section=header&text=BeatBuddy&fontSize=80&fontAlign=75&fontAlignY=36)

# BeatBuddy - 음악 취향 기반 친목 커뮤니티 서비스

## 👀 목차
1. [👥 팀원](#-팀원)
2. [📚 프로젝트 개요](#-프로젝트-개요)
3. [📑 요구사항 분석](#-요구사항-분석)
4. [🔧 시스템 아키텍처](#-시스템-아키텍처)
5. [📅 요구사항 명세서](#-요구사항-명세서)
6. [🪧 ERD](#-erd)
7. [🗃️ 테이블 명세서](#%EF%B8%8F-테이블-명세서)
8. [🎯 API 명세서](#-api-명세서)
9. [🖥 화면 및 기능 설계서](#-화면-및-기능-설계서)
10. [🧪 테스트 계획 및 결과 보고서](#-테스트-계획-및-결과-보고서)
11. [🛠️ 기술 스택](#-기술-스택)
12. [📌 주요 기술적 의사결정](#-주요-기술적-의사결정)
13. [⚙️ CI/CD 구조 및 스크립트](#%EF%B8%8F-cicd-구조-및-스크립트)
14. [🚀 CI/CD 배포 결과](#-cicd-배포-결과)
15. [📽️ 주요 기능 시연 영상](#%EF%B8%8F-주요-기능-시연-영상)
16. [💬 회고록](#-회고록)

---

### 👥 팀원

<table>
  <tr align="center">
    <th>채팅(팀장)</th>
    <th>음악</th>
    <th>친구</th>
    <th>그룹</th>
  </tr>

  <tr>
    <td align="center"><img width="120" height="180" alt="김예지" src="./introduce/yeazi_1.png" /></td>
    <td align="center"><img width="120" height="180" alt="박하얀" src="./introduce/hayan.png" /></td>   
    <td align="center"><img width="120" height="180" alt="이다윗" src="./introduce/leedawit.png" /></td>   
    <td align="center"><img width="120" height="180" alt="황희수" src="./introduce/huisu.png" /></td>
  </tr>
  
  <tr align="center">
    <th>김예지</th>
    <th>박하얀</th>
    <th>이다윗</th>
    <th>황희수</th>
  </tr>
</table>

## 📌 프로젝트 개요

### 📘 프로젝트 소개

**BeatBuddy**는 소속 집단 구성원들의 음악적 취향 데이터를 분석하여 정서적 공감대가 높은 동료를 연결해 주는 팀 빌딩 지원 플랫폼입니다.

가입 시 최애곡 10곡을 선택하면, 곡의 음악적 특성을 분석하여 16차원 취향 벡터를 생성합니다. 같은 그룹에 속한 멤버들과 코사인 유사도를 계산해 취향이 비슷한 사람을 추천받고, 마음에 드는 상대에게 친구 신청을 보내 1:1 채팅으로 대화할 수 있습니다.

---

### ✅ 배경: 왜 이 서비스가 필요한가?

#### 취향 기반 연결의 필요성
기존 소셜 서비스는 외형이나 조건 중심의 매칭으로 인해 실제 깊이 있는 정서적 교감을 기대하기 어렵고, 이는 곧 대화의 단절과 관계 유지를 위한 심리적 피로감으로 이어집니다.

#### 음악이 가진 연결의 힘
음악 취향은 성격, 감성, 라이프스타일과 높은 상관관계를 가집니다. 같은 곡을 좋아한다는 사실만으로도 대화의 물꼬를 트기 쉬워집니다.

#### 그룹 기반 안전한 만남
그룹 안에서만 추천이 이루어지므로, 불특정 다수와의 무작위 연결이 아닌 신뢰할 수 있는 환경에서 친구를 사귈 수 있습니다.

---

## 📑 요구사항 분석

<details>
<summary> 요구사항 분석 </summary>

### 🎵 1. 음악 취향 분석
- 최애곡 10곡 선택 (Spotify API 연동)
- 곡별 음악 특성 수집 (SoundNet API)
- 16차원 취향 벡터 생성 및 저장
- 취향 프로필 조회 및 수정

### 👤 2. 사용자 기능
- 이메일 회원가입 / 로그인 (JWT)
- 이메일 인증 (Gmail SMTP)
- 비밀번호 찾기 / 변경
- 프로필 관리 및 회원탈퇴

### 👥 3. 그룹 기능
- 그룹 생성
- 초대 코드 기반 그룹 가입
- 그룹 내 취향 기반 친구 추천 (코사인 유사도)
- 추천 프로필 조회 (넘기기 / 친구 신청)

### 🤝 4. 친구 기능
- 친구 신청 / 수락 / 거절
- 친구 목록 조회 및 검색
- 친구 프로필 및 최애곡 확인
- 친구 삭제

### 💬 5. 채팅
- 1:1 실시간 채팅 (WebSocket)
- 채팅방 목록 및 안읽은 메시지 수 표시
- 채팅방 나가기

### 🔔 6. 알림
- 친구 신청 / 수락 알림

</details>

---

## 🔧 시스템 아키텍처

<details>
<summary> 시스템 아키텍처</summary>

<br>

> ![Web App Reference Architecture](https://github.com/user-attachments/assets/4f84192b-62fc-4ae6-897b-765a117cd097)

</details>

---

## 📋 요구사항 명세서
> [요구사항 명세서](https://docs.google.com/spreadsheets/d/1bW-t6EJQ1NW_uqkoiAgVqqeyeDuuh2muPwpv8ee4Y2s/edit?usp=sharing)

---

## 🪧 ERD
> [ERD](https://www.erdcloud.com/d/MEMRtro3g2PtxsnCE)

---

## 🗃️ 테이블 명세서
> [테이블 명세서](https://docs.google.com/spreadsheets/d/1bW-t6EJQ1NW_uqkoiAgVqqeyeDuuh2muPwpv8ee4Y2s/edit?usp=sharing)

---

## 🎯 API 명세서

> [API 명세서](https://www.notion.so/5-API-f76901cdc00882208183014b29afe442?source=copy_link)

---

## 🖥 화면 및 기능 설계서

> [화면 및 기능 설계서](https://www.figma.com/board/daSTynfA5bNxs7zU00zo6I/flow-chart?t=ePHmKATAdPWGXzb6-1)

<details>
<summary>회원 관리</summary>
<img width="4482" height="2642" alt="BeatBuddy 화면설계서 (1)" src="https://github.com/user-attachments/assets/c681f270-19f1-4081-8cd7-a404a28fc52d" />
</details>

<details>
<summary>그룹</summary>
<img width="4482" height="2794" alt="BeatBuddy 화면설계서 (2)" src="https://github.com/user-attachments/assets/272c93a9-c80b-44a8-b915-2b49d9bd7e37" />
</details>

<details>
<summary>음악</summary>
<img width="4490" height="3077" alt="BeatBuddy 화면설계서 (3)" src="https://github.com/user-attachments/assets/9010f5a6-956e-44a4-8c29-872238c08078" />
</details>

<details>
<summary>친구</summary>
<img width="3474" height="2650" alt="BeatBuddy 화면설계서 (4)" src="https://github.com/user-attachments/assets/f9d4605f-c5c7-464b-a614-2b55f7086f1f" />
</details>

<details>
<summary>채팅</summary>
<img width="3474" height="1411" alt="BeatBuddy 화면설계서 (5)" src="https://github.com/user-attachments/assets/aa5284f3-6278-4508-a853-e18171991d07" />
</details>

<details>
<summary>마이페이지</summary>
<img width="3474" height="4465" alt="BeatBuddy 화면설계서 (6)" src="https://github.com/user-attachments/assets/a9fbde85-5a8f-4237-bc21-8a0594b51ea1" />
</details>

---

## 🧪 테스트 계획 및 결과 보고서

> 백엔드 - [테스트 계획 및 결과 보고서](https://docs.google.com/spreadsheets/d/1_yQBYho9SeX9E9EfWcyGfwN5yh79QyOxMhvVj6B-Qds/edit?gid=908489767#gid=908489767)
>
> 프론트엔드 - [테스트 계획 및 결과 보고서](https://docs.google.com/spreadsheets/d/1_pKygK3_dZ3CGeiM8Y9sOOe0t-kFvco2/edit?gid=424294998#gid=424294998)

---

## 🛠️ 기술 스택

<details>
<summary> 기술 스택</summary>

<br>

| 구분 | 기술 |
|------|------|
| Frontend | ![Vue.js](https://img.shields.io/badge/Vue.js-4FC08D?style=for-the-badge&logo=vuedotjs&logoColor=white) |
| Backend | ![SpringBoot](https://img.shields.io/badge/SpringBoot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white) |
| Database | ![MariaDB](https://img.shields.io/badge/MariaDB(MySQL)-003545?style=for-the-badge&logo=mariadb&logoColor=white) |
| ORM | ![MyBatis](https://img.shields.io/badge/MyBatis-000000?style=for-the-badge) |
| 인증 | ![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white) |
| 이메일 | ![Gmail](https://img.shields.io/badge/GmailSMTP-EA4335?style=for-the-badge&logo=gmail&logoColor=white) |
| 실시간 채팅 | ![WebSocket](https://img.shields.io/badge/WebSocket(STOMP)-010101?style=for-the-badge) |
| 외부 API | ![Spotify](https://img.shields.io/badge/SpotifyAPI-1DB954?style=for-the-badge&logo=spotify&logoColor=white)&nbsp;![RapidAPI](https://img.shields.io/badge/RapidAPI-0055DA?style=for-the-badge&logo=rapid&logoColor=white) |
| Infra/DevOps | ![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)&nbsp;![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)&nbsp;![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=for-the-badge&logo=jenkins&logoColor=white)&nbsp;![Docker Hub](https://img.shields.io/badge/Docker%20Hub-0db7ed?style=for-the-badge&logo=docker&logoColor=white)&nbsp;<img src="https://img.shields.io/badge/Argo%20CD-FE6A16?style=for-the-badge&logo=argo&logoColor=white">&nbsp;<img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github"> |

</details>

---

## 📌 주요 기술적 의사결정

<details>
<summary> 주요 기술적 의사결정 </summary>

#### 취향 벡터 설계
단순 평균이 아닌 평균 + 표준편차를 함께 저장하는 16차원 벡터를 설계했습니다. 표준편차를 포함함으로써 "취향의 폭"까지 반영할 수 있어 매칭 정확도를 높였습니다.

#### viewed_profiles 설계
Redis 대신 DB 테이블로 구현하되 `ON DUPLICATE KEY UPDATE`를 활용해 넘긴 프로필을 30일 후 재노출하는 로직을 구현했습니다. MVP 이후 Redis로의 교체를 고려한 구조입니다.

#### 채팅방 중복 방지
`user_a_id < user_b_id` CHECK 제약 조건과 UNIQUE KEY를 조합해 두 사용자 간 채팅방이 중복 생성되는 것을 DB 레벨에서 원천 차단했습니다.

</details>

---

## ⚙️ CI/CD 구조 및 스크립트
<details>
<summary>아키텍처</summary>
  <img width="4988" height="3084" alt="beatbuddy-service-architecture (4)" src="https://github.com/user-attachments/assets/b9b16887-47bf-429e-a367-9ca11b20bcc3" />
</details>

<details>
<summary>빌드 구성</summary>
  <img width="4804" height="2604" alt="beatbuddy-build-pipeline (1) (1)" src="https://github.com/user-attachments/assets/62d63a60-d910-4076-a987-ad47390bba84" />
</details>

<details>
  <summary>Jenkins Pipline</summary>
  -------------------
<details>
  <summary>backend</summary>

```groovy
pipeline {
    agent {
        kubernetes {
            yaml '''
            apiVersion: v1
            kind: Pod
            metadata:
              name: jenkins-agent
            spec:
              containers:
              - name: docker
                image: docker:29.4.1-cli-alpine3.23
                command:
                - cat
                tty: true
                volumeMounts:
                - mountPath: "/var/run/docker.sock"
                  name: docker-socket
              volumes:
              - name: docker-socket
                hostPath:
                  path: "/var/run/docker.sock"
            '''
        }
    }

    environment {
        DOCKER_IMAGE_NAME = "huisuz/beatbuddy-backend"
        DOCKER_CREDENTIALS_ID = "dockerhub-access"
    }

    stages {
        stage('Docker Image Build & Push') {
            steps {
                container('docker') {
                    script {
                        def buildNumber = "${env.BUILD_NUMBER}"

                        sh 'docker logout'

                        withCredentials([usernamePassword(
                            credentialsId: DOCKER_CREDENTIALS_ID,
                            usernameVariable: 'DOCKER_USERNAME',
                            passwordVariable: 'DOCKER_PASSWORD'
                        )]) {
                            sh 'echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin'
                        }

                        withEnv(["DOCKER_IMAGE_VERSION=${buildNumber}"]) {
                            sh 'docker build --no-cache -t $DOCKER_IMAGE_NAME:$DOCKER_IMAGE_VERSION ./'
                            sh 'docker push $DOCKER_IMAGE_NAME:$DOCKER_IMAGE_VERSION'
                        }
                    }
                }
            }
        }

        stage('Trigger beatbuddy-k8s-manifests') {
            steps {
                script {
                    def buildNumber = "${env.BUILD_NUMBER}"
                    withEnv(["DOCKER_IMAGE_VERSION=${buildNumber}"]) {
                        build job: 'beatbuddy-k8s-manifests',
                            parameters: [
                                string(name: 'DOCKER_IMAGE_VERSION', value: "${DOCKER_IMAGE_VERSION}")
                            ],
                            wait: true
                    }
                }
            }
        }
    }
}
```

</details>
    
<details>
  <summary>frontend</summary>
  
```groovy
pipeline {
    agent {
        kubernetes {
            yaml '''
            apiVersion: v1
            kind: Pod
            metadata:
              name: jenkins-agent
            spec:
              containers:
              - name: docker
                image: docker:29.4.1-cli-alpine3.23
                command:
                - cat
                tty: true
                volumeMounts:
                - mountPath: "/var/run/docker.sock"
                  name: docker-socket
              volumes:
              - name: docker-socket
                hostPath:
                  path: "/var/run/docker.sock"
            '''
        }
    }

    environment {
        DOCKER_IMAGE_NAME = "huisuz/beatbuddy-frontend"
        DOCKER_CREDENTIALS_ID = "dockerhub-access"
    }

    stages {
        stage('Docker Image Build & Push') {
            steps {
                container('docker') {
                    script {
                        def buildNumber = "${env.BUILD_NUMBER}"
                        sh 'docker logout'
                        withCredentials([usernamePassword(
                            credentialsId: DOCKER_CREDENTIALS_ID,
                            usernameVariable: 'DOCKER_USERNAME',
                            passwordVariable: 'DOCKER_PASSWORD'
                        )]) {
                            sh 'echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin'
                        }
                        withEnv(["DOCKER_IMAGE_VERSION=${buildNumber}"]) {
                            sh 'docker build --no-cache -t $DOCKER_IMAGE_NAME:$DOCKER_IMAGE_VERSION ./'
                            sh 'docker push $DOCKER_IMAGE_NAME:$DOCKER_IMAGE_VERSION'
                        }
                    }
                }
            }
        }

        stage('Trigger beatbuddy-k8s-manifests') {
            steps {
                script {
                    def buildNumber = "${env.BUILD_NUMBER}"
                    withEnv(["DOCKER_IMAGE_VERSION=${buildNumber}"]) {
                        build job: 'beatbuddy-k8s-manifests',
                            parameters: [
                                string(name: 'DOCKER_IMAGE_VERSION', value: "${DOCKER_IMAGE_VERSION}"),
                                string(name: 'SERVICE', value: 'frontend')
                            ],
                            wait: true
                    }
                }
            }
        }
    }
}
```

</details>

<details>
  <summary>k8s</summary>

```groovy
pipeline {
    agent any
    parameters {
        string(name: 'DOCKER_IMAGE_VERSION', defaultValue: '', description: 'Docker Image Version')
        choice(name: 'SERVICE', choices: ['backend', 'frontend'], description: 'Service to update')
    }
    stages {
        stage('Update deploy.yaml') {
            steps {
                dir("${params.SERVICE}") {
                    sh 'git checkout main'
                    sh "sed -i 's|huisuz/beatbuddy-${params.SERVICE}:.*|huisuz/beatbuddy-${params.SERVICE}:${params.DOCKER_IMAGE_VERSION}|g' deploy.yaml"
                    sh 'cat deploy.yaml'
                }
            }
        }
        stage('Commit & Push') {
            steps {
                sh 'git config user.name "jenkins"'
                sh 'git config user.email "jenkins@beatbuddy.com"'
                sh 'git add .'
                sh "git commit -m 'Update ${params.SERVICE} image to ${params.DOCKER_IMAGE_VERSION}'"
                sshagent(['github-beatbuddy-k8s']) {
                    sh '''
                        mkdir -p ~/.ssh
                        ssh-keyscan github.com >> ~/.ssh/known_hosts
                        git remote set-url origin git@github.com:huisu73/beatbuddy-k8s.git
                        git push origin main
                    '''
                }
            }
        }
    }
}
```

</details>
</details>

---

## 🚀 CI/CD 배포 결과

<details>
  <summary>BACKEND CI/CD</summary>

  https://github.com/user-attachments/assets/c7914280-0a82-4a04-8f20-cd8c6a1fd62b
</details>

<details>
  <summary>FRONTEND CI/CD</summary>

  https://github.com/user-attachments/assets/2b549b54-6434-4f0b-929f-11991a0fa4dc
</details>

---

## 📽️ 주요 기능 시연 영상

> [주요 기능 시연 영상](https://github.com/user-attachments/assets/db7087dd-5fd0-4903-8be5-49fc0aee5cd4)

---

### 💬 회고록

#### 김예지
> 이번 프로젝트에서는 CI/CD 파이프라인을 직접 구축하며 단순한 배포 자동화를 넘어, 실제 운영 환경에서 고려해야 하는 요소들을 경험할 수 있었습니다. GitHub Webhook → Jenkins → Docker Hub → ArgoCD → Kubernetes로 이어지는 전체 흐름을 직접 구성하면서 각 도구의 역할과 연결 구조를 이해할 수 있었고, 서비스 배포가 단순 실행이 아닌 여러 시스템이 유기적으로 동작하는 과정이라는 점을 체감했습니다. 또한 GitOps 방식으로 배포 상태를 Git 저장소에서 관리해보며, 인프라 변경 이력을 코드 기반으로 추적하고 관리할 수 있다는 점에서 유지보수성과 운영 안정성 측면의 장점을 배울 수 있었습니다.
 채팅 서버를 Replica 2개로 확장했을 때 사용자가 서로 다른 Pod에 연결될 경우 WebSocket 세션 정보가 분리되어 메시지 동기화가 이루어지지 않아, 새로고침 이후에야 메시지가 조회되는 문제가 발생했습니다. 이를 통해 수평 확장 환경에서는 Pod 간 메시지 이벤트를 공유할 수 있는 구조가 반드시 필요하다는 점을 배울 수 있었습니다. 향후에는 Kafka 또는 Redis Pub/Sub 기반의 메시지 브로커를 도입하여 분산 환경에서도 안정적인 실시간 통신 구조를 구현해보고자 합니다.

#### 박하얀
> 이번 프로젝트에서는 Jenkins와 Kubernetes를 활용해 코드 변경부터 배포까지 이어지는 CI/CD 파이프라인을 직접 구축하고 운영해볼 수 있었습니다. GitHub와 Jenkins를 연동해 빌드 및 배포 과정을 자동화하면서, 수동 배포에 비해 훨씬 효율적이고 안정적으로 서비스를 운영할 수 있다는 점을 경험할 수 있었습니다. 하지만 익숙하지 않은 DevOps 환경으로 인해 초기에는 배포 과정 자체가 어렵고 복잡하게 느껴졌습니다. 특히 Jenkins Pipeline 실행 과정에서 발생하는 오류나 Kubernetes Pod가 정상적으로 실행되지 않는 문제의 원인을 찾는 과정이 쉽지 않았지만, 로그를 확인하고 문제를 하나씩 해결해가며 전체 흐름을 점차 이해할 수 있었습니다. 또한 Docker를 활용한 실행 환경 통일과 Kubernetes 기반 배포 과정을 직접 경험하면서, 단순히 코드를 작성하는 것에서 끝나는 것이 아니라 안정적으로 서비스가 실행될 수 있는 환경을 구성하는 과정 역시 중요하다는 점을 배울 수 있었습니다. 이번 프로젝트를 통해 개발뿐 아니라 배포와 운영의 중요성까지 경험할 수 있었으며, DevOps 환경이 실제 프로젝트에서 어떻게 활용되는지 이해할 수 있었던 의미 있는 시간이었습니다.

#### 이다윗
> 이번 프로젝트에서 Jenkins와 ArgoCD를 활용해 코드 푸시부터 배포까지 전 과정을 자동화했습니다. 덕분에 수동 배포의 번거로움을 없애고 개발에만 집중할 수 있는 환경을 만들었습니다. 특히 로컬 DB 자료를 쿠버네티스 MariaDB(StatefulSet)로 안전하게 옮기고, 서버가 재시작되어도 데이터가 유지되도록 저장소를 연결하도록 했습니다. 배포 후 로컬에서는 잘 되던 기능들이 서버 환경에서 작동하지 않는 시행착오도 겪었지만, Ingress 설정과 네트워크 경로를 하나하나 대조하며 설정을 맞춘 끝에 문제를 해결했습니다. 이 과정을 통해 개발 환경과 운영 인프라의 차이를 깊이 이해하게 되었고, 프로젝트의 안정성을 한 단계 높이는 성과를 얻었습니다.

#### 황희수
> 이번 프로젝트에서 처음으로 GitOps 기반 CI/CD 파이프라인을 구축했습니다. 단순히 서비스를 올리는 것에 그치지 않고 코드 push 한 번으로 빌드부터 배포까지 자동화되는 구조를 만드는 것을 목표로 했습니다. 초반에는 application.yml의 순환 참조, CSRF 설정 문제 등 예상치 못한 트러블이 많았습니다. 배포 후에도 Ingress 라우팅 문제, WebSocket 실시간 수신 불가 등 다양한 문제가 발생하면서 코드 작성과 실제 운영 환경은 전혀 다르다는 것을 체감했습니다. 아쉬운 점은 백엔드 Pod를 2개 이상 운영할 때 In-Memory Broker 한계로 채팅 실시간 수신이 안 되는 문제를 Redis Pub/Sub으로 완전히 해결하지 못한 것입니다.이는 추후 개선 과제로 남겨두었으며, 이번 경험을 통해 인프라 구성과 운영에 대한 이해를 높일 수 있었던 경험이었습니다.

![footer](https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=20&height=100&section=footer)
