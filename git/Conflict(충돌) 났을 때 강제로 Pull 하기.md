수정한 파일이 conflict되면 

fetch로 remote 저장소에서 이전 fetch를 받은 다음

local 저장소를 reset hard를 사용하여 conflict 이전의 수정전 상태로 되돌립니다.

이후 pull 하면 remote에서 loacal로 정상적으로 다운받아집니다.

```
git fetch --all
git reset --hard origin/master
git pull origin master
```

여기서 pull과 fetch의 차이점이 궁금하실 수 있습니다.

PULL
Pull로 Git 명령어를 사용할 시에는 현재 작업하고있는 로컬에 커밋을 병합합니다. 
Pull 은 커밋을 먼저 검토하지 않고 자동으로 병합합니다.
지점을 면밀히 관리하지 않으면 자주 충돌 할 수 있습니다.

FETCH
fetch 할 때 Git은 현재 브랜치에 존재하지 않는 커밋을 현재 브랜치에서 수집한 다음 로컬 리포지토리에 저장합니다. 
현재 로컬의 상태와 병합하지 않습니다. 
이 기능은 저장소를 최신 상태로 유지해야 하지만 파일을 업데이트할 때 손상될 수있는 작업을 수행할 때 특히 유용합니다. 
커밋을 마스터로 통합하려면 merge를 사용하여 자연스럽게 합칠 수 있습니다.

```
git checkout master                                                  
git fetch                                        
git diff origin/master
git rebase origin master
```

위와 같은 방법으로 diff로 변화된 것을 확인한 다음에 
rebase로 커밋을 재정리할 수도 있습니다.


출처 : 
https://gist.github.com/vladimirtsyupko/10964772
https://code.i-harness.com/ko/q/47605
