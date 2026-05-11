---
date: 05-04-2026
meeting_type: nthu-run3coupling
meeting_category: Run 3 Coupling
tags:
  - meeting
  - meeting/nthu-run3coupling
---

# 05-04-2026 nthu-run3coupling

## Summary

Run 3 Coupling follow-up focused on v6.1 sample availability and branch merging, SR blinding behavior, signal threshold tuning, fake-factor review, selection plots, b-score thresholds, and possible statistics limitations.

## Notes

- Need to check whether diboson and zjets are available in v6.1.
- The MR or work branch may need to be merged to the v6.1 branch; merge ownership should be confirmed with YJ.
- The SR blinding strategy needs clarification, especially why only a few entries are blinded instead of all SR data.
- The signal threshold may need to change to `0.03` because the previous threshold was too high.
- Plot $m_T$ to check the selections.
- The selection "gap" might be due to a lack of statistics.
- Too much $t\bar{t}$ needs to be checked in the same selection region and same phase space for an apple-to-apple comparison.
- Future checks include fake factor, different b-score thresholds, and threshold blinding versus signal blinding in plotting tools.

## Decisions

- None recorded.

## Questions

- Are diboson and zjets available in v6.1?
- Should the MR be merged by me or by YJ?
- Why not blind all data in SR instead of blinding only a few entries?
- Was `#rodo` intended to mean `#todo` for changing the signal threshold to `0.03`?
- Is the selection "gap" due to a lack of statistics?
- What same selection region and phase space should be used for the $t\bar{t}$ apple-to-apple comparison?

## Links

- Indico:
- GitLab:
- CDS:

## Raw Quick Note

> [!quote]- Original Quick Note
> Date:: 05-04-2026
> Type:: run3coupling
> Links:: 
>
> Raw notes:
>
> - #todo check whether diboson, zjets are available in v6.1
> - #urgent merge to v6.1 branch 
> - #todo check with YJ, whether the MR is ok to merge by me or by YJ.
> - #urgent why not blind all data in SR, but just blind a few of them
> - #rodo change sig threshold to 0.03, previous too high 
> - #later review fake factor
> - #todo plot $m_T$ to check the selections
> - #later investigate different b-score threshold
> - The selection "gap" (different) might be due to a lack of statistics.
> - Too much $t\bar{t}$ needs to check in the same selection region (same phase space, to do the apple -to-pple comparison)
> - #later check the threshold blinding vs signal blinding in plotting tools
