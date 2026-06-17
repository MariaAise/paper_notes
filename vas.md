116 → 60: two stages

  Stage 1 — 116 devices → 97 resolved (drop 19)

  ┌────────────────────────────┬─────────┐
  │          Outcome           │ Devices │
  ├────────────────────────────┼─────────┤
  │ Resolved to a participant  │ 97      │
  ├────────────────────────────┼─────────┤
  │ Test/researcher (excluded) │ 11      │
  ├────────────────────────────┼─────────┤
  │ Unmatched (excluded)       │ 8       │
  ├────────────────────────────┼─────────┤
  │ Total                      │ 116     │
  └────────────────────────────┴─────────┘

  - 11 test/researcher: devices labelled vasilisstavropoylos80@gmail.com, disasterpasta@gmail.com, Deon test video, trentfootitt@gmail.com — researchers' own phones / test
  sessions, deliberately excluded from a participant dataset.
  - 8 unmatched: labels that don't resolve to any registry participant — 3 blank-label phantom registrations with no data, plus 5 with unidentifiable or not-in-registry labels
  (e.g. khsd879j, s3902857@student.rmit.edu.au, katiep000000+prolific@gmail.com). These carry 21K events total but can't be assigned to a person.

  Stage 2 — 97 devices → 60 participants (collapse 37)

  The same person registered AWARE on multiple devices/sessions. Each device got its own device_id, but they map to one participant_no:

  ┌─────────────────────────┬──────────────────────────────┐
  │ Devices per participant │        # participants        │
  ├─────────────────────────┼──────────────────────────────┤
  │ 1 device                │ 32                           │
  ├─────────────────────────┼──────────────────────────────┤
  │ 2 devices               │ 20                           │
  ├─────────────────────────┼──────────────────────────────┤
  │ 3 devices               │ 7                            │
  ├─────────────────────────┼──────────────────────────────┤
  │ 4 devices               │ 1                            │
  ├─────────────────────────┼──────────────────────────────┤
  │ Total                   │ 60 participants ← 97 devices │
  └─────────────────────────┴──────────────────────────────┘

  So 28 participants account for the 65 "extra" device records (37 collapse). Example from the QA earlier: pno 016 had three devices labelled 201016, Fitbit016@vu.edu.au,
  fitbit016 — all the same person under different label formats; pno 488 had four (3 sharing one Prolific ID + 1 personal email).

  Summary of the whole reduction

  116 registered devices
   −11  researcher/test phones
   − 8  unmatched labels
   ────
    97  resolved devices
   −37  multi-device collapse (28 people had 2–4 devices each)
   ────
    60  distinct participants with AWARE data

  The collapse is legitimate — pooling a person's multiple devices into one participant is correct (Phase 2 sums their events across devices per day). The only genuine loss is
  the 8 unmatched devices (21K events from people we can't name); the 11 test/researcher are correctly out of scope.
  ⎿  Stop says: Reminder: before stopping, append a one-line timestamped entry to /Users/e5028514/vas/research_log.md for any significant work this session — script runs, data
     manipulations, decisions, file outputs, or research findings. Skip if the turn was purely conversational with no file changes.

____________

## AWARE


  - Wave 1 (AWARE) = 2021-11-01 → 2022-05-30
  - Wave 2 (AWARE) = 2022-05-30 → 2023-01-09
  - Wave 3 (AWARE) = 2023-01-09 → now
