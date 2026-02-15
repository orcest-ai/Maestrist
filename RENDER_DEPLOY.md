# Render Deployment – agent.orcest.ai

## Quick fixes for existing deployments

### 1. Root path (/) returning 404 – fixed in code

The app now returns a JSON response at `/` instead of 404. Redeploy to pick up the change.

### 2. Health check (if Render probes `/`)

In the Render Dashboard → your service → **Settings**:

- Set **Health Check Path** to `/health` (instead of `/`)

### 3. OH_SECRET_KEY warning

To persist secrets between restarts, add this env var in the Render Dashboard:

- **Environment** → **Add Environment Variable**
- Key: `OH_SECRET_KEY`
- Value: Generate a secure random string (e.g. `openssl rand -base64 32`)

---

## Blueprint deployment

If using `render.yaml` (Blueprint), the health check and `OH_SECRET_KEY` are configured there.
