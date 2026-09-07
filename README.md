# SOC Home Lab

Домашняя лаборатория для практического изучения работы SOC / Blue Team: мониторинга событий информационной безопасности, анализа журналов, расследования инцидентов и разработки правил обнаружения с использованием Wazuh SIEM.

Лаборатория используется для воспроизведения контролируемых событий информационной безопасности в изолированной среде, сбора телеметрии с Windows и Linux систем, анализа срабатываний SIEM и документирования процесса расследования с позиции аналитика SOC L1.

## Цели проекта

Основные задачи лаборатории:

- сбор событий информационной безопасности с Windows и Linux систем;
- мониторинг и анализ срабатываний в Wazuh SIEM;
- проведение первичного triage событий и инцидентов;
- анализ и корреляция связанных событий;
- сопоставление обнаруженной активности с MITRE ATT&CK;
- определение True Positive / False Positive;
- разработка и тестирование базовых правил Sigma и Wazuh;
- документирование расследований;
- подготовка данных, необходимых для эскалации инцидента на SOC L2;

## Архитектура лаборатории

Лаборатория состоит из пяти виртуальных машин.

| Хост | Операционная система | Роль | Сетевой IPv4 |
| --- | --- | --- | --- |
| `deb_serv` | Debian Server | SIEM endpoint  | 192.168.62.10/24 |
| `kali-attacker` | Kali | attacker | 192.168.62.20/24 |
| `ubuntu-serv` | Ubuntu Server | SIEM server | 192.168.62.30/24 |
| `win11` | Windows 11 | SIEM endpoint / AD DC endpoint | 192.168.62.40/24 |
| `dc01` | Windows Server 2022 | SIEM endpoint / AD DC server | 192.168.62.50/24 |

## Event triage

Результаты event triage находится в каталоге [`event_triage/`](event_triage/).

## Расследование события

Отчет проведенного расследования находится в каталоге [`investigation_report/`](investigation_report/).

## Эскалация события

Материалы, подготовленные для передачи в SOC L2 в рамках эскалации инцидента, размещены в каталоге [`escalation_report/`](escalation_report/).

## Wazuh rules

Созданные правила детектирования Wazuh находятся в каталоге [`wazuh_rules/`](wazuh_rules/).

## Sigma rules

Созданные правила детектирования Sigma находятся в каталоге [`sigma_rules/`](sigma_rules/).

## Sysmon rules

Созданные правила детектирования Sysmon находятся в каталоге [`sysmon_rules/`](sysmon_rules/).

## Структура репозитория
```text
SOC_Home_Lab/
│
├── README.md
│
├── event_triage/
│   ├── dc01-User_Add_To_Admin_Privileged_AD.md
│   ├── deb_serv-Create_Account_Local_Account.md
│   ├── deb_serv-SSH_Bruteforce_Complete.md
│   ├── deb_serv-User_Authentication_Failure.md
│   ├── win11-Disable_Defende_of_PowerShelr.md
│   └── win11-PowerShell_Execution_With_Encoded_Command.md
│
├── investigation_report/
│   └── deb_serv-Create_Account_Local_Account.md
│
├── escalation_report/
│   ├── deb_serv-Create_Account_Local_Account.md
│   ├── deb_serv-SSH_Bruteforce_Complete.md
│   └── win11-PowerShell_Execution_With_Encoded_Command.md
│
├── wazuh_rules/
│   ├── dc01-User_Add_To_Admin_Privileged_AD.xml
│   ├── deb_serv-Create_Account_Local_Account.xml
│   ├── disable_92008-PowerShell_Command.xml
│   ├── win11-Disable_Defende_of_PowerShelr.xml
│   └── win11-PowerShell_Execution_With_Encoded_Command.xml
│
├── sigma_rules/
│   └── win11-Disable_Defende_of_PowerShelr.yml
│
├── sysmon_rules/
│   └── Powershell_Process_Creation.xml
│
└── pictures/ - не для изучения репозетория
```


