## Filepath Analysis

| Filepath | Description |
|----------|-------------|
| `C:\` | System drive; common target for persistence mechanisms |
| `C:\Users\Public` | Enables cross-user access of detonated adversary tools |
| `C:\Users\Public\Public Downloads` | High-traffic directory that often evades strict monitoring |
| `C:\Windows\Temp\` | Temporary directory used for ephemeral payloads |
| `C:\ProgramData\` | Writable system path used for stealth persistence |

## Filename Heuristic Indicators

| Indicator Type | Example | Description |
|----------------|---------|-------------|
| Double extensions | `invoice.pdf.exe` | Leverages default Windows settings that hide file extensions |
| System binary impersonation | `scvhost.exe` | Abuses user familiarity with core system processes; defenders should allowlist legitimate locations rather than standalone filenames |
| High-entropy strings | `jh8F21.exe` | Suggests automated packing or polymorphic generation, commonly used in high-churn phishing operations |
| Masquerading | `backup-2300.exe` | Blends with routine files to reduce suspicion; single character substitutions can bypass detection while appearing visually legitimate |
