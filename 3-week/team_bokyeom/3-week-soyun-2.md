# 3주차

> **깃허브**
> 
1. 깃허브에서 본인 레포 만들기(노란색 부분)
2. `Code` 를 눌러서 주소를 복사한다.

![Untitled](3%E1%84%8C%E1%85%AE%E1%84%8E%E1%85%A1%205bd21e730a9d42cb9141435f660b486f/Untitled.png)

1. 본인 컴퓨터 작업공간에 우클릭해서 `git bash` 를 열어준다.
2. 디렉토리 설정하고 2에서 복사해온 주소를 클론한다.

```bash
#깃, 깃허브에 올릴 폴더 설정
$ cd "Workspace 디렉토리"

#폴더를 어떤 깃허브 레포에 올릴지 설정
$ git clone "본인 깃허브 주소"
```

1. 깃허브 폴더가 생성되면 그 안에 깃허브에 올릴 파일을 넣는다.
2. 잘 잡는지 상태를 확인하고, add, commit, push 한다.

```bash
#파일 상태 확인
$ git status

#add
$ git add 파일이름.확장자

#작업 공간의 모든 파일을 올리기 
$ git add .

#commit
$ git commit -m "같이 올라갈 메세지"

#push
$ git push
```

1. 깃허브를 새로고침하고 파일이 올라왔는지 확인한다.
2. `Contribute`를 눌러 PR한다. 

![Untitled](3%E1%84%8C%E1%85%AE%E1%84%8E%E1%85%A1%205bd21e730a9d42cb9141435f660b486f/Untitled%201.png)