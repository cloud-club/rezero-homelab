## 이전 시간 접속 문제

처음에는 operation timed out, permission denied가 나왔었는데

나중에 재접속 했을 때에 위처럼 `remote host key has changed, port forwarding is disabled` 떴음

- 키 정보 변경된 것이 반영이 안 되어서 재설정함

```jsx
ssh-keygen -R jiwon-homelab
```

하고 재접속 시도

- 근데 아직 디바이스 ACL 쪽에서 권한이 잘 부여되지 않았음
- 최종 ACL
    
    ```jsx
    // Example/default ACLs for unrestricted connections.
    {
    	// Declare static groups of users. Use autogroups for all users or users with a specific role.
    	"groups": {
    		"group:admin": ["kooriangman@gmail.com", "sarahlee0110@gmail.com"],
    	},
    
    	// Define the tags which can be applied to devices and by which users.
    	"tagOwners": {
    		"tag:admin":    ["kooriangman@gmail.com"],
    		"tag:home-lab": ["kooriangman@gmail.com"],
    	},
    
    	// Define access control lists for users, groups, autogroups, tags,
    	// Tailscale IP addresses, and subnet ranges.
    	"acls": [
    		// Allow all connections.
    		// Comment this section out if you want to define specific restrictions.
    		//{"action": "accept", "src": ["group:admin"], "dst": ["tag:home-lab:*"]},
    
    		{"action": "accept", "src": ["group:admin"], "dst": ["tag:home-lab:*"]},
    
    		// Allow users in "group:example" to access "tag:example", but only from
    		// devices that are running macOS and have enabled Tailscale client auto-updating.
    		// {"action": "accept", "src": ["group:example"], "dst": ["tag:example:*"], "srcPosture":["posture:autoUpdateMac"]},
    	],
    
    	// Define postures that will be applied to all rules without any specific
    	// srcPosture definition.
    	// "defaultSrcPosture": [
    	//      "posture:anyMac",
    	// ],
    
    	// Define device posture rules requiring devices to meet
    	// certain criteria to access parts of your system.
    	// "postures": {
    	//      // Require devices running macOS, a stable Tailscale
    	//      // version and auto update enabled for Tailscale.
    	// 	"posture:autoUpdateMac": [
    	// 	    "node:os == 'macos'",
    	// 	    "node:tsReleaseTrack == 'stable'",
    	// 	    "node:tsAutoUpdate",
    	// 	],
    	//      // Require devices running macOS and a stable
    	//      // Tailscale version.
    	// 	"posture:anyMac": [
    	// 	    "node:os == 'macos'",
    	// 	    "node:tsReleaseTrack == 'stable'",
    	// 	],
    	// },
    
    	// Define users and devices that can use Tailscale SSH.
    	"ssh": [
    		// Allow all users to SSH into their own devices in check mode.
    		// Comment this section out if you want to define specific restrictions.
    		{
    			"action": "check",
    			"src":    ["autogroup:member"],
    			"dst":    ["autogroup:self"],
    			"users":  ["autogroup:nonroot", "root"],
    		},
    		{
    			"action":      "check",
    			"src":         ["group:admin"],
    			"dst":         ["tag:home-lab"],
    			"users":       ["autogroup:nonroot", "root"],
    			"checkPeriod": "3h",
    		},
    	],
    
    	// Test access rules every time they're saved.
    	// "tests": [
    	//  	{
    	//  		"src": "alice@example.com",
    	//  		"accept": ["tag:example"],
    	//  		"deny": ["100.101.102.103:443"],
    	//  	},
    	// ],
    }
    
    ```
    

원인 : group:admin의 ssh 접근을 허용하지 않았어서 주석 해제해주니 접속 잘 됨

## 서버 태그 붙여서 연결

```bash
sudo tailscale up --advertise-exit-node --ssh --advertise-tags=tag:home-lab
```

## crontab 설정

서버가 상태가 좋지 않아서.. 일단은 매일 0시 0분에 리부팅 되도록 세팅했다

```bash
# 전체 cron 파일 설정
vi /etc/crontab
# 정각에 너무 칼 같이 하면 작업하다가 까먹을까봐.. 5분 유예 줌. 그리 의미 있는 지는 잘?
0 0 * * * root /bin/sleep 300 && /sbin/shutdown -r now
```

## 노트북 딱딱 소리 문제

예상 원인

