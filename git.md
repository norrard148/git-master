# 무턱대고 해봅시다
* git init
<br><br>
깃은 'reposiotry'라는, 일종에 자기가 깃헙 서버에 올리기 전에 로컬에 약간 중간 서버같은 느낌의 임시 저장소를 만드는데, 이것이 바로 repository이고, 위 명령어는 그 저장소인 '레파지토리를 만드는 것을 말한다.

* git remote -v
<br><br>
그리고 그 레파지토리는, 자신이 담고 있는 내용들을 어디에 올릴지를 알기 위해서 'remote'라는, 일종의 '라우터'같은 개념으로 주소를 몇개를 알고 있어야하는데, 내가 등록한 주소 목록을 알게 해주는 것이 git remote -v다. 아무것도 안한상태로 git remote -v하면 대부분 예전에 해놓앗던 것이 뜨거나 아무것도 안 뜬다.

* git remote -v
<br>
이것은 지정되어 있는 remote를 확인하는 법이다.

* git remote add origin "주소"
<br>
이것은, 별명이 origin이면서 주소는 "주소"인 라우터를 만들으라는 것이다.

* git remote add awesome "주소"
* git remote rename awesome cool
* git remote show cool

# 자, repository를 만들고, 그리고 그 저장소가 나중에 깃헙 어디에 올릴지를 지정해주는 remote까지 만들어보았다! 이제 우리가 해야할 것은 github에서 진짜 한번 가져와보는 것이다.

* git clone "주소"
<br><br>
이러면 깃헙의 한 프로젝트(repository)가 불러와진다. 다만 필독! git clone은, git init을 하지 않아도 된다. 왜냐? 왜냐면 이것은 우리가 불러오는거지 repository를 만들어 올리는 것은 아니기 때문이다! 실습을 해보면 알 수 있다.
<br><br>
그렇다는 것은! git clone과 git init 및 git remote의 기능이 무엇인지 차이를 느껴야 한다는 것!

# 다음으로 넘어가서, 우리는 이제 누군가의 깃헙 프로젝트를 불러왔다. 그런데 나는 여기서 브랜치를 만들어보고 싶다!
* 들어가기 전에 앞서, 좀 더 이야기 할 것이 있다. 아까 전에, git init으로 repository라는 일종의 '중간 서버'를 만든다고 했다(정확히는 중간 저장소). 그리고 그 중간서버가 어떻게 움직여야되는지를 알려주는 라우터기능은 'remote'가 한다고 했다. 그런데, 그 repository가 엄밀하게 말하면 local repository와 remote repository로 나뉘어져 있다. local repository는 진짜 내가 로컬인 bash 내지 기타 환경에서 작용하는 내 컴퓨터에서 만들어진 repository를 말하고, remote repository는 깃헙에 진짜 올라와져있는 깃헙 서버에서 만들어주는 repository를 말한다. 그리하여 도식은 이러하다.
<br><br>
내 visual code 상에 열려 있는 파일 ---> bash같은 터미널--->내 컴퓨터의 repository ---> 깃헙 서버에서 만들어준 repository ---> 깃헙 서버--->깃헙 최종 저장소(db)
<br><br>

* git branch 브랜치이름
<Br><Br>
이것은, 브랜치를 만드는 용어다. 하지만 명심해야 할 것은, 이 브랜치는 '내 로컬 repository'에서 만들어지고 마는 것 뿐이다. 이것이 완벽하게 깃헙측 repository까지 전달되기 위해서는, git add . 하고 git commit -m "" 하고 git push origin 브랜치이름 까지 해야, 깃헙서버에서도 브랜치를 형성해주고 결국으로는 깃헙 서버로 넘어가 깃헙 저장소까지 넘어가게 된다. 물론, 그냥 브랜치만 피상적으로 만들고 싶다면, git add . git commit -m "" 안하고, 그냥 git push origin 브랜치이름 하면된다!
* git branch
<br>
'내 로컬 repository'의 branch 목록을 나열하라는 명령어이다.

* git branch -r
<br>
'깃헙측 repository'의 branch 목록을 나열하라는 명령어이다.
* git branch -a
<br>이건 로컬 뿐만 아니라 깃헙측 repository의 branch 목록을 보이라는 명령어이다.


## 여기서 질문! 그럼 내 로컬 repository와 깃헙측 repository 내 branch는 이름이 달라도 되는걸까요? 달라도 되는거면,,, 어떻게 서로 이어주는 거죠?
* git branch --set-upstream-to 깃헙측레파지토리이름/깃헙측레파지토리내브랜치이름
<br><br>
달라도 됩니다! 그리고 연동은 위 코드대로 하는것이구요, 예제는 아래에 있습니다. 물론, 연동하기 위해서 미리 checkout을 연동하고싶은 로컬 브랜치로 접속해놓아야합니다.
<br>
ex) git branch --set-upstream-to origin/youngjae
<br>
여기서 더 알아야 할 것은, <br>git branch 브랜치이름 <br>해서 만들고 난 다음 <br>git push origin 브랜치이름 <br> 으로 깃헙측 repository에 브랜치까지 만들면 자동으로 둘이가 연동된다는 것을 뜻합니다! 이것은,<br> git remote show origin <br해봐도 확인해볼 수 있습니다.

