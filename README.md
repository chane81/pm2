# PM2

## pm2 설치
> yarn global add pm2

## pm2-windows-startup 설치
- 서버를 재시작하여도 node 서비스가 죽지 않게 하는 모듈이다.
  > yarn global add pm2-windows-startup
  
  > pm2-startup install

## pm2 서비스
- pm2 로 node 서버를 시작
  > pm2 start my-server.js

- pm2 로 미리 설정된 json 파일로 서버를 시작
  > pm2 start server.json

  ```json
    {
    "apps": [
      {
        "name": "blog-server",
        "script": "H:\\#2. Project\\React\\react_study\\lesson19-blog-back-end-mongodb\\src\\index.js",
        "instances": 4,
        "env": {
          "pm_cwd": "H:\\#2. Project\\React\\react_study\\lesson19-blog-back-end-mongodb",
          "npm_package_scripts_start_pm": "cross-env node_path=src",
          "node_path": "src"
        }
      }
    ]
  }
  ```

- 서버가 올라갔는지 확인
  > pm2 list
  ![alt text](/images/pm2_list.png)

- pm2 서버 리스트 환경 저장
  - pm2 에서 node 서비스 설정 저장 명령어

    > pm2 save

  - 위와 같이 `pm2 save` 를 해주면 아래 경로로 설정이 저장되고, 서버가 재시작 되더라도 서비스가 죽지 않게 된다. 

    > C:\Users\chane\.pm2\dump.pm2


- pm2 서버환경설정파일(dump.pm2)에서 불러와서 pm2 서비스 시작
  > pm2 resurrect

## pm2 flow
```
yarn global add pm2
yarn global add pm2-windows-startup
pm2-startup install
pm2 start app.js --name my-app
pm2 save
reboot
pm2 ls
```