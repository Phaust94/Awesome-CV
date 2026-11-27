Building and running the repo
```bash
docker build -t cv-builder --platform linux/amd64 . && \
 (docker rm cv-container || true) && \
  docker create --name cv-container --platform linux/amd64 cv-builder && \
  docker cp cv-container:/resume/out/resume.pdf ./output/Awesome_CV_Bohdanov.pdf
```