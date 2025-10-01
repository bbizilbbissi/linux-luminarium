It's not just hackers that need to become `root`.
Oftentimes, you, as the owner of your computer, need to use `root` access to administer it.
Becoming `root` is a fairly common action that Linux users take, and there are two utilities that exist for this purpose: `su` and `sudo`.
해커만 `root` 권한을 얻어야 하는 것은 아닙니다.
컴퓨터 소유자는 종종 `root` 권한을 사용하여 컴퓨터를 관리해야 합니다.
`root` 권한을 얻는 것은 Linux 사용자가 흔히 사용하는 작업이며, 이를 위한 두 가지 유틸리티가 있습니다. `su`와 `sudo`입니다.

In this challenge, we will cover the older one, `su` (the **s**ubstitute **u**ser command).
This is not typically used to elevate to `root` access anymore, but it is an elegant utility from a more civilized time, and we'll cover it first.
이번 챌린지에서는 더 오래된 명령어인 `su`(**s**substitute **u**ser 명령어)를 다루겠습니다.
이 명령어는 더 이상 `root` 권한으로 승격하는 데 일반적으로 사용되지 않지만, 문명화된 시대의 우아한 유틸리티이므로 먼저 살펴보겠습니다.

`su` is a setuid binary:
`su`는 setuid 바이너리입니다.

```console
hacker@dojo:~$ ls -l /usr/bin/su
-rwsr-xr-x 1 root root 232416 Dec 1 11:45 /usr/bin/su
hacker@dojo:~$
```
``콘솔
hacker@dojo:~$ ls -l /usr/bin/su
-rwsr-xr-x 1 루트 루트 232416 12월 1일 11:45 /usr/bin/su
hacker@dojo:~$
````

Because it has the SUID bit set, `su` runs as `root`.
Running as `root`, it can start a `root` shell!
Of course, `su` is discerning: before allowing the user to elevate privileges to `root`, it checks to make sure that the user knows the `root` password:
SUID 비트가 설정되어 있으므로 `su`는 `root`로 실행됩니다.
`root`로 실행하면 `root` 셸을 시작할 수 있습니다!
물론 `su`는 분별력이 뛰어납니다. 사용자가 `root`로 권한을 승격하도록 허용하기 전에 사용자가 `root` 비밀번호를 알고 있는지 확인합니다.

```console
hacker@dojo:~$ su
Password: 
su: Authentication failure
hacker@dojo:~$
```
```콘솔
hacker@dojo:~$ su
비밀번호:
su: 인증 실패
hacker@dojo:~$
```

This check against the `root` password is what obsoletes `su`.
Modern systems very rarely have `root` passwords, and different mechanisms (that we will learn later) are used to grant administrative access.
`root` 비밀번호에 대한 이러한 확인은 `su`를 더 이상 사용하지 않게 만듭니다.
최신 시스템에서는 `root` 비밀번호를 사용하는 경우가 매우 드물며, 관리자 권한을 부여하기 위해 다른 메커니즘(나중에 살펴보겠습니다)이 사용됩니다.

But THIS challenge (and only this challenge) _does_ have a `root` password.
That password is `hack-the-planet`, and you must provide it to `su` to become `root`!
Go do that, and read the flag!
하지만 이 챌린지(그리고 오직 이 챌린지만)에는 `root` 비밀번호가 있습니다.
그 비밀번호는 `hack-the-planet`이고, `root`가 되려면 `su`에 이 비밀번호를 입력해야 합니다!
그렇게 하고 플래그를 읽어보세요!
