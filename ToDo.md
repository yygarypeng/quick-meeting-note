---
title: Todo
date: 2026-05-10
tags:
  - todo
aliases:
  - Central Todo
  - Task List
---
# Todo Board

> [!abstract] Board Workflow
> Check or uncheck tasks here, then ask: `Clean Todo.md.`
> Tasks are grouped by broad area: `QE`, `HGTD`, `Run 3 Coupling`, and `Students`.
> Colored callouts show the task marker: `#urgent`, scheduled due dates, `#todo`, and `#later`.
> Tasks with clear dates use `Due: MM-DD-YYYY`; add time only if known.

---
## QE

> [!todo] #todo
> Normal follow-up work.
>
> #### 05-11-2026
>
> - [ ] #todo Retrain the model with Danning's splitting and send PCRES IO to Yulei. Source: [[Meetings/QE/05-11-2026 qe|05-11-2026 qe]]
> - [ ] #todo Follow up on the comparison of Evanet. Source: [[Meetings/QE/05-11-2026 qe|05-11-2026 qe]]
>
> #### 05-06-2026
>
> - [ ] #todo Plot angle ang+ang and ang-ang to compare to the classical method. Source: [[Meetings/QE/05-06-2026 qe|05-06-2026 qe]]
> - [ ] #todo Check whether it is necessary to use HL features. Source: [[Meetings/QE/05-06-2026 qe|05-06-2026 qe]]
> - [ ] #todo Check whether l1 is needed in addition to the angular mmd losses. Source: [[Meetings/QE/05-06-2026 qe|05-06-2026 qe]]

> [!quote] #later
> Future, unclear, maybe, or background work.
>
> #### 05-06-2026
>
> - [ ] #later Do the grid search to find the proper hyperparameters. Source: [[Meetings/QE/05-06-2026 qe|05-06-2026 qe]]
> - [ ] #later Gauge the performance of models: test likelihood, KV... ?. Source: [[Meetings/QE/05-06-2026 qe|05-06-2026 qe]]
> - [ ] #later Do k-fold (2-fold) and push to the central git repo. Source: [[Meetings/QE/05-06-2026 qe|05-06-2026 qe]]
> - [ ] #later After pushing to the central repo, compare to the typical angle calibrations. Source: [[Meetings/QE/05-06-2026 qe|05-06-2026 qe]]

---
## HGTD

> [!danger] #urgent
> Blocking, deadline-critical, or action-stop work.
>
> #### 05-05-2026
>
> - [ ] #urgent Measure data retrieval time from the DB and comparison time. Source: [[Meetings/HGTD/05-05-2026 hgtd|05-05-2026 hgtd]]
> - [ ] #urgent Discuss with YJ about the `QuerySet` meaning. Source: [[Meetings/HGTD/05-05-2026 hgtd|05-05-2026 hgtd]]

> [!todo] #todo
> Normal follow-up work.
>
> #### 05-04-2026
>
> - [ ] #todo Register batch wafer and batch sensor IV if the required records do not exist. Source: [[Meetings/HGTD/05-04-2026 nthu-hgtd|05-04-2026 nthu-hgtd]]
>
> #### 04-27-2026
>
> - [ ] #todo Add pending documentation locations, layer documentation, sensor IV documentation, and hybrid documentation. Source: [[Meetings/HGTD/04-27-2026 nthu-hgtd|04-27-2026 nthu-hgtd]]

> [!quote] #later
> Future, unclear, maybe, or background work.
>
> #### 05-04-2026
>
> - [ ] #later Clarify zip file untar behavior, including whether an upper bound is needed and whether `leggy?` means legacy behavior. Source: [[Meetings/HGTD/05-04-2026 nthu-hgtd|05-04-2026 nthu-hgtd]]

---
## Run 3 Coupling

> [!danger] #urgent
> Blocking, deadline-critical, or action-stop work.
>
> #### 05-04-2026
>
> - [ ] #urgent Merge to the v6.1 branch. Source: [[Meetings/Run 3 Coupling/05-04-2026 nthu-run3coupling|05-04-2026 nthu-run3coupling]]
> - [ ] #urgent Clarify why not all data in SR are blinded, and why only a few entries are blinded. Source: [[Meetings/Run 3 Coupling/05-04-2026 nthu-run3coupling|05-04-2026 nthu-run3coupling]]

