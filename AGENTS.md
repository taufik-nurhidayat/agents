- ALWAYS db schema, logic, variables in english. UI text can multi-language
- Bun as package manager
- Some documents at @docs/[file].md

## Design
- Use Shadcn UI Design (BaseUI)

## Local Development
- For local app dev/build/docker runs, set `VITE_PWA_ENABLED=false` by default so the service worker and local PWA cache do not mask fresh code changes.
- If local browser behavior looks stale, suspect an old service worker/cache first; open the app once with `VITE_PWA_ENABLED=false` so runtime cleanup can unregister it.

## Coding Style
- feature-first architecture dengan batas Clean Architecture yang pragmatis.
- Max 1000 lines, readable for human+llm.
- Function name = what it do.
- Reusable as much as possible.

## Planning Mode
- ALWAYS use plan mode if task > 3 steps
- ALWAYS ask user for clearer context

## Testing Scenario
- ALWAYS update/create test after changes, ensure pass.
- ONLY test what you changes if in worktree
- NEVER test docs

## Writing (Bahasa Indonesia)

UI text is Indonesian. The rule that decides English vs Indonesian:

- **A term stays English when a hospitality ops person would say it in English
  on the job** — handover, check-in, venue, link, shift, briefing, PIC, draft,
  pin, preview, Staff App, Command Center. Inflect it Indonesian-style where
  natural: *di-pin*, *sudah di-handover*.
- **A word from the software's own construction never reaches the screen** —
  polling, lifecycle, placeholder, JSON, sheet, backend, Parse class names.
  Translate it, or rewrite the sentence so the concept disappears.
- **Everything else translates to the word people actually use.** If the only
  Indonesian equivalent is one you have never heard spoken (*tautan, ciutkan,
  sematan, berkas, pratinjau*), you are in case 1. The tell for a bad
  translation is that it is *correct*.

Glossary — use / never:

| Use | Never | Why |
| --- | --- | --- |
| Tugas | Task | The product's central noun; `Task` stays the Parse class only |
| Dikonfirmasi · Konfirmasi tugas | Diakui · Akui | *mengakui* means to admit or confess |
| Terkendala · kendala | Terhambat · hambatan | one letter from *Terlambat*, and two roots for one state |
| PIC | Pelaksana · Penanggung jawab | *pelaksana* is tender-document register |
| link | tautan | nobody types *tautan* |
| password | kata sandi | |
| Preview | Pratinjau | |
| file | berkas | *berkas* is a dossier in a registry office |
| update | pembaruan | a nominalisation nobody utters; *update* inflects natively |
| di-upload | diunggah | *unggah* lives in style guides, not in speech |
| tekan | ketuk | *ketuk* is knocking on a door |
| chat | percakapan | the nav tab already says Chat |
| cek | periksa | *periksa* is inspection register |
| HP | perangkat | in reassurance copy: *tersimpan di HP*, not *di perangkat* |
| Command Center | command center | it is a product name |
| Aman · Perlu dicek · Hampir telat · Mendesak | Sesuai jalur · Berisiko · Kritis | task health: the first three are calques, and *kritis* is medical |
| Hampir tenggat | Segera selesai | *Segera selesai* misparses as an imperative |
| Harus selesai dulu | Prasyarat | procurement-annex register |

Offline copy — the app's signature surface, and where translationese does the
most damage. It must narrate **the work**, not the outbox:

- `belum terkirim`, never `tertunda` (postponed — nobody decided that) or
  `tertahan` (implies an agent holding it back).
- `gagal terkirim` when the send actually failed.
- Never name the queue in a sentence. `antrean lokal`, `antrean offline`,
  `menunggu sinkronisasi` and `kiriman` are the developer's mental model in an
  Indonesian coat. The staffer's question is only whether it is moving.
- Say what is safe *and* that it will go: `Tersimpan di HP. Terkirim otomatis
  begitu ada sinyal.` A state without a promise makes people redo work.
- `sinyal`, not `koneksi` — it is what they are actually looking at.

Voice:

- Formal-neutral. `Anda` only when a person must be addressed. No `kamu`, no
  slang, no exclamation marks.
- No `Silakan` / `Mohon` / `Harap` — the staffer has no choice, so the word
  only adds a syllable.
- Prefer the spoken half of each pair: `sudah` over `telah`, `bisa` over
  `dapat`, `tapi` over `tetapi`.
- Indonesian word order, not English: `Hanya berlaku`, not `Berlaku hanya`.
- No semicolons. Split the sentence.

Errors — `[what failed]. [what is still safe]. [what to do next].` This app is
offline-first, so the middle clause is usually the important one: say the data
is queued on the device. Never end on a diagnosis; never show a Parse code.

Buttons — imperative verb plus object where the object is not obvious. A
confirm button repeats the title's verb, never `Konfirmasi` or `OK`. Dismiss
labels: `Batal` to abandon an edit, `Tutup` to leave a read-only view,
`Kembali` only where the destructive verb is itself *Batalkan*.

Empty states — `Belum ada X.` means nothing was ever created; `Tidak ada X yang
cocok.` means a filter excluded everything. Never claim empty for data that
failed or is still loading.

Punctuation — ellipsis is `…`, one character. Sentence case everywhere except
navigation module names and proper nouns.

`tests/shared/writing-conventions.test.ts` enforces the glossary, the
particles and the ellipsis.

## Gitlab
- Use glab cli for gitlab merge request or something

## Git Workflow
- ALWAYS commit and push directly to `develop`. NEVER create a feature/fix
  branch, and never ask to branch first.
- Remote: `git@gitlab.com:8grams/impactplus/salam-app.git`
