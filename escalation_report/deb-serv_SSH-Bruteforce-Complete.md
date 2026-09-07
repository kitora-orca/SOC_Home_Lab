## Case Summary

| Параметр | Значение |
|---|---|
| Host | `debian-server` |
| Host IP | `192.168.62.10` |
| Source IP | `192.168.62.20` |
| Target User | `orca` |
| Service | `sshd` |
| Wazuh Rule | `40112` |
| Severity | `12` |
| L1 Verdict | True Positive |
| Escalation Reason | Successful SSH login after multiple authentication failures |
| MITRE ATT&CK | T1110.001 - Brute Force: Password Guessing; T1078.001 - Valid Accounts: Default Accounts |
| Time | Sep 04 13:24:33 |

---

## L1 Подтвердил следующие факты:

- зафиксирован успешный SSH-вход под учетной записью `orca`;
- источник соединения — `192.168.62.20`;
- успешному входу предшествовали множественные неуспешные попытки аутентификации;
- Wazuh корректно скоррелировал события по правилу `40112`;
- событие является True Positive;
- факт компрометации учетной записи на этапе L1 не подтвержден.

Исходное событие:

```text
Sep 04 13:24:33 debian-server sshd[13457]: Accepted password for orca from 192.168.62.20 port 54498 ssh2