> [!todo] #todo
> Normal follow-up work.
>
> #### 05-04-2026
>
> - [ ] #todo Check whether diboson and zjets are available in v6.1. Source: [[Meetings/Run 3 Coupling/05-04-2026 nthu-run3coupling|05-04-2026 nthu-run3coupling]]
> - [ ] #todo Check with YJ whether the MR should be merged by me or by YJ. Source: [[Meetings/Run 3 Coupling/05-04-2026 nthu-run3coupling|05-04-2026 nthu-run3coupling]]
> - [ ] #todo Change signal threshold to `0.03`; previous threshold was too high. Source: [[Meetings/Run 3 Coupling/05-04-2026 nthu-run3coupling|05-04-2026 nthu-run3coupling]]
> - [ ] #todo Plot $m_T$ to check the selections. Source: [[Meetings/Run 3 Coupling/05-04-2026 nthu-run3coupling|05-04-2026 nthu-run3coupling]]
> - [ ] #todo Check the excess $t\bar{t}$ in the same selection region and same phase space for an apple-to-apple comparison. Source: [[Meetings/Run 3 Coupling/05-04-2026 nthu-run3coupling|05-04-2026 nthu-run3coupling]]

> [!quote] #later
> Future, unclear, maybe, or background work.
>
> #### 05-04-2026
>
> - [ ] #later Review fake factor. Source: [[Meetings/Run 3 Coupling/05-04-2026 nthu-run3coupling|05-04-2026 nthu-run3coupling]]
> - [ ] #later Investigate different b-score threshold. Source: [[Meetings/Run 3 Coupling/05-04-2026 nthu-run3coupling|05-04-2026 nthu-run3coupling]]
> - [ ] #later Check threshold blinding versus signal blinding in plotting tools. Source: [[Meetings/Run 3 Coupling/05-04-2026 nthu-run3coupling|05-04-2026 nthu-run3coupling]]

---
## Students

> [!danger] #urgent
> Blocking, deadline-critical, or action-stop work.
>
> #### 05-03-2026
>
> - [ ] #urgent Plot $M_T$ to check the selection correctness. Source: [[Meetings/Students/05-03-2026 students|05-03-2026 students]]

> [!todo] #todo
> Normal follow-up work.
>
> #### 05-03-2026
>
> - [ ] #todo Plot cutflow in HTML or CSV. Source: [[Meetings/Students/05-03-2026 students|05-03-2026 students]]
> - [ ] #todo Apply the new structure from the v6 branch in the coupling class. Source: [[Meetings/Students/05-03-2026 students|05-03-2026 students]]
> - [ ] #todo Compare cutflow with the same b-score between v5 and v6.1. Source: [[Meetings/Students/05-03-2026 students|05-03-2026 students]]

> [!quote] #later
> Future, unclear, maybe, or background work.
>
> #### 05-03-2026
>
> - [ ] #later Study group: prepare materials for jets and heavy jets. Source: [[Meetings/Students/05-03-2026 students|05-03-2026 students]]

---
## Done

> [!success]- Done
> Completed or cancelled tasks are archived here by broad area and source date.
>
> ### HGTD
>
> #### 05-04-2026
>
> - [x] #urgent Check wafer existence before upload. If a wafer exists, show `Wafer XXXX already exist, action stop!` and stop upload. Source: [[Meetings/HGTD/05-04-2026 nthu-hgtd|05-04-2026 nthu-hgtd]]
> - [x] #todo Update `AddBatchWaferUploadSensorIV` to follow the same upload style and duplicate-wafer error-message behavior. Source: [[Meetings/HGTD/05-04-2026 nthu-hgtd|05-04-2026 nthu-hgtd]]
> - [x] #todo Check the wafer-sensor relationship before upload. Source: [[Meetings/HGTD/05-04-2026 nthu-hgtd|05-04-2026 nthu-hgtd]]
> - [x] #todo Upload the wafer-sensor relationship when appropriate. Source: [[Meetings/HGTD/05-04-2026 nthu-hgtd|05-04-2026 nthu-hgtd]]
>
> #### 04-27-2026
>
> - [x] #todo Add a tutorial link behind the Grafana link in the frontend page. Source: [[Meetings/HGTD/04-27-2026 nthu-hgtd|04-27-2026 nthu-hgtd]]
> - [x] #todo Check and keep the cancel button functionality. Source: [[Meetings/HGTD/04-27-2026 nthu-hgtd|04-27-2026 nthu-hgtd]]
> - [x] #todo Show a pointer hover message on buttons, including `convert to zip`. Source: [[Meetings/HGTD/04-27-2026 nthu-hgtd|04-27-2026 nthu-hgtd]]
> - [x] #todo Add download support for conversion scripts for sensor IV, using `test.py` in `frontned_gui/public` if appropriate. Source: [[Meetings/HGTD/04-27-2026 nthu-hgtd|04-27-2026 nthu-hgtd]]
> - [x] #later Add Sahla(?)'s converter scripts with message `convert XXX to XXX/n Only IV, CV`, link back to a dummy file, and clarify future development scope. Source: [[Meetings/HGTD/04-27-2026 nthu-hgtd|04-27-2026 nthu-hgtd]]
