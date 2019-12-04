Springboot + nginx + docker default setting
===========================
###1. Spring-boot 파일을 Dockerfile 로 만드는 작업
####1.1 pom.xml 에 다음을 추가한다.
    <properties>
        <docker.image.prefix>[image 명]</docker.image.prefix>
    <properties>
    
    <build>
      <plugins>
           <plugin>
               <groupId>com.spotify</groupId>
               <artifactId>dockerfile-maven-plugin</artifactId>
               <version>1.4.9</version>
               <configuration>
                 <repository>${docker.image.prefix}/${project.artifactId}</repository>
               </configuration>
           </plugin>
       <plugins>
    <build>

####1.2 Dockerfile 을 생성한다.
    ./Dockerfile
    docker image -t springboot:0.1 .

###2. nginx + Springboot 를 연결하여 도커에 올리기
####2.1 nginx 이미지를 직접 빌드하여 할 경우
    ./nginx 하위 파일 참조
    docker image -f nginx-Dockerfile --name springboot-nginx:0.1 .
####2.2 docker-compose.yml 을 만들어서 업로드 한다.
    docker-compose up

본 프로젝트와 동일하게 구성을 할 경우 **localhost:80/** 를 통해 외부접속이 가능하다.
