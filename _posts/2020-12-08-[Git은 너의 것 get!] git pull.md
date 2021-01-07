---
title: "PULL!!"
excerpt: "밀당하지마!"
categories:
  - git
tags:
  - git
---
> GIT PUll 시에 자동으로 REBASE!

안녕하세요. ! MONKEY.D 입니다 :-) 코로나가 요즘 600명대 돌파하고 감염자 수가 줄 기미가 보이질 않습니다. 

그럴 때는 집에서 저와 같이 블로그를 참고하면서 공부를.. (자신에게 몽키킥!!) 서론이 길었습니다. 

이번 포스팅은 git pull시에 rebase를 사용할 것인지 사용하지 않을 것인지에 대한 이야기는 아닙니다. 



프로젝트를 진행하며 일반적으로 많은 분들이 commit history를 선호하시는 것을 알게 되었습니다. 

일반적으로 merge를 통해 만들어진 히스토리는 복잡하고 효율적이지 못합니다.

{: .notice--success}



때문에 rebase를 이용하여 pull을 하여 만들어진 히스토리는 직관적입니다. 예를 들어 다음과 같은 작업은 소스코드의 merge를 발생 시킵니다.

1. git pull (로컬의 소스를 최신으로 업데이트 하기 위해 수행함)
2. 개발을 start!
3. git commit
4. git pull
5. git push

기본적으로 git pull은 remote로부터 새로운 commit들을 가져옵니다. 그리고 로컬의 코드들에 merge를 합니다.

![KakaoTalk_20201210_225103022](https://user-images.githubusercontent.com/74045426/101781435-27192280-3b3b-11eb-804e-9d929578be65.png)

좀 더 개선을 위해 git pull 대신에 git pull -rebase 명령을 사용하는 것을 생각해 볼수 있습니다! 이 명령은 remote로부터 가져온 commit들 뒤에 새로운 나의 commit들을 추가합니다.

여러분들의 git이 pull 시에 기본적으로 merge를 사용하지 않고 rebase를 선택하도록 설정할 수 있습니다. 다음의 명령은 이후의 모든 브랜치들에 대해 기본적을 rebase를 설정하도록 해줍니다.

```
$ git config --global branch.autosetuprebase always
```



그러나! 위의 명령은 이미 개발중인 branch에는 적용되지 않습니다. 이미 개발중인 branch에는 다음과 같은 명령을 사용하여 적용할 수 있습니다. (적용하려는 프로젝트 root 디렉토리에서 실행!)

```
$ git config branch. {BRANCH-NAME}.rebase true
```

{BRANCH-NAME} 대신, master와 같은 여러분이 적용하고자 할 적절한 branch 명을 적어주세요! 



오늘은 간단한 포스팅 글이였습니다. 읽어주셔서 감사합니다! 이상 MONKEY.D 였습니다. 