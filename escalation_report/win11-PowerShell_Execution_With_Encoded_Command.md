## Case Summary

| Параметр | Значение |
|---|---|
| Host | `win11` |
| Host IP | `192.168.62.40` |
| User | `CORP\Administrator` |
| Process | `powershell.exe` |
| Parent Process | `powershell.exe` |
| Integrity Level | `High` |
| Source | `Sysmon Event ID 1` / `EventChannel` |
| Wazuh Rule | `100003` |
| Severity | `13` |
| L1 Verdict | True Positive |
| Escalation Reason | Запуск PowerShell с `-EncodedCommand` и скрытым окном |
| MITRE ATT&CK | T1059.001 - PowerShell; T1027.010 - Command Obfuscation |
| Время события | `2026-09-06 20:40:45.205` |

---

## L1 Подтвердил следующие факты:

- на узле `win11` был создан процесс `powershell.exe`;
- процесс запущен пользователем `CORP\Administrator`;
- командная строка содержит параметр `-EncodedCommand`;
- дополнительно использовались параметры `-NoProfile` и `-WindowStyle Hidden`;
- родительским процессом также являлся `powershell.exe`;
- событие зарегистрировано Sysmon как `Event ID 1 — Process Create`;
- пользовательское правило Wazuh `100003` сработало корректно;
- назначение закодированной команды на этапе L1 не установлено;
- факт компрометации узла на этапе L1 не подтвержден.

Исходное событие:

```text
"C:\WINDOWS\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -WindowStyle Hidden -EncodedCommand VwByAGkAdABlAC0ATwB1AHQAcAB1AHQAIAAiAHkAbwAgAHcAbwByAGwAZAAhACIA
