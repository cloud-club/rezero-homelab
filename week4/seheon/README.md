# 들어가며

---

## 학습 목표

### 홈서버 활용 계획

- 왜 굳이 PCIe를 사용할까? USB로도 가능한데.
    - PCIe는 메모리에 직접 접근(DMA)이 가능
    - 전송 오버헤드가 USB보다 적음
    - 대역폭이 훨씬 넓고, 지연도 낮기 때문에 고속 데이터 전송에 적합
        - USB 3.0 기준 약 5Gbps vs PCIe 3.0 x1은 약 8Gbps (x4면 32Gbps)

### 관련 용어

- **하드 디스크 케이스**: 채굴용 / 외장 HDD용 중고 부품 활용
- **기존 PC 케이스 재활용**: 옛날 케이스 + 메인보드 + 램 조합으로 NAS 전용 머신 구성
- **SATA 포트 많을수록 유리**: 멀티베이 구성 고려
- **TrueNAS Scale (리눅스 기반)**
    - Docker/Kubernetes 지원 → n8n, Tailscale도 같이 운영 가능
- Synology (DSM)
    - 완성도 높고 안정적이지만 **자체 OS / 하드웨어 종속성** 있음
    - Xpenology(비공식)도 가능하긴 하나, 유지보수 불안정
- **Runtipi**: 셀프호스팅 앱스토어 (ex. n8n, Vaultwarden 등 자동화/보안 앱 설치)
- **n8n**: 워크플로우 자동화
- **PhotoSync**: 이미지 자동 전송
- **Google Pixel 서버 컨셉**: 무제한 구글 포토 업로드용

### 아이디어

- **MacOS + Windows 듀얼 환경 운영**
    - 단일 PC에서 그래픽카드 파티션 나눠서 두 OS 운용
- **사진 백업 자동화**
    - `Tailscale`로 모바일 → 서버 이미지 실시간 전송
    - `PhotoSync` 사용 (핸드폰 ↔ Windows 서버)
    - Windows VM에서 **"구글 픽셀 서버"** 역할
        - 수신된 이미지 실시간 폴더 동기화
        - Google Photos 무제한 업로드 자동화
        - Google Pixel 이용
- **NAS 서버로 사용**
- **광고 차단 시스템 구축**
    - Pi-hole: 네트워크 전체 광고 차단
- **노드/서비스 모니터링 및 경고 시스템**
    - 노드 상태 모니터링 도구 연결
    - 라즈베리파이에 부저 연결 → 장애 발생 시 알림음 송출

### 참고 자료/채널

- **YouTube**
    - Hardware Haven
    - Techno Tim
    - NetworkChuck
    - Christian Lempa
    - 베테우스
    - tinyrack
- **커뮤니티**
    - 서버포럼(달쏘)
    - Reddit: [r/homelab](https://www.reddit.com/r/homelab)
