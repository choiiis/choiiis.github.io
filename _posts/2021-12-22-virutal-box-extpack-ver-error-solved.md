---
title: "VBoxExtPackRegister returned VERR_VERSION_MISMATCH Solution 확장팩 설치 에러 해결 방법"
excerpt: "VM virtualbox extension pack version error solved"

categories:
  - Linux
tags:
  - [VirtualBox]

permalink: /virtual-box/extpack-ver-error-solved/

toc: true
toc_sticky: true
 
date: 2021-12-22
last_modified_at: 2021-12-22
---

Virtual Box를 사용하기 위해서 Extension Pack을 설치해야 하는 경우가 많다.<br>
이때 버추얼 박스와 이 확장팩 간의 버전이 맞지 않으면 오류가 발생한다.<br>
이 오류를 해결하는 방법에 대해서 알아보자.

---

## VirtualBox 확장팩 Extension Pack 설치 오류 해결 방법

### 확장팩 설치 오류 발생

<img src="/assets/images/posts_img/virtual-box-extpack-ver-error-solved/error_msg.jpg" alt="error_msg" width="70%">

**Oracle_VM_VirtualBox_Extension_Pack-6.1.30.vbox-extpack을 설치할 수 없습니다.**<br>
VirtualBox의 Extension Pack을 설치하다가 이런 오류를 만났다.

<img src="/assets/images/posts_img/virtual-box-extpack-ver-error-solved/error_detail.jpg" alt="error_detail" width="70%">

자세한 정보 버튼을 클릭해보니,<br>
VBoxExtPackRegister returned VERR_VERSION_MISMATCH 라는 에러 메세지가 나왔다.<br>
쭉 읽어보면 `VERR_VERSION_MISMATCH`, `ErrInfo='Helper version mismatch'` ... <br>
대충 봐도 뭔가 버전이 맞지 않다는 뜻이다.

<br>

### VirtualBox 버전 확인하기

<img src="/assets/images/posts_img/virtual-box-extpack-ver-error-solved/version_config.jpg" alt="version_config" width="70%">

내 PC의 VirtualBox 버전이 무엇인지 확인을 해보자<br>
VirtualBox의 버전을 확인하기 위해서 `도움말 > VirtualBox 정보`를 클릭한다.

<img src="/assets/images/posts_img/virtual-box-extpack-ver-error-solved/version_check.jpg" alt="version_check" width="70%">

내 VirtualBox는 6.1 버전이다.<br>
오른쪽 하단을 보면 정확히는 6.1.22 버전이다. 이게 중요하다.<br>
그럼 이제 내 버전에 맞는 확장팩을 찾으러 가보자.

<br>

### 이전 버전 VirtualBox 확장팩 설치하기

<img src="/assets/images/posts_img/virtual-box-extpack-ver-error-solved/older_ver_download.jpg" alt="older_ver_download" width="70%">

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)에 들어가서 밑으로 내려가보면<br>
`VirtualBox older builds`를 찾을 수 있다.

<img src="/assets/images/posts_img/virtual-box-extpack-ver-error-solved/ver_list.jpg" alt="ver_list" width="70%">

클릭한 후 자신의 VirtualBox 버전에 맞는 확장팩을 다운 받는다.<br>
나는 VirtualBox 6.1 버전!

<img src="/assets/images/posts_img/virtual-box-extpack-ver-error-solved/correct_ver_check.jpg" alt="correct_ver_check" width="70%">

나는 아까 6.1.22 버전이었으니, 해당 버전에 가서 `Extension Pack` 버튼을 눌러 다운 받았다.

<img src="/assets/images/posts_img/virtual-box-extpack-ver-error-solved/new_extension_file.jpg" alt="new_extension_file" width="70%">

다운로드 받은 파일을 실행하면,

<img src="/assets/images/posts_img/virtual-box-extpack-ver-error-solved/ver_downgrade.jpg" alt="ver_downgrade" width="70%">

이렇게 다운그레이드 하겠냐고 메세지가 뜬다. `다운그레이드` 버튼을 클릭하자.

<img src="/assets/images/posts_img/virtual-box-extpack-ver-error-solved/success.jpg" alt="success" width="70%">

쨘 VirtualBox Extension Pack가 성공적으로 설치되었다!