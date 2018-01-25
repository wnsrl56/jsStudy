
1. repository 생성 하기
    - git init --bare [my-project]
        - my-project는 보통 관례적으로 [my-project.git]으로 표현한다 
        - 빈 공유 용도의 git project 생성
        - 공유하기 위한 git folder 이동
            - 필요 아이템-> ssh 접속 가능한 서버, ssh 권한 (default port: 22)
            - **git bash**
              ```
              >scp -r [현재 위치 폴더명 or 절대 주소] [계정@원격지 주소]:[전달 위치]
              >scp [파일명][계정@원격지 주소]:[전달 위치]

              ex)
              >scp -r myPro root@192.168.23.129:/root/gitTest
              ```

    - git init [my-project]
        - local repository 생성
        - git remote 관계 형성
        - **git bash**
          ```    
          >git remote add [origin] [계정@원격지 주소]:[git remote bare repository 주소]
          // origin은 관례 상 사용

          >git add *
          >git commit -m 'init project'
          >git push --set-upstream origin master(추후 git push -{u}로도 대체 가능)
        
          >git pull
          >git push
          //테스트 진행
          ```

          ```
          ex)
          >git remote add origin root@192.168.23.129:/root/gitTest/myPro.git
          >git add *
          >git commit -m 'init'
          >git push --set-upstream origin master
          >git pull
          >git push
          ```
        추후 업데이트 시, git remote set-url [--push , --add, --delete] 사용

2. local branch 생성
```
>git branch [원하는 브런치 네임]
>git checkout [원하는 브런치 네임]
ex)
>git branch fix-bug
>git checkout fix-bug
```

3. remote branch 생성
```
>git remote add origin/fix-bug root@192.168.23.129:/root/gitTest/myPro.git
>git fetch
>git push --set-upstream origin/fix-bug
>git branch -vv
```

4. reset / log / revert / checkout
```
>git reset HEAD~2
(모든 기준은 branch / working directory 기준)
>
>
>
```

5. 기타
remote branch 제거하기
    - git remote [remote name] --delete [up stream branch name]
        ``` 
        ex) git remote origin --delete fix-bug 
        origin/fix-bug를 remote 저장소에서 제거한다.
        ```