* git checkout youngjae

* git checkout -b sangwoo
 
 * git branch -d 브랜치이름
 <br>
 이 명령어는 로컬 브랜치를 삭제하는 명령어입니다. 대신, 이 명령어는 지우고 싶은 '로컬' 브렌치로 checkout해서 접속을 해야가능합니다.

 * git brnach -D 브랜치이름
 <br>
 이 명령어는 다른 로컬 브랜치 접속상태에서도 딴 로컬 브랜치를 없앨 수 있습니다.

 ## 그럼 로컬 브랜치 말고, 깃헙측 레파지토리 안에 있는 브랜치는 어떻게 없애나요!
 * git push origin :브랜치이름
 <br>
 이러면 없어집니다!
 <br>
 대신 주의할 점은, 깃헙측 레파지토리 없앤다는 것은, 깃헙 사이트에서 브랜치 단추 눌러서 열리는 그 브랜치 목록에서 해당 없애고 싶은 브랜치를 없애겠다는 말이에요! 다시말해서, 진짜로 브랜치를 없애겠다는 말입니다.


# 여기까지, 기본적으로 로컬 레파지토리와 깃헙 레파지토리를 만들고 그 안에 branch를 만들어 가지고 노는 법을 배워 보았다.

## 이번엔, 다소 아리까리 할 수 있는 내용을 확실히 이해하고자 몇가지를 해보아야 한다. 제가 만들어 놓은 github 프로젝트를 하나 다운받아야 합니다.

* git clone https://github.com/norrard148/git-master.git

* cd git-master

* git branch
<br>
아마, master 하나만 딸랑 있을 겁니다. 왜일까요?
<br>
아까도 말했듯이, 처음 프로젝트를 다운 받으면, 로컬 레파지토리는 텅텅 비어있는 상태입니다. 그래서, 깃헙측 레파지토리는 많은 브랜치가 있음에도 하나도 뜨지 않는 것이죠. 그래서 우리는, 몇개의 로컬 브랜치를 만들어서, 그것을 각각 깃헙측 레파지토리에 연동시켜서 사용하는 법을 익혀 볼 겁니다.

* git branch connect-youngjae
* git checkout connect-youngjae
* git branch --set-upstream-to origin/youngjae
* git pull origin youngjae
* app.js 들어가봅니다.
* console.log("youngjae"); 을 더 써넣습니다.
* git add .
* git status
* git commit -m "md+"
* git push origin youngjae
<br> 이거 하면 오류 생깁니다. 왜일까요?
<br> 그 이유는, git push 자체가 별도의 설정없이 하면 현재 체크아웃 되어 있는 로컬 브랜치랑 깃헙 레파지토리측 브랜치 이름이 '같을 때만 해주거나, 혹은 같은 놈들이 있으면 그놈끼리만 연결해서 해줍니다. 그래서 그런 것입니다. 그래서 이럴 땐,
* git push
<br>
해보면 안내문이 뜨는데, 여기서,
*git push origin HEAD:youngjae
<br>로 하라고 합니다. 이렇게 하면됩니다. 이 방법은, 사실 어느 브랜치든간에, 올리고 싶은 깃헙측 레파지토리가 있는데 지금 내가 그 레파지토리와는 이름이 다른, 다른 브랜치에 있을 때, 체크아웃되어 있는 현재의 나의 로컬 브랜치 내용을, 브랜치 영역 초월해서 업로딩해버릴 수 있는 명령어이기도 합니다.

## 자그럼, 이로써 우리는 로컬 브랜치 connect-youngjae 라는 놈을 만들었고? 그리고 얘를 깃헙 브랜치인 youngjae와 연결짓는 한편, connect-youngjae가 체크아웃 되어 있는 상태에서, 즉 그 브랜치에 들어와 있는 상태에서 깃헙 브랜치 youngjae 내용을 고대로 git pull origin youngjae로 불러와서? 비쥬얼 코드에 띄운 다음?, app.js에서 수정을 하고, git add . git commit -m "" 이런 걸 다하고? 다시 원래 가져왔던 브랜치인 깃헙측 브랜치인 youngjae에 다시 업로딩하는것까지 해보았습니다!

## 그러면, connect-youngjae 브랜치에 체크아웃 되어 있는 상태에서, 깃헙측 브랜치인 sangwoo 브랜치를 불러온다음, 수정을 하고 난 뒤, 이걸 hangyeol 깃헙 브랜치에 업로딩 할 수는 없을까요? 가능합니다!






