---
categories:
    - Others
tags:
    - ubuntu
    - environment-setup
---

<head></head>

나는 좀 특이한 구성으로 듀얼 모니터 환경을 세팅해 놨다. 왼쪽에는 1920\*1080 해상도의 서브 모니터를 90도 회전시킨 다음 화면 맨 위쪽까지 쳐다보는 게 불편해서 위아래 일부를 잘라놓은 상태로 1080\*1440 해상도로 사용하고 있고, 오른쪽에는 2560\*1440 해상도의 메인 모니터를 그나마 평범하게 설치해서 사용하고 있다.

NVIDIA X Server를 잘 만져줘서 설정이 제대로 됐다고 생각하고 대충 잘 쓰고 있다가 재부팅을 해 보니 문제가 발생했다. 로그온 화면에서 메인 모니터가 왼쪽 모니터로 설정이 돼 있는지 왼쪽 모니터에 반대 방향으로 90도 돌아간 로그인화면이 떠 있고, 로그인을 하고 나니 메인 모니터는 제대로 잡혔지만 서브 모니터가 1080\*1920 사이즈로 화면을 꽉 채우고 있었다.

나중에 Ubuntu를 재설치하거나 다른 PC에 깔 때 삽질하지 않기 위해서 일단 써 둔다.

일단 GPU 드라이버는 설치됐다고 가정하고 글을 쓰겠다. 설치가 안 되어 있다면 <a href="https://pstudio411.tistory.com/entry/Ubuntu-2004-Nvidia%EB%93%9C%EB%9D%BC%EC%9D%B4%EB%B2%84-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0">이런 글</a>을 참고해서 설치해 주도록 하자.

1. NVIDIA X Server로 설정 변경

우선 터미널에 ```sudo nvidia-settings```를 쳐서 X Server를 실행시킨다. 듀얼 모니터의 해상도나 모니터 배치 같은 설정은 왼쪽 메뉴에서 **X Server Display Configuration**을 선택하면 볼 수 있다.

메인 모니터 설정은, 위쪽에서 메인 모니터로 설정할 모니터를 선택하고 **Make this the primary display for the X screen**을 체크해주면 된다. 모니터를 회전시켜서 사용하는 경우, **Orientation**의 설정을 바꿔주면 된다.

나처럼 모니터의 일부만 사용할 경우 **Advanced...** 뷰의 **ViewPortIn, ViewPortOut, Panning** 옵션을 사용해야 된다. 


2. 재부팅 / 다시 로그인 했을 때도 설정 유지

터미널에 ```sudo nvidia-settings```를 쳐서 ```xorg.conf``` 파일을 생성한다. 이후 ```xorg.conf``` 파일에서 **"Device"**로 시작하는 블럭을 찾은 후, 아래 내용을 블럭 끝에 붙여넣는다.


```
Option "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3322"
```

(출처: https://askubuntu.com/questions/379483/nvidia-x-server-settings-lost-on-every-reboot)


3. 로그인 전 화면에도 설정 적용

아래 명령어를 터미널에 입력하면 된다. gdm은 그래픽 로그인 화면을 관리하는 특수한 유저라고 생각하면 된다.

```
sudo cp ~/.config/monitors.xml ~gdm/.config/monitors.xml
sudo chown gdm:gdm ~gdm/.config/monitors.xml
```

왜인지는 모르겠지만 이 방법으로 해결했다는 다른 글들을 보면 한 번에 되지 않고 재부팅을 몇 번씩 해가면서 여러 번 시도해야 했다는 얘기가 있다.

(출처: https://askubuntu.com/questions/1043337/is-there-to-make-the-login-screen-appear-on-the-external-display-in-18-04)