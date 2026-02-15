# Render Deployment – agent.orcest.ai

## Full OpenHands Web UI

برای نمایش رابط کاربری وب OpenHands (نه فقط API)، این تنظیمات را اعمال کنید.

### 1. Build Command

در Render Dashboard → سرویس شما → **Settings** → **Build Command**:

```
cd frontend && npm ci && npm run build && cd .. && uv sync
```

### 2. Start Command

**Settings** → **Start Command**:

```
uv run -- uvicorn openhands.server.listen:app --host 0.0.0.0 --port $PORT
```

### 3. Health Check Path

**Settings** → **Health Check Path**: `/health`

### 4. OH_SECRET_KEY (اختیاری)

برای حفظ secrets بین ری‌استارت‌ها، در **Environment** متغیر اضافه کنید:

- Key: `OH_SECRET_KEY`
- Value: رشته تصادفی امن (مثلاً `openssl rand -base64 32`)

---

## Blueprint

اگر از `render.yaml` استفاده می‌کنید، این تنظیمات به‌صورت خودکار اعمال می‌شوند.
