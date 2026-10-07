# MYST PHRAZE HD (g_mystery_phraze_hd)

Status: runs (smoke-tested 2026-10-07): puzzle board, category spin, letter keyboard.

## Checklist
- [ ] Window size in game.conf matches the largest PNG (notes/scaffold.md)
- [ ] Every symbol in notes/unresolved.txt has a stand-in in src/host/loader_services.cpp
      (`make analyze GAME=g_mystery_phraze_hd` until it reports 0)
- [ ] First run: `make run GAME=g_mystery_phraze_hd DEBUG=shots` — crash trace + screenshots in notes/shots
- [ ] Paths: `make run GAME=g_mystery_phraze_hd DEBUG=files`; engine trace: `mkdir -p data/var/merit/debug/files && touch data/var/merit/debug/files/resource_locator`
- [ ] Reference code: `make decompile GAME=g_mystery_phraze_hd`
- [ ] Translations + help text appear (gamedata/translations/g_mystery_phraze_hd.utf8)
- [ ] Sound and music play (`DEBUG=sound`)
- [ ] A full game plays through (`DEBUG=profile` to catch stalls and old-malloc bugs)

## Log
<!-- dated notes: what broke, what fixed it -->

- 2026-10-07 — runs: DBFClass/RandomizedArrayClass/MystPICRAND_record from libmerit_gendef.so (preloaded), Allegro u* helpers as function pointers, empty libgame_device_irrlicht (its libpng shadowed the runtime's).
