# Agentic SDESA – Supplementary Material

This repository holds the original outputs of Agentic SDESA for the three cases in the paper
*Deploying agents to operate construction simulation tools: the SOHG framework and Agentic SDESA*
(Sections 4 and 5). Each folder contains only the final confirmed revision of every file; earlier
review rounds, drafts and helper files are omitted.

## Structure

```
case-1-double-resource/            Case 1, double-resource teaching case (activity-network profile)
case-2-box-culvert/
  resource-limits-only/            Case 2, box culvert project, resource limits only
  with-resource-calendars/         Case 2, the same project with resource calendars
case-3-road-base/
  10-trucks/                       Case 3, road base operation (process-flow profile), 10 trucks
  20-trucks/                       Case 3, the same operation with 20 trucks
```

## Files in each folder

| File | Content |
|---|---|
| `project*.json` | Confirmed project facts (project ABox): activities, relations, resources, sources and confirmed issues |
| `review*.json` | Review of the confirmed project file (open issues) |
| `pdm*.json` | Precedence diagram generated from the project file (activity-network cases only) |
| `aon*.json` | Activity-on-node network generated from the PDM (activity-network cases only) |
| `s3*.json` | SDESA (S3) simulation model generated from the project file and, where present, the AON network |
| `run.json` | Run manifest: inputs with SHA-256 hashes, model settings, seed and outputs |
| `simulation/summary.json` | Run summary: stop reason, final time, activity completions, mean waits, resource busy times and utilisation |
| `simulation/events.csv` | One row per activity occurrence: flow, start, finish, waiting time and resources held |
| `simulation/flow_queue.csv` | Flow-entity queue records |
| `simulation/resources.csv` | Resource allocation and release records |

The suffix `-rN` in Case 1 and Case 2 (resource limits only) gives the project revision.

## Run settings

| Case | Profile | Project revision | Seed | Runs | Horizon | Resource calendars |
|---|---|---|---|---|---|---|
| Case 1 | Activity network | 31 | 17 | 1 | None (to completion) | None |
| Case 2, resource limits only | Activity network | 2 | 17 | 1 | None (to completion) | None; all resources continuously available |
| Case 2, with resource calendars | Activity network | 5 | 17 | 1 | None (to completion) | On; model time 0 is a Monday |
| Case 3, 10 trucks | Process flow | 4 | 17 | 1 | 480 min | None |
| Case 3, 20 trucks | Process flow | 5 | 17 | 1 | 480 min | None |

All activity priorities are 0. Durations are constant, so a single run is deterministic.

## Notes

- The paths in `run.json` refer to the layout of the authors' working directory, in which some inputs
  sat in neighbouring folders. Every input and output is identified by its SHA-256 hash, which matches
  the copy in this repository.
- In Case 2 with resource calendars, the model files (`project.json` to `s3.json`) and the run
  (`run.json`, `simulation/`) came from two working folders; the hashes in `run.json` link them.
- The files are unedited copies of the outputs. Some names, notes and user confirmations were recorded
  in Chinese, as entered during the sessions.
- The native SDESA outputs used for comparison in Section 5 of the paper are not included.
