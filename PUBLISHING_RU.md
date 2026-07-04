# Как опубликовать этот HTML на GitHub Pages

## Что уже подготовлено

Папка проекта:

`C:\ESB Group\pink-wire-procurement-site`

Внутри:

- `index.html` - страница сайта. GitHub Pages ищет именно это имя.
- `.nojekyll` - просит GitHub отдать HTML как есть, без Jekyll-сборки.
- `README.md` - короткое описание проекта.

## Важная рекомендация по приватности

GitHub Pages публикует сайт в интернете. Даже если репозиторий приватный на платном плане, сам Pages-сайт может быть публично доступен по ссылке. Если в отчёте есть цены, поставщики, внутренние комментарии или клиентские данные, лучше сначала удалить чувствительные данные или использовать приватный способ передачи.

Если нужна схема "коллега открывает ссылку, логинится в GitHub и видит работающий сайт", обычный личный GitHub-аккаунт для этого не подходит. Приватный GitHub Pages с контролем доступа доступен только для репозиториев организации на GitHub Enterprise Cloud.

Для личного аккаунта есть два безопасных варианта:

1. Приватный репозиторий + коллега как collaborator. Он сможет скачать `index.html` и открыть локально, но это не будет полноценная Pages-ссылка на сайт.
2. Не GitHub Pages, а хостинг с авторизацией: SharePoint/OneDrive, Cloudflare Access, Netlify/Vercel с password/auth protection, внутренний корпоративный сервер.

## Вариант A: через веб-интерфейс GitHub

1. На странице создания репозитория укажите:
   - Repository name: `pink-wire-procurement-site`
   - Visibility: `Private`, если данные нельзя публиковать в интернет
   - Add README: `Off`
   - Add .gitignore: `No .gitignore`
   - License: `No license`

2. Нажмите `Create repository`.

3. На странице нового пустого репозитория выберите `uploading an existing file`.

4. Перетащите эти файлы из папки проекта:
   - `index.html`
   - `.nojekyll`
   - `README.md`

5. Нажмите `Commit changes`.

6. Если у вас обычный личный GitHub-аккаунт, не включайте Pages для чувствительных данных. Вместо этого добавьте коллегу в `Settings` -> `Collaborators` и дайте ему доступ к приватному репозиторию.

7. Если репозиторий принадлежит GitHub Enterprise Cloud organization и вам доступен private Pages, откройте `Settings` -> `Pages`.

8. В блоке `Build and deployment` выберите:
   - Source: `Deploy from a branch`
   - Branch: `main`
   - Folder: `/ (root)`

9. В блоке видимости Pages выберите `Private`, если такая настройка есть.

10. Нажмите `Save`.

11. Подождите несколько минут. Если это публичный project Pages, ссылка обычно будет:

`https://leodenebesb-hub.github.io/pink-wire-procurement-site/`

Если это private Pages в Enterprise Cloud, GitHub покажет отдельную защищённую ссылку в `Settings` -> `Pages`.

## Вариант B: через git

После создания пустого репозитория на GitHub выполните в этой папке:

```powershell
git remote add origin https://github.com/leodenebesb-hub/pink-wire-procurement-site.git
git push -u origin main
```

Потом включите Pages в `Settings` -> `Pages`: `Deploy from a branch`, `main`, `/ (root)`.

## Как проверить

Откройте опубликованную ссылку и проверьте:

- переключение языков RU / EN / ET;
- фильтры и поиск;
- кнопки копирования;
- экспорт CSV/JSON;
- заметки, которые сохраняются в браузере;
- курс GBP->EUR, если нужен runtime-пересчёт.

GitHub Pages иногда публикует изменения не сразу. Нормально подождать до 10 минут.
