repo 생성 및 포크

git branch dev

git checkout dev

ls 분기점 기준

git merge dev

git branch -b dev (있으면 이동, 없으면 만든후 이동 단축표현)

---

branch 지우기 git branch -D

(node_modules 폴더 업로드하지말기 .gitignore가 있어야됨)

---

git flow전략 (git flow daniel 검색)

git flow init

-> 만든적 없는 develop branch가 생김, 그리고 자동으로 체크아웃됨 develop에서만 작업하면됨

git flow feature start ~~~

git flow feature finish ~~~

git flow release start ~~~

git flow release finish ~~~

<br>

write a message for tag : 기능 태그 ☆ 중요

<br>

fork & clone

git remote -v

git remote add 별명 _원본주소

push후 pull reqeust했는데 아직 안받은상태에서 수정사항이 발생하면 수정한것까지 모두 올라감

complict 발생 => git pull 별명 master에서 가져와서 충돌해결

