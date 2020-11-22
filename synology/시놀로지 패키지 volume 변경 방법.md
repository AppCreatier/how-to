# Synology Package Swap

바꾸실때 가급적 putty에서 하지마시고... sudoers에서 root 권한 얻은후
winscp에서 하세요. 소프트 링크 수정하는거 패키지 많아 지면 일일이 타이핑 하기 불편합니다. 
winscp에서 더블클릭해서 편집으로 열어서 루트만 재설정 해주면 됩니다.

패키지 설치 볼륨 변경하기 (DSM 6.0 기준)

1. putty를 이용해서 ssh로 접속하고 관리자 권한을 얻는다. (sudo -i)
2. 패키지센터에서 이동할 패키지를 실행 중지시키고, 패키지 센터를 닫는다.
3. sh에서 아래와 같이 명령어를 입력한다. (volume1 -> volume2 예시)

```
mv /volume1/\@appstore/[패키지명] /volume2/\@appstore/
rm -fv /var/packages/[패키지명]/target
ln -s /volume2/\@appstore/[패키지명] /var/packages/[패키지명]/target
rm -fv /usr/local/[패키지명]
ln -s /volume2/\@appstore/[패키지명] /usr/local/[패키지명]
```

여기서 옮길 패키지명은 'ls /volume1/\@appstore'를 입력하면 알 수 있다.
그리고 '@'는 앞에 \로 escaping이 필요하다는 것을 주의해야 한다.

4. 패키지센터를 다시 열고 패키지 설치 경로가 변경된 것을 확인하고 다시 실행시킨다.


출처: https://www.clien.net/service/board/cm_nas/11003726
