# magiclauncher-content

Repozytorium zawierające konfigurację paczek **From Magic** w MagicLauncher.

## Zmiana URL repo

Jeśli to repo zostanie scalone z głównym, zmień jedną stałą w launcherze:

```typescript
// src/components/VersionsPage.tsx
const MAGIC_CONTENT_BASE = 'https://raw.githubusercontent.com/kserafin17/magiclauncher-content/main'
```

---

## Format `packs.json`

```json
{
  "schemaVersion": 1,
  "packs": [
    {
      "id": "unique-pack-id",
      "name": "Nazwa Paczki",
      "description": "Opis widoczny w launcherze.",
      "mcVersion": "1.20.1",
      "loader": "fabric",
      "loaderVersion": "0.16.5",
      "icon": "star",
      "color": "#A855F7",
      "image": "./magic-origins.png",
      "mods": [
        {
          "projectId": "P7dR8mSH",
          "name": "Fabric API",
          "versionId": "9956f70c"
        }
      ]
    }
  ]
}
```

### Pola

| Pole | Opis |
|---|---|
| `id` | Unikalny identyfikator paczki (używany jako nazwa folderu instancji) |
| `mcVersion` | Wersja Minecrafta, np. `"1.21.1"` |
| `loader` | `"fabric"` / `"forge"` / `"quilt"` / `"neoforge"` / `"vanilla"` |
| `loaderVersion` | Wersja loadera — puste string `""` = najnowsza dostępna |
| `icon` | Ikona: `box`, `star`, `sword`, `cloud`, `mountain`, `zap`, `rocket`, `shield`, `compass`, `map`, `trophy`, `hammer` |
| `color` | Kolor akcentu (hex), widoczny gdy nie ma obrazka |
| `image` | Ścieżka do obrazka tła — `./` to katalog `public/` w launcherze |
| `mods[].projectId` | Modrinth project ID (z URL: `modrinth.com/mod/**P7dR8mSH**`) |
| `mods[].name` | Nazwa do wyświetlenia w logu pobierania |
| `mods[].versionId` | **Konkretna** wersja moda z Modrinth (zakładka Versions → kliknij wersję → ID w URL) |

### Jak znaleźć `versionId`

1. Otwórz stronę moda na Modrinth
2. Zakładka **Versions**
3. Kliknij konkretną wersję
4. ID w URL: `modrinth.com/mod/fabric-api/version/**9956f70c**`

> **Ważne:** Używaj `versionId` (nie `loaderVersion`) — gwarantuje to że każdy użytkownik pobierze dokładnie ten sam plik, niezależnie od nowych updateów.
