# ChainRule - GitHub Pages

Красивая sample страница для демонстрации GitHub Pages.

## 🚀 Как задеплоить на GitHub Pages

### Вариант 1: Через веб-интерфейс GitHub (самый простой)

1. **Запушьте код в GitHub:**
   ```bash
   git add .
   git commit -m "Add sample page"
   git push origin main
   ```

2. **Настройте GitHub Pages:**
   - Перейдите в Settings вашего репозитория
   - В левом меню найдите раздел "Pages"
   - В разделе "Source" выберите ветку `main` и папку `/ (root)`
   - Нажмите "Save"
   - Через несколько минут ваш сайт будет доступен по адресу: `https://<your-username>.github.io/chainrule/`

### Вариант 2: Через GitHub Actions (автоматический деплой)

1. **Создайте файл `.github/workflows/deploy.yml`:**
   ```yaml
   name: Deploy to GitHub Pages

   on:
     push:
       branches: ["main"]
     workflow_dispatch:

   permissions:
     contents: read
     pages: write
     id-token: write

   jobs:
     deploy:
       environment:
         name: github-pages
         url: ${{ steps.deployment.outputs.page_url }}
       runs-on: ubuntu-latest
       steps:
         - name: Checkout
           uses: actions/checkout@v4
         - name: Setup Pages
           uses: actions/configure-pages@v4
         - name: Upload artifact
           uses: actions/upload-pages-artifact@v3
           with:
             path: '.'
         - name: Deploy to GitHub Pages
           id: deployment
           uses: actions/deploy-pages@v4
   ```

2. **Запушьте изменения:**
   ```bash
   git add .
   git commit -m "Add GitHub Actions workflow"
   git push origin main
   ```

3. **Настройте GitHub Pages:**
   - Перейдите в Settings → Pages
   - В разделе "Source" выберите "GitHub Actions"

### Вариант 3: С использованием gh-pages branch

1. **Установите gh-pages (если используете npm):**
   ```bash
   npm install -g gh-pages
   ```

2. **Задеплойте:**
   ```bash
   gh-pages -d . -b gh-pages
   ```

3. **Настройте GitHub Pages:**
   - Settings → Pages → Source → выберите ветку `gh-pages`

## 📝 Структура проекта

```
chainrule/
├── index.html      # Главная страница
└── readme.md       # Документация
```

## 🎨 Особенности sample страницы

- ✨ Современный градиентный дизайн
- 🎭 Плавные анимации при загрузке и взаимодействии
- 📱 Адаптивный дизайн (mobile-friendly)
- 🎯 Минималистичный и чистый код
- 💜 Использование CSS Grid и Flexbox

## 🔧 Кастомизация

Вы можете легко изменить:
- Цвета градиентов в CSS (переменные с `#667eea` и `#764ba2`)
- Текст контента в HTML
- Добавить свои секции и функционал

## 📍 Проверка статуса деплоя

После настройки GitHub Pages проверьте статус:
- Вкладка "Actions" в репозитории покажет процесс деплоя
- Settings → Pages покажет URL вашего сайта

---

**Готово!** 🎉 Теперь у вас есть красивая страница на GitHub Pages!
