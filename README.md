# bt-docker

## 1) docker build

```bash
docker build -t bt-docker:latest .
```

## 2) docker run

```bash
docker run --rm -it -p 8080:80 --name bt-docker bt-docker:latest
```

Open `http://localhost:8080`.

## 3) docker compose

```bash
docker compose up -d --build
docker compose logs -f
docker compose down
```

## GitHub + CI/CD (bài tập)

### 1) Tạo GitHub repo và đẩy source lên

```bash
git init
git branch -M main
git add .
git commit -m "init: docker build/run/compose"
git remote add origin <GITHUB_REPO_URL>
git push -u origin main
```

### 2) Tạo GitHub Secrets cho Docker Hub

Trong GitHub repo → **Settings → Secrets and variables → Actions → New repository secret**:

- `DOCKERHUB_USERNAME`: `duytri0302`
- `DOCKERHUB_TOKEN`: Docker Hub **Access Token** (không dùng mật khẩu thường nếu bạn bật 2FA)

### 3) Workflow tự build + push lên Docker Hub khi push `main`

File đã có sẵn: `.github/workflows/deploy.yml`

Image được push lên Docker Hub:

- `duytri0302/bt-docker:latest`
- `duytri0302/bt-docker:<short-sha>`
