# Render Deployment – agent.orcest.ai

## روش استقرار: Docker (توصیه‌شده)

از `Dockerfile.render` استفاده می‌شود تا تمام system dependencies (tmux, git, node) داخل ایمیج نصب شوند.

### تنظیمات Render Dashboard

1. **در Settings سرویس:**
   - **Environment:** `Docker`
   - **Dockerfile Path:** `Dockerfile.render`
   - **Health Check Path:** `/health`

2. **متغیرهای محیطی (Environment):**

| متغیر | مقدار | توضیح |
|-------|-------|--------|
| `OH_APP_MODE` | `oss` | صفحه اصلی از `/` بدون login |
| `RUNTIME` | `local` | LocalRuntime (tmux در Docker نصب است) |
| `WORKSPACE_BASE` | `/tmp/workspace` | مسیر workspace |
| `OH_SECRET_KEY` | (Generate) | حفظ secrets بین restart |

3. **کلید API:**
   - `OPENAI_API_KEY` – برای GPT-4o
   - یا `ANTHROPIC_API_KEY` – برای Claude
   - یا در رابط وب از **Settings → LLM** وارد کنید

### Deploy

بعد از تنظیمات بالا، **Manual Deploy** با **Clear build cache** بزنید.

---

## Blueprint

اگر از `render.yaml` استفاده می‌کنید، تنظیمات Docker به‌صورت خودکار اعمال می‌شوند.
