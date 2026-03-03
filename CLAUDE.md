# ResearchGraph
<!-- Projekt-Identität und Langzeit-Vision: siehe VISION.md -->

Bitte SO TOKENSPAREND WIE MÖGLICH SEIN

## Hard rules
0. IF THERE ARE ANY UNCERTANTIES OR U NEED MORE INFO: ASK ME
1. Always update `thesis_data.json` after every change — it is the source of truth.
2. Ask before assuming experimental outcomes or relationships not explicitly stated.
3. Never delete nodes — mark them `status: "abandoned"` if dropped.
4. Output file is `overview.html` (single self-contained file, no external dependencies).
5. Kontext files (GenBank, Excel, docx) are in `Kontext/`.

## Umgang mit großen Dateien (allgemeine Regel)
- NIEMALS `Read` ohne `offset`/`limit` auf Dateien >300 Zeilen anwenden — sprengt den Kontext und kostet unnötig Tokens.
- Vorgehen: erst `Grep` zur Lokalisierung des relevanten Blocks, dann gezieltes `Read` mit `offset`/`limit`.
- NIEMALS `Write` zum Überschreiben einer bestehenden Datei nutzen — immer `Edit` für gezielte Änderungen. `Write` auf overview.html (~1000 Zeilen) löst das 32k-Token-Limit aus.

## Metaplaner-Sync
After significant changes (new features, architecture changes, milestones), update the project summary in:
`C:\Users\Dominik\.claude\projects\F--CLAUDECODE-Projects-Metaplaner\memory\project-summaries.md`
Keep the ResearchGraph section current: status, recent changes, open TODOs.

## Dominiks Labor-Struktur (Backup)
- `user_state_backup.json` enthält den aktuellen Stand aus Dominiks Browser (altes Format, pre-unified).
- Bei Migration als neue Defaults: diese Datei als Referenz verwenden, abandoned Test-Goals (j, papya, etc.) weglassen.

## Umgang mit overview.html (große Datei ~1418 Zeilen)
- Bekannte Zeilen-Ranges: CSS: 6–345, HTML: 347–409, Data (_DG+_DE): 413–510, Load/Save/Migration: 512–575, Inline-Linking+TagManager: 577–730, buildRoadmap: 732–860, Cards+DnD: 862–920, renderDetail: 1070–1220, AddModal: 1240–1340.
- Bei Änderungen immer nur den betroffenen Block lesen, nie die ganze Datei.
