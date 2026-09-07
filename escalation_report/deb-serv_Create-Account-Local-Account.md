## Case Summary

| Параметр | Значение |
|---|---|
| Host | `debian-server` |
| Host IP | `192.168.62.10` |
| Created User | `svc-backup` |
| Execution Context | `root` |
| Service / Source | `sudo` / `journald` |
| Wazuh Rule | `100001` |
| Severity | `8` |
| L1 Verdict | True Positive |
| Escalation Reason | Создание новой локальной учетной записи в привилегированном контексте |
| MITRE ATT&CK | T1136.001 - Create Account: Local Account |
| Время события | Sep 01 21:31:10 |
---

## L1 Подтвердил следующие факты:

- на узле `debian-server` была создана новая локальная учетная запись `svc-backup`;
- создание учетной записи выполнено в контексте `root`;
- событие зарегистрировано через `journald`;
- пользовательское правило `100001` сработало корректно;
- событие классифицировано как True Positive;
- легитимность создания учетной записи на этапе L1 не подтверждена;
- факт компрометации узла на этапе L1 не подтвержден.

Исходное событие:

```text
Sep 01 21:31:10 debian-server sudo[7766]: root : TTY=pts/1 ; PWD=/root ; USER=root ; COMMAND=/usr/sbin/useradd -m -s /bin/bash svc-backup