1. 하드디스크 쪽 문제
2. 쿨링 팬 쪽 문제 → 근데 이건 주요 원인이라기 보다는 냄새의 원인일듯.. 꿉꿉한 냄새가 난다
3. 오디오 문제

일단 냄새도 해결해야 해서.. 간단하게 하단 분리 후 청소하기로 결정

급하게 일단 다이소에서 드라이버 사옴

나사 뽑고 카드로 쑤셔서 케이스 뜯는데 너무 힘들었다… 근데 삽질하느라 한 번 더 뜯으니까 약간 요령이 생김(?)

[IMG_3331.pdf](https://github.com/user-attachments/files/19401329/IMG_3331.pdf)

케이스 안 쪽 면이 이렇게 그을린 것 같이 되어 있는데 실제로 타서 이런 건지는 모르겠다 근데 그렇다기엔 스티커는 또 깨끗하고 뭐지

→ 배터리 쪽이 생각보다 깨끗한 걸로 봐서는 디자인적 요소 + 새월의 풍파가 원인이 아닐까 싶다.

[IMG_3332.pdf](https://github.com/user-attachments/files/19401327/IMG_3332.pdf)

[IMG_3333.pdf](https://github.com/user-attachments/files/19401331/IMG_3333.pdf)

생각보다 보드 쪽은 멀쩡하게 보인다.

스피커 쪽 문제인가 싶었지만 외관상으로는 찢어진 부분도 없고 괜찮다 

→ 근데 사실 나중에 듣다 보니 오른쪽 스피커 부분에서 딱딱 소리가 나는 것 같기도 하다

[IMG_3334.pdf](https://github.com/user-attachments/files/19401328/IMG_3334.pdf)

구동 시 꿉꿉한 냄새도 문제였기에 가생이에 오염 부분들을 닦고 쿨러 쪽도 최대한 청소했다.

[IMG_3335.pdf](https://github.com/user-attachments/files/19401330/IMG_3335.pdf)

나사 풀어서 최대한 먼지만 제거하고 재조립했다

배터리 아래에 혹시 탄 부분 있을까봐 나사를 풀었었는데

저 PUSH라고 적혀있는 부분을 어떻게 분해하는지 몰라서 일단 냅뒀다

살짝 들어서 최대한 봤을 때에는 탄 흔적 같은건 없긴 했다.


[IMG_3336.pdf](https://github.com/user-attachments/files/19401326/IMG_3336.pdf)

분해의 역순으로 조립하고 나니 전원은 정상적으로 작동했다.

근데 케이스 뜯으면 컴퓨터가 인지를 하는지 평소와는 약간 다른 과정으로 부팅하던데

이를 컴퓨터가 따로 인지하는 버튼? 같은 것이 있는 건지 궁금하다.

뭐 딱히 내부 부품에서 나사를 건들지 않아도 평소와는 다르게 부팅했다.

# 앞으로의 방향성

## 목표 : 프로젝트 서비스들 띄우고 CI/CD 환경 구축하기

### 이를 위해 해야할 일

1. 우선 서비스를 적합하게 띄워야 함
    1. 컨테이너로  띄우면 되려나?
2. CI/CD 서비스 구축
    1. 서비스 정하기
        1. 간단하게 해 본 github action을 제대로 써볼지 or 처음 써보는 jenkins를 시도해볼지
        2. cd는 argoCD로? 근데 jenkins로 cd 까지도 가능하기는 한다는데 뭐가 더 나을까?
            1. ~~사실 취업때 어필하기 좋은 서비스로 택하고 싶다~~
        3. 소나큐브
3. 네트워크 설정(ACL, LB)
    1. 어느 ip, 포트를 허용할 것이고 어디로 포트 포워딩 할 것인지 정해야 함
    2. LB로 외부 ip 접근 설정하고, ACL로 내부 보안 설정하면 되려나

### 추가 적으로 하고 싶은 것

1. 로드 밸런싱 설정
    1. nginx 이용하면 간단하게 할 수 있긴 한데 좀 더 활용을 하고 싶다. 단순 포워딩, 부하 분산은 기능을 너무 적게 활용하는 것 같음
2. 방화벽 설정
    1. 보안이 약간 헷갈리는데 lb 설정하면서 액세스 설정 하는 것 만으로도 충분하련지.. 방화벽을 따로 설정해야 하는 것 같은데