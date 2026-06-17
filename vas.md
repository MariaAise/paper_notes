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


Issue 1:
cut off dates for waves

option 1.1 tried:

- min dates for wave1 fitbit total sample - min date for wave2 fitbit total sample= wave1
- min dates for wave2 fitbit total sample - min date for wave3 fitbit total sample= wave2
- min date for wave3 fitbit total sample= wave2 - now= wave3

results:
Fitbit wave start-dates

  ┌──────┬────────────┬────────────────────────────────────────────────┬──────────────────────────────────┐
  │ Wave │  raw min   │                    problem                     │ robust start (drop lone outlier) │
  ├──────┼────────────┼────────────────────────────────────────────────┼──────────────────────────────────┤
  │ W1   │ 2020-09-20 │ lone bad date, then jumps to 2021-11-01        │ 2021-11-01                       │
  ├──────┼────────────┼────────────────────────────────────────────────┼──────────────────────────────────┤
  │ W2   │ 2022-01-23 │ lone early straggler, then jumps to 2022-05-30 │ 2022-05-30                       │
  ├──────┼────────────┼────────────────────────────────────────────────┼──────────────────────────────────┤
  │ W3   │ 2022-07-19 │ lone outlier, then jumps to 2023-01-09         │ 2023-01-09                       │
  └──────┴────────────┴────────────────────────────────────────────────┴──────────────────────────────────┘

  The raw min of each wave is contaminated by a single anomalous file (device with a wrong clock). Using raw mins, minW3 = 2022-07-19 would land before most of Wave 2 — breaking
  the scheme. After dropping the single leading outlier in each wave, the boundaries are clean and monotonic.

  Your scheme, with robust boundaries

  - Wave 1 (AWARE) = 2021-11-01 → 2022-05-30
  - Wave 2 (AWARE) = 2022-05-30 → 2023-01-09
  - Wave 3 (AWARE) = 2023-01-09 → now

    but applied to AWARE data 

    
  ┌──────────────────────────────┬───────────────┬──────────────┐
  │         Wave window          │ Screen events │ Participants │
  ├──────────────────────────────┼───────────────┼──────────────┤
  │ W1 (2021-11-01 → 2022-05-30) │ 122,297       │ 15           │
  ├──────────────────────────────┼───────────────┼──────────────┤
  │ W2 (2022-05-30 → 2023-01-09) │ 403,549       │ 35           │
  ├──────────────────────────────┼───────────────┼──────────────┤
  │ W3 (2023-01-09 → now)        │ 334,017       │ 34           │
  └──────────────────────────────┴───────────────┴──────────────┘

  Wave 1 ends up with the fewest participants (15) — the opposite of what you'd expect (W1 should be the largest, "over 40"). Here's why the min-based global cutoffs misfire:

  - W1 recruitment was rolling and ran Nov 2021 → Aug 2022 (median W1 Fitbit date = 2022-07-24).
  - But your W2 boundary = min W2 = 2022-05-30.
  - So 2022-05-30 falls before the median of Wave 1. More than half of participants did their Wave 1 after the W2-start cutoff — so their genuine Wave-1 AWARE gets mislabeled
  "Wave 2."

  The waves overlap in calendar time (each wave's recruitment spans ~9 months), so a single global cutoff can't separate them — the min of the next wave lands inside the current
  wave's window.

  The fix that actually works: wave dates from Fitbit, per participant

  This isn't "each makes up its own window" — it's exactly your principle (waves defined by Fitbit dates), but applied per participant because recruitment was rolling. The
  earlier burst analysis confirmed AWARE bursts align with each participant's own Fitbit wave dates. So:

  - Wave 1 AWARE (participant X) = AWARE events within X's own [w1_fitbit_first, w1_fitbit_last] (their Fitbit-defined Wave 1 occasion).
  - Same for W2/W3.

  That correctly assigns each participant's Wave-1 AWARE to Wave 1 regardless of when in 2021–2022 they were recruited.

  So the choice is:
  1. Global min cutoffs (what you proposed) — simple, but undercounts W1 (15) and mislabels rolling-recruited participants. Demonstrated above.
  2. Per-participant Fitbit wave windows — accurate, wave-based, dates sourced from Fitbit; handles the rolling recruitment. (W1 would capture the ~58 participants with W1
  Fitbit, where AWARE overlaps.)
 
the waves overlap heavily at the sample level. Hard evidence:

  Per-participant W1/W2 Fitbit windows (252 participants have both)

  ┌────────────────────────────────────────────────────────────────┬─────────────────────────────────────────┐
  │                              Test                              │                 Result                  │
  ├────────────────────────────────────────────────────────────────┼─────────────────────────────────────────┤
  │ W1 entirely before W2 within each participant                  │ 245 / 252 ✓ (clean individual ordering) │
  ├────────────────────────────────────────────────────────────────┼─────────────────────────────────────────┤
  │ W1 sample window (across participants)                         │ 2021-11-01 → 2023-02-11                 │
  ├────────────────────────────────────────────────────────────────┼─────────────────────────────────────────┤
  │ W2 sample window (across participants)                         │ 2022-01-23 → 2023-12-01                 │
  ├────────────────────────────────────────────────────────────────┼─────────────────────────────────────────┤
  │ Latest W1 ends (2023-02-11) vs earliest W2 starts (2022-01-23) │ W1 and W2 calendar ranges OVERLAP       │
  ├────────────────────────────────────────────────────────────────┼─────────────────────────────────────────┤
  │ Earliest participant to finish Wave 2                          │ 2022-06-05                              │
  ├────────────────────────────────────────────────────────────────┼─────────────────────────────────────────┤
  │ Participants whose Wave 1 starts after that                    │ 200                                     │
  ├────────────────────────────────────────────────────────────────┼─────────────────────────────────────────┤
  │ A single global W1|W2 cutoff that separates everyone           │ does not exist                          │
  └────────────────────────────────────────────────────────────────┴─────────────────────────────────────────┘

  Conclusion (the thing you wanted confirmed)

  200 participants were still doing Wave 1 after other participants had already finished Wave 2. The waves are staggered by rolling recruitment and overlap by more than a year
  in calendar time. Therefore no global date cutoff can split the waves — participants must be analysed on individual (per-participant) wave windows, taken from each
  participant's own Fitbit W1/W2/W3 dates.

  This settles it: the AWARE split must use each participant's own Fitbit wave dates, not a global boundary. Within a participant the ordering is clean (W1 before W2 before W3),
  so applying their personal Fitbit windows to their AWARE stream is well-defined.

  Two minor things flagged: 7 of 252 participants have their W1 Fitbit overlapping their own W2 (likely bad dates or a mislabeled file) — I'll quarantine/inspect those before
  the split.

  The resolved method is: per-participant Fitbit wave windows → applied to that participant's AWARE data → Wave 1 (primary), W2, W3 segments. 
