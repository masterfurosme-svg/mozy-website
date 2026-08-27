# Mozy Construction — site + deploy

Site estático (HTML/CSS) da Mozy Construction. Deploy automatico: **GitHub → GitHub Actions → SFTP → Network Solutions**.

## Estrutura
- `index.html` — home
- `services/` — hub + 8 páginas de serviço
- `locations/` — Orlando, Broward County, Miami
- `about/`, `projects/`, `contact/`
- `css/style.css` — design system (tema Charcoal & Ember)
- `assets/` — logo + fotos de obra (ORIGINAIS; o deploy comprime automaticamente)
- `sitemap.xml`, `robots.txt`, `llms.txt`
- `.github/workflows/deploy.yml` — pipeline de deploy
- Docs (não vão pro site): `SEO-GEO-PLAN.md`, `faq-answers.md`, `youtube-kit.md`

## Ver localmente
```
py -m http.server 8137 --bind 127.0.0.1
```
Abrir http://localhost:8137

## Como colocar no ar (passo a passo — só o dono faz)

### 1. Criar o repositório no GitHub
No GitHub, criar um repo novo (ex.: `mozy-website`), **privado**. Depois, nesta pasta:
```
git remote add origin https://github.com/SEU-USUARIO/mozy-website.git
git branch -M main
git push -u origin main
```

### 2. Configurar os SECRETS (as credenciais — só você digita, ninguém mais vê)
No repo do GitHub: **Settings → Secrets and variables → Actions → New repository secret**. Criar:

| Secret | O que é | Onde achar |
|--------|---------|-----------|
| `SFTP_HOST` | endereço do servidor | painel da Network Solutions (ex.: `sftp.mozyconstructions.com`) |
| `SFTP_USER` | usuário de FTP/SFTP | painel da Network Solutions |
| `SFTP_PASSWORD` | senha de FTP/SFTP | painel da Network Solutions |
| `SFTP_PORT` | porta | `22` para SFTP (padrão) |
| `SFTP_REMOTE_PATH` | pasta pública do site | ex.: `/htdocs/`, `/public_html/` ou `/www/` (confirmar com a NS) |

> **Confirmar com a Network Solutions:** o serviço é **SFTP** (porta 22) ou **FTP/FTPS** (porta 21)?
> - Se for **SFTP** → o `deploy.yml` já está pronto.
> - Se for **FTP/FTPS** → me avisa que eu troco o passo de deploy para o `SamKirkland/FTP-Deploy-Action` (uma linha de mudança).

### 3. Deploy
A cada `git push` na branch `main`, o site sobe sozinho. Também dá pra rodar manual em **Actions → Deploy to Network Solutions → Run workflow**.

### 4. Rollback (se algo quebrar)
Reverter para a versão anterior no GitHub e dar push — o Actions reenvia a versão boa.

## Ainda pendente (conteúdo)
- **Zoho:** colar os IDs reais do Web-to-Lead em `contact/index.html` e no formulário da home (`index.html`), no lugar de `ZOHO_FORM_ID_HERE` / `ZOHO_SECRET_ID_HERE`.
- **Reviews:** trocar os depoimentos-exemplo da home por reviews reais do Google.
- **Logo:** quando houver versão "Mozy Construction" com fundo transparente (PNG/SVG), substituir `assets/logo.jpg`.
