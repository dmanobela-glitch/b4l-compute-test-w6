# B4L compute

This repository runs work for its owner's B4L app on GitHub's runners. A public repository uses none of the
owner's GitHub minutes. The B4L app wrote every file here; it holds no source code.

- `.github/workflows/b4l-hunt.yml`: one hunt of the owner's strategy (`jobs/<id>.json`) on their prices
  (`data/<id>.csv`). The result is sealed to the owner's B4L app key (X25519 + AES-256-GCM, "b4l-seal/1") before it
  leaves the runner, so `results/<id>.b4l` and the run log show nothing readable; only that app opens it.
- `.github/workflows/b4l-donate.yml`: one bounded window (70 to 350 minutes) of the
  B4L grid node 1.23.0, compiled, checked against its sha256 `4cd84edae6fb4cbf38010178db43e1867259d528f13da167a333fac1c541a5b8`.
  The grid credits the B4L account named by the repository variable `B4L_EMAIL`.
- `bin/b4l-hunt.mjs`: the B4L strategy engine's hunt, compiled (sha256 `63df5f38a6ee36b939641c2641b981eb0c2971f8cd8620a708f739d4e0c697e8`).

Nothing here runs on a schedule: the app starts each run, and STOP ALL in the app cancels every run that is queued or
running. To stop for good, disable the workflows (Actions tab) or delete this repository.
