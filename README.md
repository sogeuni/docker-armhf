# docker-armhf
Odroid용 Dockerbuild 파일 모음(같은 arm 계열이므로 라즈베리파이에서도 테스트는 안해봤지만 잘 동작할 듯)

기 빌드된 이미지는 [https://hub.docker.com/u/sogeuni/](https://hub.docker.com/u/sogeuni/)에 있음

## Plantuml

[plantuml 서버](http://plantuml.com/)

Alpine 리눅스 베이스에 jdk가 설치됨

### image build

```
docker build -t <image_name>:<tag> <plantuml_Dockerfile_path>
```

### image download

```
docker pull sogeuni/armhf-plantuml
```

## Gollum

[gollum 위키](https://github.com/gollum/gollum)엔진

Alpine 리눅스 베이스에 ruby 설치, auth를 위해 omniauth, omnigollum 설치, default git adapter에서 한글이 제대로 지원되지 않아 [rugged adapter](https://github.com/gollum/rugged_adapter) 추가함

### image build

```
docker build -t <image_name>:<tag> <gollum_Dockerfile_path>
```

