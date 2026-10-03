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

Ниже представлен реестр старых платформ, подлежащих архивному зеркалированию:

### Платформы Qualcomm Snapdragon (Ключевой приоритет)

| Плата | Процессор (SoC) | Архитектура | Категории доступных релизов Linaro | Тег релиза / Статус |
| :--- | :--- | :--- | :--- | :--- |
| **DragonBoard 410c (DB410c)** | Snapdragon 410 (APQ8016E) | ARM64 (4x A53) | Debian (15.06–18.01), RPB, Android (5.1–8.1), Rescue, Win10 IoT | Запланирован (`db410c-*`) |
| **DragonBoard 820c (DB820c)** | Snapdragon 820 (APQ8096) | ARM64 (4x Kryo) | Debian (16.06–18.01), RPB, Android (6.0–8.0), Загрузчики | Запланирован (`db820c-*`) |
| **DragonBoard 845c / RB3** | Snapdragon 845 (SDA845) | ARM64 (8x Kryo) | Debian, Linux BSP, Android AOSP snapshots, Robotics | Запланирован (`db845c-*`) |
| **Qualcomm Robotics RB5** | QRB5165 (SM8250) | ARM64 (8x Kryo) | Linaro Ubuntu BSP, Poky / Yocto, Fastboot Recovery | Запланирован (`rb5-*`) |
| **Inforce 6309 (IFC6309)** | Snapdragon 410E (APQ8016E) | ARM64 (4x A53) | Linaro Linux BSP, Android BSP, Rescue Bootloader | Запланирован (`ifc6309-*`) |
| **Inforce 6410 / 6410Plus** | Snapdragon 600 (APQ8064) | ARMv7 (4x Krait) | Linaro ALIP, Ubuntu, Android Releases, Fastboot Blobs | Запланирован (`ifc6410-*`) |
| **Inforce 6540 / 6560** | Snapdragon 805 / SD660 | ARMv7 / ARM64 | Linaro Linux BSP, Android BSP, Загрузчики | Запланирован (`ifc6540-*`) |

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
