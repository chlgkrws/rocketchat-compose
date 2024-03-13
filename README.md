###  Rocket.Chat Server 실행 환경 (도커 컴포즈)

Rocket chat 분석 중 [공식 문서](https://docs.rocket.chat/deploy/deploy-rocket.chat/deploy-with-docker-and-docker-compose)를 통해 다운로드 받은 compose.yml이 실행되지 않는 이슈 발생

MongoDB 레플리카 호스트 네임 불일치 이슈, env 파일을 식별하지 못하는 이슈를 해결한 실행환경을 업로드함


### 실행 방법
```shell
# MongoDB data 폴더 추가 
$ mkdir mongodb_data

# docker compose 실행
$ docker-compose up -d

# MongoDB 호스트 네임 수정 (서버 실행 후 1회만 수행)  
$ docker-compose exec mongodb mongo

> config = rs.config()
> config.members[0].host = 'mongodb:27017'
> rs.reconfig(config)
```

### 접속 확인
localhost:3000



### Reference
- https://github.com/RocketChat/Rocket.Chat/issues/7560
  
- https://github.com/RocketChat/Rocket.Chat/issues/26519
