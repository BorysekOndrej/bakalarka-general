



## Docker deployment

Install usin
```bash
git clone https://github.com/BorysekOndrej/bakalarka-general.git
cd bakalarka-general/docker-deployment
cp backend/dist.env backend/.env
cp frontend/dist.env frontend/.env
cp sslyze_rq/dist.env sslyze_rq/.env

# Optional: replace REMOTE_COLLECTOR_KEY in backend/.env and sslyze_rq/.env
# Optional: replace VUE_APP_API_URL in frontend/.env
# Optional: replace server_name in nginx/nginx.conf

docker-compose up # possibly run in background, if you want to
```

Update using:
```bash
# https://stackoverflow.com/a/61362893/

docker-compose pull
docker-compose up -d --remove-orphans
# docker image prune  # Optional: This removes all dangling images. Not just the ones from this project.
```
