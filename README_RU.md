# 📦 BoardPort — Linaro Releases

[![Лицензия: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](./LICENSE)
[![Проект: BoardPort](https://img.shields.io/badge/Project-BoardPort-green.svg)](https://github.com/boardport)
[![Хранилище: GitHub Releases](https://img.shields.io/badge/Storage-GitHub%20Releases-blueviolet.svg)](https://github.com/boardport/linaro-releases/releases)

Надежное архивное зеркало официальных релизов Linaro, пакетов поддержки плат (BSP), загрузчиков и rescue-дампов для отладочных плат.

Этот репозиторий является частью экосистемы **[BoardPort](https://github.com/boardport)**, нацеленной на спасение и вторую жизнь аппаратного
обеспечения на базе процессоров Qualcomm Snapdragon: адаптацию ванильного ядра Linux (Mainline Kernel), открытых загрузчиков и актуальных дистрибутивов.

> 🤖 **Инструкция для ИИ-ассистентов:** Автономные ИИ-агенты и LLM-помощники обязаны ознакомиться с правилами проекта в
> [AGENTS_RU.md](./AGENTS_RU.md) перед выполнением любых задач в данном репозитории.

---

## 🎯 О проекте

Исторически консорциум Linaro выступал ключевым центром разработки открытого ПО для ARM-платформ, отвечая за поддержку ванильного ядра,
дистрибутивов Linux (Debian, OpenEmbedded) и эталонных сборок AOSP для плат стандарта 96Boards — в первую очередь на чипсетах Qualcomm Snapdragon.

После реорганизации и отключения серверов `releases.linaro.org` и `builds.96boards.org` доступ ко многим критически важным прошивкам,
эталонным таблицам разделов, пакетам восстановления (rescue) и базовым образам ОС оказался нарушен. Архивные копии в Wayback Machine медленны,
нестабильны и подвержены рискам потери данных.

**Задачи репозитория:**

1. **Создание надежного долгосрочного зеркала:** Сохранение проверенных релизов Linaro для старых одноплатных компьютеров (SBC) и отладочных плат.
2. **Гарантия целостности данных:** Каждый образ и архив сопровождается оригинальными контрольными суммами SHA256 и манифестом `manifest.json`.
3. **Интеграция с экосистемой BoardPort:** Предоставление проверенных загрузчиков (`sbl1`, `tz`, `hyp`, `rpm`, `lk`), разметки партиций
   (`rawprogram0.xml`) и rescue-пакетов, необходимых инструментам вроде **[EDL Container](https://github.com/boardport/edl-container)** для
   низкоуровневого восстановления и портирования.

---

## 🏛️ Модель хранения и публикации релизов

Для поддержания легковесности и чистоты Git-дерева:

- **В Git хранятся только метаданные:** Документация, реестр поддерживаемых плат, правила и шаблоны задач.
- **Все тяжелые артефакты — в GitHub Releases:** Бинарные архивы (`.tar.gz`, `.tar.xz`, `.zip`), полные образы (`.img`) и rescue-пакеты
  публикуются исключительно в **[GitHub Releases](https://github.com/boardport/linaro-releases/releases)**.
- **Изолированная рабочая область `tmp/`:** Процессы загрузки, распаковки и вычисления хэшей происходят в локальной директории `tmp/`,
  исключенной из Git и индексации ИИ.
- **Комплект каждого релиза:**
  - Сжатые архивы прошивки и образы ОС.
  - Индивидуальные файлы контрольных сумм `.sha256`.
  - Машинно-читаемый `manifest.json`.
  - Двуязычное описание релиза (`[RU]` / `[EN]`) со сводной таблицей файлов и инструкциями по прошивке.

---

## 🧩 Каталог поддерживаемых плат

Ниже представлен реестр старых платформ, подлежащих архивному зеркалированию.

> 📖 **Полный каталог оборудования и релизов:** Подробные аппаратные характеристики плат, ссылки на официальные и архивные ресурсы,
> конфигурацию сервисных переключателей и матрицу релизов смотрите в **[BOARDS_RU.md](./BOARDS_RU.md)**.

### Платформы Qualcomm Snapdragon (Ключевой приоритет)

| Плата | Процессор (SoC) | Архитектура | Категории доступных релизов Linaro | Опубликованные релизы | Статус |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **DragonBoard 410c (DB410c)** | Snapdragon 410 (APQ8016E) | ARM64 (4x A53) | Debian 21.12 / 16.06, Android BSP 16.03, Прошивки (r1036, r1034, r1032), Rescue (21.12, 17.09), Boot Tools | [`db410c-rescue-21.12`](https://github.com/boardport/linaro-releases/releases/tag/db410c-rescue-21.12), [`db410c-debian-21.12`](https://github.com/boardport/linaro-releases/releases/tag/db410c-debian-21.12), [`db410c-firmware-r1036`](https://github.com/boardport/linaro-releases/releases/tag/db410c-firmware-r1036), [`db410c-firmware-r1034`](https://github.com/boardport/linaro-releases/releases/tag/db410c-firmware-r1034), [`db410c-firmware-r1032`](https://github.com/boardport/linaro-releases/releases/tag/db410c-firmware-r1032), [`db410c-rescue-17.09`](https://github.com/boardport/linaro-releases/releases/tag/db410c-rescue-17.09), [`db410c-boot-tools`](https://github.com/boardport/linaro-releases/releases/tag/db410c-boot-tools), [`db410c-debian-16.06`](https://github.com/boardport/linaro-releases/releases/tag/db410c-debian-16.06), [`db410c-android-16.03`](https://github.com/boardport/linaro-releases/releases/tag/db410c-android-16.03) | ✅ Завершен |
| **DragonBoard 820c (DB820c)** | Snapdragon 820 (APQ8096) | ARM64 (4x Kryo) | Linaro Debian 21.12 (ядро 5.15), UFS Bootloader & Rescue сборка 83636, Qualcomm BSP Firmware r01700.1 | [`db820c-debian-21.12`](https://github.com/boardport/linaro-releases/releases/tag/db820c-debian-21.12), [`db820c-rescue-83636`](https://github.com/boardport/linaro-releases/releases/tag/db820c-rescue-83636), [`db820c-firmware-r01700`](https://github.com/boardport/linaro-releases/releases/tag/db820c-firmware-r01700) | ✅ Завершен |
| **DragonBoard 845c / RB3** | Snapdragon 845 (SDA845) | ARM64 (8x Kryo) | Qualcomm BSP Firmware v4, Linaro UFS Rescue сборка 101, Linux RPB Console сборка 169 (ядро 5.1) | [`db845c-firmware-v4`](https://github.com/boardport/linaro-releases/releases/tag/db845c-firmware-v4), [`db845c-rescue-101`](https://github.com/boardport/linaro-releases/releases/tag/db845c-rescue-101), [`db845c-linux-rpb-169`](https://github.com/boardport/linaro-releases/releases/tag/db845c-linux-rpb-169) | ✅ Завершен |
| **Qualcomm Robotics RB5** | QRB5165 (SM8250) | ARM64 (8x Kryo) | Linaro UFS Bootloader & Rescue сборка 27, QCOM LT Linux Kernel 5.13.9 Boot Image (сборка 708) | [`rb5-rescue-27`](https://github.com/boardport/linaro-releases/releases/tag/rb5-rescue-27), [`rb5-linux-5.13`](https://github.com/boardport/linaro-releases/releases/tag/rb5-linux-5.13) | ✅ Завершен |
| **Qualcomm Robotics RB2** | QRB4210 (Dragonwing) | ARM64 (8x Kryo) | Linaro QCOM LT Debian Bookworm arm64 Boot Image (сборка 58915) | [`rb2-debian-bookworm`](https://github.com/boardport/linaro-releases/releases/tag/rb2-debian-bookworm) | ✅ Завершен |
| **Inforce 6410 / 6410Plus** | Snapdragon 600 (APQ8064) | ARMv7 (4x Krait) | Linaro Debian 16.02 (ядро 4.4), Qualcomm BSP Firmware & eMMC Rescue, Linux Kernel 5.15 LTS (Headless) | [`ifc6410-debian-16.02`](https://github.com/boardport/linaro-releases/releases/tag/ifc6410-debian-16.02), [`ifc6410-firmware-rescue`](https://github.com/boardport/linaro-releases/releases/tag/ifc6410-firmware-rescue), [`ifc6410-linux-5.15`](https://github.com/boardport/linaro-releases/releases/tag/ifc6410-linux-5.15) | ✅ Завершен |
| **Inforce 6309 (IFC6309)** | Snapdragon 410E (APQ8016E) | ARM64 (4x A53) | Совместим со стеком загрузчиков и прошивками DragonBoard 410c | См. [`db410c-*`](https://github.com/boardport/linaro-releases/releases?q=db410c) | Совместим |

### Другие исторические платы 96Boards (Вторая очередь)

| Плата | Процессор / Вендор | Архитектура | Ключевые исторические релизы | Статус |
| :--- | :--- | :--- | :--- | :--- |
| **HiKey 620** | HiSilicon Kirin 620 | ARM64 (8x A53) | Linaro Debian, AOSP Reference, UEFI / ARM-TF | По запросу |
| **HiKey 960** | HiSilicon Kirin 960 | ARM64 (4x A73 + 4x A53) | Linaro Debian, AOSP Builds, UEFI Firmware | По запросу |
| **Bubblegum-96** | Actions Semi S900 | ARM64 (4x A53) | Linaro Debian Desktop/Minimal, Android | По запросу |
| **Rock960** | Rockchip RK3399 | ARM64 (2x A72 + 4x A53) | Linaro Debian, RPB, Android 7.1/8.1 | По запросу |
| **MediaTek X20** | MediaTek Helio X20 | ARM64 (10-ядерный кластер) | Linaro Debian, Android Marshmallow | По запросу |

---

## ⚡ Как скачивать и проверять релизы

### Вариант 1: С помощью GitHub CLI (`gh`)

```bash
# Просмотреть список опубликованных релизов
gh release list --repo boardport/linaro-releases

# Скачать все файлы конкретного релиза в директорию ./tmp
gh release download db410c-debian-18.01 --repo boardport/linaro-releases --dir ./tmp

# Проверить контрольные суммы SHA256
cd ./tmp && sha256sum -c *.sha256
```

### Вариант 2: Загрузка через веб-интерфейс GitHub

Перейдите в раздел **[GitHub Releases](https://github.com/boardport/linaro-releases/releases)**, выберите нужную плату и тег релиза,
затем скачайте образ (`.img.gz`, `.zip`) и соответствующий ему файл хэша `.sha256`.

---

## 🤝 Участие в проекте и поддержка

- **Запрос релиза для новой платы:** Создайте задачу по [шаблону запроса](./.github/ISSUE_TEMPLATE/request_release_ru.md).
- **Сообщение о поврежденном архиве:** Если хэш скачанного файла не совпадает, отправьте обращение по
  [шаблону поврежденного релиза](./.github/ISSUE_TEMPLATE/broken_release_ru.md).
- **Руководство контрибьютора:** Ознакомьтесь с [CONTRIBUTING_RU.md](./.github/CONTRIBUTING_RU.md) и
  [SECURITY_RU.md](./.github/SECURITY_RU.md).

---

## 📄 Лицензия и авторские права

- Метаданные, документация и индексы данного репозитория распространяются под лицензией **[MIT](./LICENSE)**.
- Авторские права на оригинальные сборки, ядра, загрузчики и бинарные прошивки принадлежат **Linaro Ltd.**,
  **Qualcomm Technologies, Inc.** и соответствующим авторам открытого ПО.
