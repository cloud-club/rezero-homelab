# 홈랩 스터디 1주차

## 실습할 내용

1. ✅ Boot Media 만들기
2. ✅ OS가 이미 설치되어 있는 장치 / 설치 되어 있지 않은 장치에 우분투 설치하기
3. ✅ 환경 공유하기
    <details>
    <summary>방 네트워크 토폴로지</summary>
    <div markdown="1">

    <p align="center">
    <img src="./images/my_home_network.png" width="500">
    </p>

    IP는 보안상 모두 가렸음. 벽마다 외부 IP가 할당되어 있는 듯 함.

    </div>
    </details>

## 새롭게 배운 것

### Ubuntu 설치의 정석 [[참고]](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

- 기존에는 rufus를 사용해서 boot media를 만들었었는데, 공식 홈페이지에서는 Windows, macOS, Linux를 모두 지원하는 [balenaEtcher](https://etcher.balena.io/)의 사용을 권고하고 있음 (rufus는 Windows만 지원)
- rufus와 비교했을 때 balenaEthcher의 사용성이 더 좋아보임

<details>
<summary>rufus UI</summary>
<div markdown="1">

<p align="center">
  <img src="./images/rufus_ui.png" width="500">
</p>

~~솔직히 처음 봤을 때 정신이 아득해졌다~~

</div>
</details>

<details>
<summary>balenaEtcher UI</summary>
<div markdown="1">

<p align="center">
  <img src="./images/balenaetcher_ui.png" width="500">
</p>

</div>
</details>

### Ventoy [링크](https://www.ventoy.net/en/index.html)
- Ventoy를 사용하면 하나의 boot media에 여러 os image를 담아 설치할 때 선택할 수 있음
- MBR과 GPT 방식 모두 지원하는 특징이 있음

### USB3가 준비물이었던 이유
- 데이터 전송 속도가 빠르기 때문에 OS 부팅 시간이 단축됨
- 호환성 및 안정성이 좋아 최신 PC 대부분에서 인식 잘 됨
    - usb2 소켓에 usb3를 꽂으면 작동하지만 usb3 소켓에 usb2를 꽂으면..
- 대용량 OS 이미지도 빠르게 플래싱하고 읽을 수 있음, 설치 시간 절약 가능

## 문제 상황

### ✅ bios에는 진입했으나 ubuntu 설치 화면으로 넘어가지 않음
- Windows가 이미 설치되어 있는 삼성 노트북에서 bios까지는 진입에 성공하였으나 부팅 우선순위를 SSD에서 USB로 변경하여도 Windows로 연결되는 문제가 있었음
- Boot Loader를 Windows Boot Manager를 UEFI로 변경하여 해결
- [부트로더란?](http://www.ktword.co.kr/test/view/view.php?no=2658)

### ❓ pfsense 환경에서 모든 실습이 안정적으로 가능할 것인가?
- [pfsense](https://www.pfsense.org/)는 오픈소스 방화벽 소프트웨어로서 가상, 물리 관계없이 NIC가 2개 이상이라면 방화벽의 기능을 수행하게 해줌
- NAT, OpenVPN, DNS Resolver/Forwarder, Firewall Rules, VLAN, DHCP Server등의 기능이 있음
- 왠만한 외부의 네트워크 요청을 막기 때문에 꽤나 안전하게 느껴지지만 어지간한 요청을 다 막아버려서 곤란한 경우도 있음 ~~깡통 상태에서도 마인크래프트 멀티 서버 접속을 막음~~
- 앞으로의 실습에 있어 pfsense가 걸림돌이 될지도 모름 