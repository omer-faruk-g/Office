# Office

Office is a multi-role crew skill for [Claude Code](https://code.claude.com). It is prompt-only: one `SKILL.md`, with no scripts and no hooks. For a coding task, the model sets up a virtual software office, assigns roles, works through the task role by role, and audits the result as lead before it delivers the code.

## Phases

| Phase | Name | What the model does |
|---|---|---|
| 1 | Crew allocation | It picks the team the task needs: system architect, an exact count of developers (backend, frontend, game logic, engine), a UI/UX and graphics designer, and a QA and security tester. It prints the crew table before it goes on. |
| 2 | Crew execution | It works in role order. The architect sets the folder structure and interfaces, designers produce CSS/Tailwind, UI schemas or design specs, developers write the implementation, and QA writes unit, boundary and failure tests. |
| 3 | Lead audit | It reviews the crew's output for O(N²) risks, memory leaks, unhandled edge cases and missing files, rejects `// TODO` placeholders, and fixes flaws directly. |
| 4 | Final delivery | It outputs the verified code, the file layout and how to run it. |

## Install

```bash
git clone https://github.com/omer-faruk-g/Office ~/.claude/skills/office
```

Then restart Claude Code. The skill loads when you say office, kadro kur or ekip oluştur, ask to run a project through a multi-agent office, or type `/office`.

## Limits

- The roles are written by one model in one conversation. The skill does not start separate agents by itself, so the "crew" is a way to structure the work, not independent reviewers.
- Phase 1 prints the crew table and goes on without waiting. Skills that require a confirmed plan first (for example ClaudeMT or ClaudPer) conflict with this; when both load, the model has to pick one.
- The lead audit is the same model checking its own output. It can miss what it got wrong in the first place, so run the tests yourself.
- No measured improvement yet.

## Background

- **Role-based software agents:** Qian et al., [ChatDev: Communicative Agents for Software Development](https://arxiv.org/abs/2307.07924) (2023); Hong et al., [MetaGPT: Meta Programming for A Multi-Agent Collaborative Framework](https://arxiv.org/abs/2308.00352) (2023).

## Türkçe özet

Office, Claude Code için tek dosyalık bir skill:

- Kodlama görevine göre sanal bir ekip kurar: mimar, sayısı belli geliştiriciler, UI/UX tasarımcısı, QA ve güvenlik test uzmanı. Kadro tablosunu önce gösterir.
- İşi rol sırasıyla yapar: mimar klasör yapısını ve arayüzleri, tasarımcı CSS ve UI şemalarını, geliştiriciler kodu, QA testleri yazar.
- Sonunda lider olarak O(N²) riskini, bellek sızıntısını, eksik uç durumları ve eksik dosyaları denetler; `// TODO` bırakmaz, hatayı kendisi düzeltir.
- Son kodu, dosya düzenini ve çalıştırma talimatını verir.

Rollerin hepsini aynı model yazar; ayrı ajanlar başlatmaz.

Kurmak için yukarıdaki `git clone` komutunu çalıştırın ve Claude Code'u yeniden başlatın.

## License

GPL-3.0-or-later. See [LICENSE](LICENSE).
