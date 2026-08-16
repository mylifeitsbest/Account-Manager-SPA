<div align="center">

  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=700&size=26&pause=1000&color=F8D800&center=true&vCenter=true&width=650&lines=%E2%9A%99%EF%B8%8F+ACCOUNT+MANAGER+SPA;%F0%9F%9F%A9+VUE+3+%2B+TYPESCRIPT+%2B+PINIA;%F0%9F%92%BE+LOCALSTORAGE+PERSISTENCE" alt="Typing SVG" />

  <p align="center">
    <b>Реактивное Single Page Application для валидации, создания и централизованного управления учетными записями</b>
  </p>

  <p align="center">
    <img src="https://img.shields.io/badge/Vue_3-Composition_API-4FC08D?style=flat-square&logo=vuedotjs&logoColor=white" alt="Vue 3" />
    <img src="https://img.shields.io/badge/TypeScript-5.x-3178C6?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript" />
    <img src="https://img.shields.io/badge/Pinia-State_Store-FFD859?style=flat-square&logo=pinia&logoColor=black" alt="Pinia" />
    <img src="https://img.shields.io/badge/Vite-Bundler-646CFF?style=flat-square&logo=vite&logoColor=white" alt="Vite" />
    <img src="https://img.shields.io/badge/License-MIT-gray?style=flat-square" alt="License" />
  </p>

</div>

---

### 📌 О проекте

**Account Manager SPA** — модульное веб-приложение для гибкого менеджмента учетных записей двух типов: **Локальная** и **LDAP**. Интерфейс построен по принципам компонентно-ориентированной архитектуры с мгновенным откликом (Zero Latency), изолированной валидацией данных и автоматической синхронизацией сессий.

---

### 🚀 Ключевые возможности

* ⚡ **Динамический CRUD:** создание, редактирование и удаление любого количества записей в реальном времени.
* 🛡️ **Реактивная валидация (`@blur`):** проверка логина, пароля и длины строк с выводом подсказок об ошибках без блокировки интерфейса.
* 🔀 **Условный рендеринг полей:** автоматический сброс и скрытие поля «Пароль» при переключении типа аккаунта на **LDAP**.
* 💾 **Автономная персистентность:** непрерывный sync состояния со встроенным браузерным `localStorage` (данные не сбрасываются при перезагрузке страницы).
* 🏷️ **Парсинг составных меток:** автоматическая обработка нескольких тегов через разделитель (символ `;`).

---

### 🔄 Поток данных (Data Flow Architecture)

```mermaid
graph TD
    A[Пользовательский ввод] -->|Событие @blur / @input| B[AccountForm.vue]
    B -->|Валидация полей| C{Данные валидны?}
    C -->|Да| D[Pinia Store: accounts.ts]
    C -->|Нет| E[Рендер подсветки ошибок]
    D -->|Автоматическая запись| F[(Browser localStorage)]
    F -->|Инициализация стейта| D
    D -->|Реактивный computed| B
