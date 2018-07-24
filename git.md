# 무턱대고 해봅시다
* git init
<br><br>
깃은 'reposiotry'라는, 일종에 자기가 깃헙 서버에 올리기 전에 로컬에 약간 중간 서버같은 느낌의 임시 저장소를 만드는데, 이것이 바로 그 저장소인 '레파지토리를 만드는 것을 말한다.

* git remote
<br><br>
그리고 그 레파지토리는, 자신이 담고 있는 내용들을 어디에 올릴지를 알기 위해서 'remote'라는, 일종의 '라우터'같은 개념으로 주소를 몇개를 알고 있어야하는데, 그 주소목록이 remote다.

* git remote -v
<br><br>
이것은 지정되어 있는 remote를 확인하는 법이다.

* git remote add origin "주소"
* git remote add awesome "주소"g
* git remote rename awesome cool
* git remote show cool

# 자, repository를 만들고, 그리고 그 저장소가 나중에 깃헙 어디에 올릴지를 지정해주는 remote까지 만들어보았다! 이제 우리가 해야할 것은 github에서 진짜 한번 가져와보는 것이다.

* git clone "주소"
<br><br>
이러면 깃헙의 한 프로젝트(repository)가 불러와진다. 다만 필독! git clone은, git init을 하지 않아도 된다. 왜냐? 왜냐면 이것은 우리가 불러오는거지 repository를 만들어 올리는 것은 아니기 때문이다! 실습을 해보면 알 수 있다.
<br><br>
그렇다는 것은! git clone과 git init 및 git remote의 기능이 무엇인지 차이를 느껴야 한다는 것!

# 다음으로 넘어가서, 우리는 이제 누군가의 깃헙 프로젝트를 불러왔다. 그런데 나는 여기서 브랜치를 만들어보고 싶다!
* 들어가기 전에 앞서, 좀 더 이야기 할 것이 있다. 아까 전에, git init으로 repository라는 일종의 '중간 서버'를 만든다고 했다(정확히는 중간 저장소). 그리고 그 중간서버가 어떻게 움직여야되는지를 알려주는 라우터기능은 'remote'가 한다고 했다. 그런데, 그 repository가 밀하게 말하면 로컬 repository와 remote repository로 나뉘어져 있다. 로컬 repository는 진짜 내가 로컬인 bash 내지 기타 환경에서 작용하는 내 컴퓨터에서 만들어진 repository를 말하고, remote repository는 깃헙에 진짜 올라와져있는 깃헙 서버에서 만들어주는 repository를 말한다. 그리하여 도식은 이러하다.
<br><br>
내 visual code 상에 열려 있는 파일 ---> 내 컴퓨터의 repository ---> 깃헙 서버에서 만들어준 repository ---> 깃헙 서버--->깃헙 최종 저장소(db)
<br><br>
* git branch
<br>
'내 로컬 repository'의 branch 목록을 나열하라는 명령어이다.

* git branch -r
<br>
'깃헙측 repository'의 branch 목록을 나열하라는 명령어이다.
*git branch -a
<br>이건 로컬 뿐만 아니라 깃헙측 repository의 branch 목록을 보이라는 명령어이다.

* git branch youngjae
<Br><Br>
이것은, 브랜치를 만드는 용어다. 하지만 명심해야 할 것은, 이 브랜치는 '내 로컬 repository'에서 만들어지고 마는 것 뿐이다. 이것이 완벽하게 깃헙측 repository까지 전달되기 위해서는, git add . 하고 git commit -m "" 하고 git push origin 브랜치이름 까지 해야, 깃헙서버에서도 브랜치를 형성해주고 결국으로는 깃헙 서버로 넘어가 깃헙 저장소까지 넘어가게 된다. 물론, 그냥 브랜치만 피상적으로 만들고 싶다면, git add . git commit -m "" 안하고, 그냥 git push origin 브랜치이름 하면된다!

# 여기서 질문! 그럼 내 로컬 repository와 깃헙측 repository 내 branch는 이름이 달라도 되는걸까요? 그럼 달라도 되는거면,,, 어떻게 서로 이어주는 거죠?
* 달라도 됩니다! 그리고 연동하는 방법은, 
<br>
git branch --set-upstream-to 깃헙측 repository이름/깃헙측 repository내 branch

* git checkout youngjae

* git checkout -b sangwoo
 






