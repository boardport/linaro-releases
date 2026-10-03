# 📋 BoardPort — Каталог плат и архивных релизов

Данный документ представляет собой подробный технический справочник по отладочным платам, одноплатным
компьютерам (SBC) и робототехническим платформам, поддерживаемым архивным зеркалом Linaro в рамках проекта **[BoardPort](https://github.com/boardport)**.

Здесь собраны спецификации оборудования, официальные и архивные ссылки производителей, матрица сохранности релизов
с наглядными emoji-статусами, конфигурации аппаратных переключателей загрузки и призыв к сообществу по сохранению недостающих образов.

---

## 📌 Обозначения статусов релизов

| Статус | Значение |
| :---: | :--- |
| ✅ **Сохранено** | 100% полный релиз — проверен и опубликован в [GitHub Releases](https://github.com/boardport/linaro-releases/releases). |
| ⚠️ **Частично** | Загрузочная цепочка и ядро сохранены — тяжелый образ rootfs отсутствует в веб-архивах. |
| 🔍 **Разыскивается** | Релиз отсутствует в публичных веб-архивах; принимаются архивы от сообщества. |
| 🔄 **Совместимо** | Аппаратно совместимо с набором загрузчиков и прошивок родительской платы. |

---

## 🧩 Платформы Qualcomm Snapdragon (Ключевой приоритет)

### 1. DragonBoard 410c (DB410c)

- **Процессор (SoC):** Qualcomm Snapdragon 410 (APQ8016E)
- **CPU:** 4 ядра ARM Cortex-A53 с частотой до 1.2 ГГц (ARMv8-A 64-bit)
- **GPU:** Qualcomm Adreno 306 @ 400 МГц
- **DSP:** Qualcomm Hexagon QDSP6 v5
- **Память и накопитель:** 1 ГБ / 2 ГБ LPDDR3 @ 533 МГц, 8 ГБ eMMC 4.51, слот карт MicroSD
- **Стандарт:** 96Boards Consumer Edition (CE)

#### Официальные и архивные ссылки

- **Страница 96Boards:** [96boards.org/product/dragonboard410c](https://www.96boards.org/product/dragonboard410c/) *(Архив / EOL)*
- **Страница Arrow Electronics:** [arrow.com/.../dragonboard410c](https://www.arrow.com/en/products/dragonboard410c/) *(Снята с производства)*
- **Qualcomm Developer Network:** [developer.qualcomm.com/hardware/dragonboard-410c](https://developer.qualcomm.com/hardware/dragonboard-410c) *(Архив)*
- **Сервер релизов Linaro:** `releases.linaro.org/96boards/dragonboard410c/` *(Сервер отключен)*
- **Документация Linaro:** [Linaro DB410c Wiki](https://web.archive.org/web/20200806085521/https://wiki.linaro.org/Boards/DragonBoard410c) *(Wayback Machine)*

> [!NOTE]
> **Статус поддержки:** Официально снята с производства (End-of-Life). Прямые серверы загрузки Linaro и Qualcomm отключены.

#### Сводная таблица релизов

| Название релиза | Сборка Linaro | Состав и компоненты | Релиз BoardPort | Статус |
| :--- | :--- | :--- | :--- | :---: |
| **Linaro Rescue 21.12** | Сборка 176 | SBL1, TrustZone, Hyp, RPM, LK Fastboot, Firehose EDL 9008 | [`db410c-rescue-21.12`](https://github.com/boardport/linaro-releases/releases/tag/db410c-rescue-21.12) | ✅ Сохранено |
| **Linaro Debian 21.12** | Сборка 1125 | Ядро 5.15.0 LTS, DTB, initramfs, Fastboot-образы boot и инсталлера | [`db410c-debian-21.12`](https://github.com/boardport/linaro-releases/releases/tag/db410c-debian-21.12) | ⚠️ Частично* |
| **Qualcomm BSP Firmware** | r1036.1 (Latest) | Adreno 306 GPU, Venus, микрокоды Wi-Fi/BT WCN3660 | [`db410c-firmware-r1036`](https://github.com/boardport/linaro-releases/releases/tag/db410c-firmware-r1036) | ✅ Сохранено |
| **Qualcomm BSP Firmware** | r1034.2.1 | Adreno 306, DSP, калибровка WCN3660 | [`db410c-firmware-r1034`](https://github.com/boardport/linaro-releases/releases/tag/db410c-firmware-r1034) | ✅ Сохранено |
| **Qualcomm BSP Firmware** | r1032.1 | Adreno 306, DSP, калибровка WCN3660 | [`db410c-firmware-r1032`](https://github.com/boardport/linaro-releases/releases/tag/db410c-firmware-r1032) | ✅ Сохранено |
| **Linaro Rescue 17.09** | Сборка 88 | Комплекты загрузчиков под Linux и Android, EDL 9008 | [`db410c-rescue-17.09`](https://github.com/boardport/linaro-releases/releases/tag/db410c-rescue-17.09) | ✅ Сохранено |
| **Qualcomm Boot Tools** | 2024.05 | Компилятор XML-партиций (`ptool.py`), генератор SD-rescue (`mksdcard`) | [`db410c-boot-tools`](https://github.com/boardport/linaro-releases/releases/tag/db410c-boot-tools) | ✅ Сохранено |
| **Linaro Debian 16.06** | Сборка 110 | Ядро 4.4.9, DTB, `dt.img`, initramfs, `.config` | [`db410c-debian-16.06`](https://github.com/boardport/linaro-releases/releases/tag/db410c-debian-16.06) | ⚠️ Частично* |
| **Qualcomm Android BSP** | 16.03 | LK Fastboot, ramdisks Android 5.1.1, дерево устройств, манифесты | [`db410c-android-16.03`](https://github.com/boardport/linaro-releases/releases/tag/db410c-android-16.03) | ⚠️ Частично* |

*\* Примечание: Загрузочная цепочка сохранена на 100%. Тяжелые образы графического интерфейса rootfs не сохранились в веб-архивах. Подробнее в разделе [Призыв к сохранению артефактов](#-призыв-к-сохранению-артефактов).*

#### Аппаратный переключатель загрузки (DIP Switch S6)

На нижней стороне платы DragonBoard 410c расположен 4-позиционный переключатель **S6**:

| Переключатель | Назначение | Положение: OFF (По умолчанию) | Положение: ON |
| :---: | :--- | :--- | :--- |
| **1** | USB Host / Device | Режим USB Host (активен Type-A) | Режим USB Device (активен Micro-USB OTG) |
| **2** | Выбор накопителя | Загрузка со встроенной eMMC | **Загрузка с MicroSD карты (SD Rescue)** |
| **3** | Выбор режима | Обычная загрузка ОС | Принудительный старт в Fastboot |
| **4** | Сервисный режим | Стандартная работа | Аварийный режим Qualcomm EDL 9008 |

---

### 2. DragonBoard 820c (DB820c)

- **Процессор (SoC):** Qualcomm Snapdragon 820 (APQ8096)
- **CPU:** 4 ядра Qualcomm Kryo 64-bit (2x 2.15 ГГц + 2x 1.6 ГГц)
- **GPU:** Qualcomm Adreno 530 @ 624 МГц
- **DSP:** Qualcomm Hexagon 680 DSP (с поддержкой HVX)
- **Память и накопитель:** 3 ГБ LPDDR4 @ 1866 МГц, 32 ГБ UFS 2.0 gear 3, слот MicroSD
- **Стандарт:** 96Boards Consumer Edition (CE)

#### Официальные и архивные ссылки

- **Страница 96Boards:** [96boards.org/product/dragonboard820c](https://www.96boards.org/product/dragonboard820c/) *(Архив)*
- **Страница Arrow Electronics:** [arrow.com/.../dragonboard820c](https://www.arrow.com/en/products/dragonboard820c/) *(Снята с производства)*
- **Сервер релизов Linaro:** `releases.linaro.org/96boards/dragonboard820c/` *(Сервер отключен)*
- **Зеркало валидации:** `images.validation.linaro.org/snapshots.linaro.org/96boards/dragonboard820c/`

#### Сводная таблица релизов

| Название релиза | Сборка Linaro | Состав и компоненты | Релиз BoardPort | Статус |
| :--- | :--- | :--- | :--- | :---: |
| **Linaro Debian 21.12** | Сборка 869 | Ядро 5.15.0 LTS, DTB, initramfs, Fastboot-образ boot | [`db820c-debian-21.12`](https://github.com/boardport/linaro-releases/releases/tag/db820c-debian-21.12) | ⚠️ Частично* |
| **Rescue & UFS Bootloader** | Сборка 83636 | XBL, TrustZone, Hyp, Little Kernel, Firehose 9008, GPT LUN 0–5 | [`db820c-rescue-83636`](https://github.com/boardport/linaro-releases/releases/tag/db820c-rescue-83636) | ✅ Сохранено |
| **Qualcomm BSP Firmware** | r01700.1 | Adreno 530 GPU, декодер Venus, Hexagon DSP, калибровка WLAN | [`db820c-firmware-r01700`](https://github.com/boardport/linaro-releases/releases/tag/db820c-firmware-r01700) | ✅ Сохранено |

#### Режимы загрузки

- **Режим Fastboot:** Удерживайте кнопку **S4 (Vol-)** при подключении блока питания 12В.
- **Аварийный режим EDL 9008:** Программатор `prog_ufs_firehose_8996_ddr.elf` доступен в релизе `db820c-rescue-83636`.

---

### 3. DragonBoard 845c / Qualcomm Robotics RB3

- **Процессор (SoC):** Qualcomm Snapdragon 845 (SDA845)
- **CPU:** 8 ядер Qualcomm Kryo 385 (4x 2.8 ГГц Gold + 4x 1.8 ГГц Silver)
- **GPU:** Qualcomm Adreno 630 @ 710 МГц
- **DSP:** Qualcomm Hexagon 685 DSP с расширениями HVX
- **Память и накопитель:** 4 ГБ LPDDR4x, 64 ГБ UFS 2.1, слот MicroSD
- **Стандарт:** 96Boards Consumer Edition (CE)

#### Официальные и архивные ссылки

- **Страница 96Boards:** [96boards.org/product/rb3-platform](https://www.96boards.org/product/rb3-platform/) *(Архив)*
- **Thundercomm RB3:** [thundercomm.com/.../qualcomm-robotics-rb3](https://www.thundercomm.com/product/qualcomm-robotics-rb3-platform/)
- **Зеркало Linaro Validation:** `images.validation.linaro.org/.../dragonboard845c/`

#### Сводная таблица релизов

| Название релиза | Сборка Linaro | Состав и компоненты | Релиз BoardPort | Статус |
| :--- | :--- | :--- | :--- | :---: |
| **Qualcomm BSP Firmware** | v4 | Adreno 630 GPU, Hexagon 685 DSP, Venus, Wi-Fi/BT WCN3990 | [`db845c-firmware-v4`](https://github.com/boardport/linaro-releases/releases/tag/db845c-firmware-v4) | ✅ Сохранено |
| **Rescue & UFS Bootloader** | Сборка 101 | XBL, TrustZone, Hyp, QUPv3, Firehose EDL 9008, GPT LUN 0–5 | [`db845c-rescue-101`](https://github.com/boardport/linaro-releases/releases/tag/db845c-rescue-101) | ✅ Сохранено |
| **Linux RPB Console** | Сборка 169 | Образ boot Fastboot с ядром 5.1 + OpenEmbedded rootfs (145 МБ) | [`db845c-linux-rpb-169`](https://github.com/boardport/linaro-releases/releases/tag/db845c-linux-rpb-169) | ✅ Сохранено |

---

### 4. Qualcomm Robotics RB5 (QRB5165)

- **Процессор (SoC):** Qualcomm QRB5165 / SM8250
- **CPU:** 8 ядер Qualcomm Kryo 585 (1x 2.84 ГГц + 3x 2.42 ГГц + 4x 1.8 ГГц)
- **GPU:** Qualcomm Adreno 650
- **DSP:** Qualcomm Hexagon 698 DSP с двойным HVX и NPU
- **Память и накопитель:** 8 ГБ LPDDR5, 128 ГБ UFS 3.0, слот MicroSD

#### Официальные и архивные ссылки

- **Страница 96Boards:** [96boards.org/product/rb5-platform](https://www.96boards.org/product/rb5-platform/)
- **Thundercomm RB5:** [thundercomm.com/.../qualcomm-robotics-rb5](https://www.thundercomm.com/product/qualcomm-robotics-rb5-development-kit/)
- **Зеркало Linaro QCOM LT:** `images.validation.linaro.org/.../qrb5165-rb5/`

#### Сводная таблица релизов

| Название релиза | Сборка Linaro | Состав и компоненты | Релиз BoardPort | Статус |
| :--- | :--- | :--- | :--- | :---: |
| **Rescue & UFS Bootloader** | Сборка 27 | XBL, TrustZone, Hyp, ABL Fastboot, Firehose 9008, GPT LUN 0–5 | [`rb5-rescue-27`](https://github.com/boardport/linaro-releases/releases/tag/rb5-rescue-27) | ✅ Сохранено |
| **Linaro QCOM LT Linux** | Ядро 5.13.9 (708) | Официальный загрузочный Fastboot-образ ядра 5.13.9 | [`rb5-linux-5.13`](https://github.com/boardport/linaro-releases/releases/tag/rb5-linux-5.13) | ✅ Сохранено |

---

### 5. Qualcomm Robotics RB2 (QRB4210)

- **Процессор (SoC):** Qualcomm QRB4210 / Qualcomm Dragonwing
- **CPU:** 8 ядер Qualcomm Kryo 260
- **GPU:** Qualcomm Adreno 610
- **Память и накопитель:** 4 ГБ LPDDR4x, 64 ГБ eMMC 5.1

#### Сводная таблица релизов

| Название релиза | Сборка Linaro | Состав и компоненты | Релиз BoardPort | Статус |
| :--- | :--- | :--- | :--- | :---: |
| **Linaro Debian Bookworm** | Сборка 58915 | Fastboot-образ boot с ядром, DTB QRB4210 и initrd Debian Bookworm | [`rb2-debian-bookworm`](https://github.com/boardport/linaro-releases/releases/tag/rb2-debian-bookworm) | ✅ Сохранено |

---

### 6. Inforce IFC6410 / IFC6410Plus

- **Процессор (SoC):** Qualcomm Snapdragon 600 (APQ8064 / APQ8064-1AA)
- **CPU:** 4 ядра Qualcomm Krait 300 с частотой до 1.7 ГГц (ARMv7-A 32-bit)
- **GPU:** Qualcomm Adreno 320 @ 400 МГц
- **DSP:** Qualcomm Hexagon QDSP6 v4
- **Память и накопитель:** 2 ГБ DDR3, 4 ГБ eMMC, порт SATA 3Gbps, слот MicroSD

#### Официальные и архивные ссылки

- **Penguin Edge / Inforce:** [Одноплатный компьютер IFC6410 Plus](https://www.penguinsolutions.com/edge-computing/products/single-board-computers/ifc6410-plus/)
  *(Архив)*
- **Каталог Linaro Snapdragon:** `releases.linaro.org/debian/boards/snapdragon/16.02/` *(Сервер отключен)*

#### Сводная таблица релизов

| Название релиза | Сборка Linaro | Состав и компоненты | Релиз BoardPort | Статус |
| :--- | :--- | :--- | :--- | :---: |
| **Linaro Debian 16.02** | Ядро 4.4 LTS | Образы boot под eMMC, SATA (`sda1`), SD, DTB, модули, deb-пакеты | [`ifc6410-debian-16.02`](https://github.com/boardport/linaro-releases/releases/tag/ifc6410-debian-16.02) | ✅ Сохранено |
| **Qualcomm BSP & eMMC Rescue** | r16.02 / eMMC | Файлы `/lib/firmware` (Adreno 320, Wi-Fi, Venus) + посекторные дампы eMMC | [`ifc6410-firmware-rescue`](https://github.com/boardport/linaro-releases/releases/tag/ifc6410-firmware-rescue) | ✅ Сохранено |
| **Linux Kernel 5.15 LTS** | Headless LTS | Современные образы ядра 5.15 LTS (eMMC, SATA, SD), модули, cgroups | [`ifc6410-linux-5.15`](https://github.com/boardport/linaro-releases/releases/tag/ifc6410-linux-5.15) | ✅ Сохранено |

---

### 7. Inforce IFC6309

- **Процессор (SoC):** Qualcomm Snapdragon 410E (APQ8016E)
- **Архитектура:** ARM64 (4x Cortex-A53)
- **Аппаратная совместимость:** 100% совместимость со стеком загрузчиков и прошивками DragonBoard 410c.
- **Рекомендуемые релизы:** Используйте [`db410c-rescue-21.12`](https://github.com/boardport/linaro-releases/releases/tag/db410c-rescue-21.12)
  и [`db410c-firmware-r1036`](https://github.com/boardport/linaro-releases/releases/tag/db410c-firmware-r1036).
- **Статус:** 🔄 **Совместимо**

---

### 8. Inforce IFC6540 / IFC6560

- **Процессор (SoC):** Qualcomm Snapdragon 805 (APQ8084) / Snapdragon 660 (SDA660)
- **Статус:** 🔍 **Разыскивается** — Принимаются дампы прошивок и оригинальные сборки Linaro от сообщества.

---

## 🏛️ Исторические платы 96Boards (Вторая очередь)

| Плата | Процессор / Вендор | Архитектура | Ключевые релизы | Статус |
| :--- | :--- | :--- | :--- | :---: |
| **HiKey 620** | HiSilicon Kirin 620 | ARM64 (8x A53) | Linaro Debian, AOSP Reference, UEFI Firmware | 🔍 По запросу |
| **HiKey 960** | HiSilicon Kirin 960 | ARM64 (4x A73 + 4x A53) | Linaro Debian, AOSP Builds, UEFI Firmware | 🔍 По запросу |
| **Bubblegum-96** | Actions Semi S900 | ARM64 (4x A53) | Linaro Debian Desktop/Minimal, Android | 🔍 По запросу |
| **Rock960** | Rockchip RK3399 | ARM64 (2x A72 + 4x A53) | Linaro Debian, RPB, Android 7.1/8.1 | 🔍 По запросу |
| **MediaTek X20** | MediaTek Helio X20 | ARM64 (10-core Tri-Cluster) | Linaro Debian, Android Marshmallow | 🔍 По запросу |

---

## 🤝 Призыв к сохранению артефактов

### Разыскиваемые файлы и образы

Если у вас сохранились локальные копии оригинальных файлов с серверов `releases.linaro.org` или `builds.96boards.org`,
мы будем признательны за помощь в сохранении недостающих образов:

1. **DragonBoard 410c:**
   - `linaro-sid-alip-dragonboard-410c-1125.img.gz` (~1.4 ГБ)
   - `linaro-jessie-alip-qcom-snapdragon-arm64-20160630-110.img.gz` (~1.1 ГБ)
   - Официальный образ Qualcomm Android 16.03 `system.img` (~800 МБ)
2. **DragonBoard 820c:**
   - `linaro-sid-alip-dragonboard-820c-869.img.gz` (~1.2 ГБ)
3. **Inforce 6540 (APQ8084):**
   - Оригинальные BSP-пакеты Inforce и загрузчики Fastboot.

### Как передать файлы

- **Создайте Issue:** Воспользуйтесь [Шаблоном запроса релиза](./.github/ISSUE_TEMPLATE/request_release.md).
- **Верификация:** При отправке укажите имя файла, точный размер в байтах, контрольные суммы MD5 и SHA256.
