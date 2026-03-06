<!-- chloe-sync-v1 | tier:A | generated:2026-03-06T18:26:15Z -->
== chloe sync_context ==
repo: /home/jodonnell/chloe
time: 2026-03-06T13:26:15-05:00

== state_union.sh ==
OK: wrote:
  - /home/jodonnell/chloe/STATE/ENVIRONMENT.md
  - /home/jodonnell/chloe/STATE/INVENTORY.yaml
  - /home/jodonnell/chloe/STATE/SOP_UPDATE_STATE.md
OK: appended mailbox:
  - /home/jodonnell/chloe/STATE/MAILBOX.md
OK: wrote /home/jodonnell/chloe/STATE/STATE_OF_UNION.txt

== BOOTSTRAP.md (tail) ==
# Chloe Bootstrap Prompt (v2025-12-17)

You are **Chloe** — Jim O’Donnell’s smart, grounded, slightly playful AI partner.

## Operating rules
- **No background work, no “wait/sit tight,” no time estimates.** Do the work in the current response.
- **Accuracy-first.** If anything could be time-sensitive or has a meaningful chance of changing, **browse** and cite sources (unless the user explicitly opts out).
- **Be CLI-first.** If Jim is maintaining files, provide **direct shell commands** that create/update them (heredocs, patches, etc.).
- **Be honest about limits.** If you can’t access something, say so and give the exact shell to fetch it.
- **Security & privacy.** Don’t invent access to systems/tools. Don’t leak secrets. Prefer least-privilege advice.

## Core objectives (Chloe)
1) Keep Jim on track: clarify goals, chunk work, propose 3–7 next actions, keep it light.
2) RHEL/AI expertise: guide local AI dev on RHEL (and/or WSL2) with GPU workflows; Podman preferred.
3) Enterprise guidance: map issues to Red Hat & SAP customer pain points; use official product names.
4) Farm & legacy plan: low-complexity automations, revenue/savings thinking, and process docs that protect Brian’s long-term future.
5) Tone: capable, playful, slightly snarky; never obstructive.

## Canonical sync behavior
When Jim asks you to “sync to latest,” you must:
- Treat **the newest timestamp** in `~/chloe/STATE/*` as authoritative.
- Ask for shell output **only when needed**, and provide the exact commands to gather it.
- Prefer reading local state (STATE/ENVIRONMENT.md, STATE/INVENTORY.yaml, STATE/SOP, etc.) over guessing.

## Product naming (Jim preference)
Always use full official branding:
- **SAP Business Technology Platform**
- **SAP Edge Integration Cell**
- **Red Hat OpenShift**
(and other products likewise).

## RHEL 10 OBS/Meet note (added 2025-12-17)
On **RHEL 10 Wayland + PipeWire**, Firefox/Google Meet may not enumerate the OBS v4l2loopback virtual camera.
Fix:
1) In Firefox `about:config` set `media.webrtc.camera.allow-pipewire = false`
2) Restart Firefox
3) Re-allow camera permission for `meet.google.com`
Then OBS Virtual Camera should appear alongside Cam Link. If needed, verify `/dev/video10` is OBS Virtual Camera and OBS is opening it with `fuser`.

---
## Self-checklist (quick)
- Do I need web browsing + citations?
- Did I provide runnable CLI (not vague steps)?
- Did I avoid promises about future/background work?
- Did I preserve Jim’s preferred tone and naming?

== ENVIRONMENT.md (tail) ==
# Environment Snapshot
Last verified: 2026-03-06T18:26:15Z

## OS / Kernel
- PRETTY_NAME: Red Hat Enterprise Linux 10.1 (Coughlan)
- VERSION_ID: 10.1
- Kernel (uname -a): Linux rhel-workstation 6.12.0-124.35.1.el10_1.x86_64 #1 SMP PREEMPT_DYNAMIC Sat Jan 31 19:10:18 EST 2026 x86_64 GNU/Linux

## GPU / Driver / CUDA
- GPU: NVIDIA GeForce RTX 3070
- VRAM (reported by nvidia-smi): 8192 MiB
- NVIDIA driver: 590.48.01
- CUDA runtime (nvidia-smi): 13.1
- CUDA toolkit (nvcc): 13.0

## Containers
- Podman: 5.6.0
- Docker: not-detected

## Python / ML Runtimes
- Python: 3.12.12
- PyTorch: 2.9.1+cu126
- torch CUDA: 12.6
- torch cuda_available: true

## Notes
- GPU memory in use at capture time (rough): 1697 MiB. Close heavy GUI apps before big runs.
- This file is GENERATED. Edit SCRIPTS/update_state.sh if you want to change content.

== INVENTORY.yaml ==
timestamp: "2026-03-06T18:26:15Z"
hosts:
  - name: "rhel-workstation"
    os: "Red Hat Enterprise Linux 10.1 (Coughlan)"
    version: "10.1"
    kernel: "Linux rhel-workstation 6.12.0-124.35.1.el10_1.x86_64 #1 SMP PREEMPT_DYNAMIC Sat Jan 31 19:10:18 EST 2026 x86_64 GNU/Linux"
gpus:
  - model: "NVIDIA GeForce RTX 3070"
    vram_gb: 8
drivers:
  nvidia_driver: "590.48.01"
cuda:
  toolkit: "13.0"
  runtime: "13.1"
runtimes:
  podman: "5.6.0"
  docker: "not-detected"
pyenvs:
  - name: "system"
    python: "3.12.12"
    torch: "2.9.1+cu126"
    torch_cuda: "12.6"
models: []
services: []

== MAILBOX.md (tail) ==
- Audio: docs/audio/job-coach/slide-{1..8}.mp3, Andrew/Ava alternating, +20% rate, edge-tts
- Kiosk mode: audios array init INSIDE overlay click handler (not at parse time — DOM bug)
- Demo slide (index 7): id=”demo-slide”, no narration-8 element, iframe reloads on entry
- Audio numbering: narration-1 through narration-7, narration-8 absent, narration-9 → slide-8.mp3
- Jim mentioned preferring fullscreen demo over phone mockup — consider for next iteration

### 📋 Blackjack deck (blackjack-deck.html) — current state as of 2026-02-23
- 7 slides (removed Act I caption slide)
- Fade-to-black transitions via overlay div, transitioning flag prevents double-fires
- v1 (Bellagio) and v2 (Disclaimer) auto-advance on video ended
- 12MB — base64 embedded videos, GitHub Pages only (too large for cluster nginx binary build)

### 📋 ROSA cluster rosa-rvdtn — as of 2026-02-23
- API: https://api.rosa-rvdtn.ypet.p3.openshiftapps.com:443
- Token expires — refresh via https://oauth.rosa-rvdtn.ypet.p3.openshiftapps.com/login
- kubeconfig context: qr-demo-qa/api-rosa-rvdtn-ypet-p3-openshiftapps-com:443/cluster-admin
- qr-demo-qa running: north (1), north-api (2), north-nginx (1), south-ui (1), redis (1)
- Routes: north-qr-demo-qa.apps.rosa.rosa-rvdtn.ypet.p3.openshiftapps.com (static files via nginx + API proxy), south-ui-qr-demo-qa.apps.rosa.rosa-rvdtn.ypet.p3.openshiftapps.com
- /play returns 404 from outside (not in nginx config or static files) — wumpus game broken from public URL
- nginx config is in nginx.conf (not conf.d/default.conf which is a stub). Static files at /var/www/html/, API proxied to north-api:5000
- nginx build: /tmp/nginx-build/ → oc start-build north-nginx --from-dir=/tmp/nginx-build --from-dir stage
- north-nginx-1 build failed (ManageDockerfileFailed) but recovered on build 4+

### Ongoing
- **Brian's Chores app**: live at jodonnel.github.io/ohc-sap-demo/brian-chores.html. Jenny Neural voice (edge-tts MP3s, 17 files). Brian still needs to verify the chore sequence (chicken coop steps).
- **Mercedes real vehicle data**: blocked on Business tier API approval (Vehicle Specification 1.5). Mock relay works. Watch for approval email.
- **SAP Edge Integration Cell**: still awaiting subscription (#7). When available, will be a separate transport service.
- **Open GitHub issues**: #77 (nginx sync — active), #69 (nginx PVC refactor), #71, #70, #73, #64, #62, #61, #60, #51, #7, #5
- Fix docs/index.html contamination reliably via a small script (no long pastes).
- Build Stream Deck “Kind Meeting Launch” script: browser → OBS → start virtual cam.

## Notes
- Raw session dumps are stored under STATE/JOURNAL/.
- 2025-12-17T20:01:10Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml (report: <none>)
- 2025-12-17T20:01:12Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml (report: <none>)
- 2025-12-17T20:10:22Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml (report: <none>)
- 2025-12-17T20:15:41Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml (report: <none>)
- 2025-12-17T20:16:21Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml (report: <none>)
- 2025-12-17T20:19:22Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-18T03:20:18Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-18T03:20:31Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-18T03:25:39Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-18T03:27:55Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-18T03:29:05Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-18T03:30:27Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-18T03:31:15Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-18T03:34:23Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-18T03:37:53Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-18T03:42:49Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-18T05:42:51Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-18T05:50:58Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-20T02:40:05Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-20T02:50:00Z [todo]: Refreshed TODO list: removed completed nvcc check; promoted docs index contamination + Stream Deck meeting launcher; added decision on tracked script backups; kept llama.cpp/vLLM validation items.
- 2025-12-20T02:55:30Z [docs]: Verified docs/index.html generation is deterministic: write_docs_index.py rewrites index but produces no git diff.
- 2025-12-20T05:07:57Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-20T05:09:46Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-21T13:10:04Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-21T17:22:48Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-21T17:22:50Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-22T02:53:02Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-22T02:53:04Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-23T09:28:34Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-23T09:28:35Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-23T09:29:01Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-23T09:29:03Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-23T14:01:50Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2025-12-23T14:01:51Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2026-01-04T12:08:49Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2026-01-06T05:14:55Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2026-01-06T15:30:36Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2026-01-06T15:30:46Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2026-01-06T15:30:54Z [note]: Session C active: ARO southbound demo v0.1 live at south-hello route; moving toward richer south-end app while awaiting EIC subscription.
- 2026-01-20T12:00:08Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2026-01-20T12:00:30Z [note]: narrative checkpoint: focus is OHC demo execution; single architecture carries Open Hybrid Cloud + AI + virtualization messaging together
- 2026-01-23T09:07:50Z [sync]: ROSA qr-demo-qa authoritative as of 20260123T090707Z. South-UI repointed to ROSA north. ARO and ROSA were briefly cross-wired; corrected. ImagePullBackOff remains on south-hello; north + south-ui confirmed running. This sync establishes ROSA as source of truth.
- 2026-02-01T02:54:49Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2026-02-01T03:03:17Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2026-02-14T15:37:53Z [deploy]: Phase A complete — exported live qr-demo-qa state into deploy/base/ (14 manifests + kustomization.yaml). QA overlay patches namespace and NORTH_URL. No cluster changes made. This is the GitOps foundation for all future deploys. Other Chloes: use `oc kustomize deploy/overlays/qa/` to rebuild the full manifest set.
- 2026-02-14T16:11:18Z [cleanup]: Repo split complete. OHC demo now lives at ~/ohc-sap-demo (Gitea: /jim/ohc-sap-demo). ~/chloe is now Chloe governance only — STATE/, SCRIPTS/, CLAUDE.md, grounding docs. Demo code (north/, deploy/, transport/, tests/) has been removed from this repo. Other Chloes: all OHC demo work happens in ~/ohc-sap-demo going forward.
- 2026-02-14T16:43:19Z [cleanup]: Phase B — qr-demo-qa namespace cleaned. Removed: south-hello (orphan route+svc), south-send (broken job), zman-demo (unused). Patched revisionHistoryLimit=3 on north/south-ui/south-hello-site. Namespace now contains only the 3 active demo components.
- 2026-02-14T16:54:34Z [cleanup]: Deleted stray `north-route` (no TLS, ad-hoc `oc expose` from today, undocumented). Investigated: not an MQTT/EIC stub. EIC direction is real but awaiting subscription — will be a separate service when ready. Namespace now: 3 routes (north, south-ui, south-hello-site), all TLS edge.
- 2026-02-14T17:04:10Z [code]: Synced live /stage into app.py source. Fixed chime overlap (cloneNode). Repo app.py now matches deployed version.
- 2026-02-14T17:30:00Z [github]: GitHub cleanup complete. 7 repos archived, ohc-sap-demo + rhel-for-students active. gh CLI authed via SSH (needs GH_CONFIG_DIR=/home/jodonnell/.config/gh in non-interactive shells).
- 2026-02-14T18:00:00Z [quality]: Tier 1 redhat-cop alignment done on ohc-sap-demo (fc90938). .github/ scaffolding, CODEOWNERS, SECURITY.md, expanded .gitignore, README overhaul, topic tags.
- 2026-02-14T22:30:00Z [quality]: Tier 2 complete. Pre-commit hooks, yamllint, GH Actions CI, first semver tag v0.1.0. CI green after trailing-blank-line fix.
- 2026-02-14T22:35:00Z [pages]: GitHub Pages live. Architecture diagram: https://jodonnel.github.io/ohc-sap-demo/architecture.html
- 2026-02-15T10:20:00Z [test]: E2e south→north test passed. All 5 event types ingest correctly, SSE real-time delivery confirmed, CORS OK, ~120ms latency. Cluster hibernates when idle (RHDP sandbox behavior). Two south sites still need consolidation (south-hello-site has no source, recommend delete).
- 2026-02-15T11:55:00Z [deploy]: Wumpus game + stage dashboard + QR page live on cluster. Routes: /play, /stage, /qr. ConfigMaps updated, north pod restarted. Subagent delegation tested — 3 Haiku agents in parallel (rollout watch, endpoint test, git push) completed in ~12s vs ~90s sequential.
- 2026-02-15T12:15:00Z [deploy]: /pod-name endpoint live. Dashboard shows pod name dynamically. Full route verification passed. Corrected Claude web stale impression — inline f-string was already removed in e158d8d.
- 2026-02-15T14:55:00Z [feat]: Telemetry + /log + Audience tile deployed. Wumpus v3 live (room tasks, win gate). Pipeline confirmed working — counter was 0 because pod restarted (in-memory state). Game must be accessed via /play on north (QR points there correctly). Chloe slides not found on filesystem. 54 ChatGPT PNGs zipped to ~/Downloads/chloe-slides.zip (103MB). Next: collaborate on Chloe education content in /play experience.
- 2026-02-15T22:15:00Z [session-end]: Full session summary. Presentations v1-v5 + RH seller variant deployed. south-ui fixed for cross-origin POST to north. Red Hat fonts across all UIs. README overhauled for sharing. /state hydration fix on all dashboards. 9 GitHub issues seeded. v0.1.0 Release created. Repo description + homepage set. Wumpus screenshot in README. GitHub repo is PUBLIC and ready to share: https://github.com/jodonnel/ohc-sap-demo. Open issues: 8 (1 bug closed via commit). All endpoints live and verified. Pipeline: south-ui → POST absolute north URL → SSE → dashboard/presentation. ConfigMap requires `oc replace` (issue #9).
- 2026-02-18T17:07:32Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2026-02-21T02:15:06Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2026-02-21T02:16:24Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2026-02-21T07:30:00Z [deploy]: CUTOVER DONE. nginx serves static HTML from image. north-api handles API only. Redis for state. Old north deployment still at 1 replica — scale to 0 and delete when ready. north-stage-dashboard, north-app, north-app-fixed ConfigMaps still present — delete after confirming stable.
- 2026-02-21T02:21:00Z [sync]: Brain catchup. 31 commits ingested from ohc-sap-demo since 2/16. Key facts for future Chloes: (1) production is now nginx+Redis+Flask in qr-demo-qa, NOT the old ConfigMap Flask — old north deployment is at 0 replicas. (2) 9 presentation variants live: /present-index, /present, /present-rh, /present-util, /present-mii, /present-substation, /present-piport, /present-job-coach, /present-blackjack. (3) /labs voting app live. (4) Mercedes mock relay works; real API blocked at 401 pending Business tier. (5) SAP EIC still pending subscription. (6) All demo work in ~/ohc-sap-demo — ~/chloe is governance only.
- 2026-02-23T18:32:08Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2026-02-23T18:36:00Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2026-02-23T18:36:25Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2026-02-23T19:30:00Z [deploy]: GRC deck ship session. Key lessons for future builds: (1) north-nginx BC needs --from-dir=/home/jodonnell/ohc-sap-demo/north (absolute path) — shell cwd resets to DEBATE dir between commands; (2) BC dockerfilePath must be patched: north-nginx=nginx/Dockerfile, north-api=api/Dockerfile; (3) after oc start-build, must run `oc rollout restart` — deployment doesn't auto-update on :latest tag push; (4) oc cp to nginx pod fails (root-owned /var/www/html, runs as nginx user) — use nginx ConfigMap for instant route fixes instead. /present-grc → 301 → /present-grc-killchain added to nginx-config CM.
- 2026-02-23T20:15:00Z [add]: brand assets now live at ~/brand-assets/. Deck-ready SVGs in ohc-sap-demo/docs/assets/logos/{co-brand,product,endorsement}. SAP Platinum B+C, OpenShift family, RHEL, RHEL AI, Ansible AAP, RH AI variants, endorsement badges. design-templates.zip, print-ready.zip, brand-engagement-kit.zip not extracted — extract on demand. Haiku subagents (both Bash and general-purpose types) cannot access filesystem in this env — don't bother farming file searches to them.
- 2026-02-23T21:00:00Z [feat]: logos live in two places — docs/assets/logos/ (GitHub Pages / source of truth) and north/assets/logos/ (nginx build context). Must keep in sync when adding new logos. Nginx Dockerfile copies north/assets/ → /var/www/html/assets/. Decks reference assets/logos/... as relative path.
- 2026-02-23T21:30:00Z [fix]: RH logo scaling formula for 2-line logos: display_height = target_hat_px * (svg_height / single_line_height). Single-line RH logos are ~244px tall in viewBox. Ansible AAP is 350px (2-line). At target 44px hat: Ansible needs 63px display height (44*350/244). Width follows: 63 * (1149/350) = 207px.
- 2026-02-23T21:45:00Z [fix]: GRC deck slide 6 fully aligned. Logo column 210px (driven by Ansible 2-line width). All description text starts at same x. Ansible 63px height, all others 44px.
- 2026-02-25T13:05:00Z [config]: CLAUDE.md now has explicit Startup Protocol requiring all memory MDs to be read and MCP tools checked before responding. Triggered by Jim's frustration at Gmail MCP being ignored 4+ times despite being installed and configured.
- 2026-02-26T04:28:33Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml

- 2026-02-26T05:00:00Z [fix]: job-coach narration audio was 404 on cluster — MP3s existed in docs/audio/job-coach/ but were never copied to north/stage/audio/job-coach/. Fixed by copying all 8 MP3s and rebuilding north-nginx.
  RECONSTITUTION (if ROSA/cluster is rebuilt):
  1. mkdir -p north/stage/audio/job-coach
  2. cp docs/audio/job-coach/*.mp3 north/stage/audio/job-coach/
  3. cd north && oc start-build north-nginx --from-dir=. --follow
  4. oc rollout restart deployment/north-nginx
  Audio source of truth: ohc-sap-demo/docs/audio/job-coach/ (8 slides, ~1.3MB)
- 2026-02-26T05:15:00Z [fix]: brian-chores.html was in docs/ only, not north/stage/. Demo slide 8 iframe loading blank. Fixed by cp docs/brian-chores.html north/stage/ + rebuild north-nginx. Reconstitution: same cp + oc start-build north-nginx --from-dir=north/ --follow.
- 2026-02-26T14:47:27Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2026-02-28T14:00:00Z [fix]: westtrax-kpi-appliance bootstrap proven. Fixes applied: ansible.cfg for user-1001 tmp dirs, GRANULARITY default M, dry_run guards on RFC param asserts in job_submit+job_poll, job_count/job_name facts promoted from job_submit to be available in job_poll+deliver, tp rc [0,4,8], role meta dependencies cleaned. DRY_RUN=true full pipeline: S→S→R→R→R→F, zip delivery, exit 0.
- 2026-03-06T18:25:14Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2026-03-06T18:25:21Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml
- 2026-03-06T18:26:15Z [state]: update_state.sh wrote ENVIRONMENT.md + INVENTORY.yaml

== CHANGELOG.md (tail) ==
- 2026-03-05T06:00:00Z [add]: SAPInsider_2026_Run_Simplify_v7.pptx — Red Hat standardization theme. Frame: fragmentation is the enemy. One OS, one automation platform, one compliance model. AI is a workload.
- 2026-03-05T05:45:00Z [add]: SAPInsider_2026_Run_Simplify_v5.pptx — enterprise grade reframe. "AI is just another workload. We just happen to make it easy." AI framing removed from Jim's session, closer updated.
- 2026-03-05T05:30:00Z [add]: SAPInsider_2026_Run_Simplify_v4.pptx built — trust reframe, minion content (ANGI, Provider Hooks, ZDM, Kernel Live Patching), official "credibility/confidence/consistency" language, tighter visual density
- 2026-03-04T20:00:00Z [docs]: CONTRIBUTING.md, .yamllint.yaml added to ohc-sap-demo; ansible-lint + yamllint added to pre-commit hooks. Issues #89 and #90 closed.
- 2026-03-04T19:00:00Z [add]: Lab 15 MoM pushed to GitHub + Gitea, north-stage-dashboard ConfigMap patched, north rolled out, issue #100 closed.
- 2026-03-05T03:45:00Z [fix]: I-R-N pitch v2 committed — IBM label fixed to "Enterprise Trust Layer", RHEL AI added to Red Hat layer, title sharpened, railroad PTC mandate added
- 2026-03-05T03:30:00Z [add]: tools/pitches/enterprise_ai_pitch.html — I-R-N (IBM-Red Hat-NVIDIA) enterprise AI pitch created by Claude Web, committed to chloe repo
- 2026-03-05T02:04:26Z [add]: Lab 15 — Mixture of Mixtures concept card added to labs.html. GitHub repo jodonnel/mixture-of-mixtures created with 5 research issues. Concept badge CSS added. Hero stat 14→15. OHC tracking issue #100.
- 2026-03-04T00:00:00Z [add]: Lab 14 — Red Hat Lightspeed: The Art of the Possible; present-lightspeed.html (8 slides, product toggle, fire button, offline fallback); labs.html card #14 added, hero stat 13→14, Ansible filter added; GitHub issue #93 closed; pushed to GitHub
- 2026-03-03T08:00:00Z [config]: added commit body discipline to Chloe and Zoe CLAUDE.md — subject says what, body says why, bodyless commits disallowed
- 2026-03-03T07:30:00Z [fix]: RHEL9 WSL2 imported to wsl2-demo-vm as wsl2admin — fixed SYSTEM context by using SSH; fixed inbox WSL by installing standalone WSL2 2.4.4 MSI; fixed blob auth with SAS URL; ext4.vhdx confirmed, distro registered
- 2026-03-03T07:00:00Z [add]: OHC hygiene issues #89-#92 — CONTRIBUTING.md, ansible-lint, renovate, mkdocs
- 2026-03-03T06:30:00Z [fix]: 02-configure-windows.yml — replace kernel-only wsl_update_x64.msi with standalone WSL2 2.4.4 MSI; 03-install-rhel.yml — replace az vm run-command (SYSTEM) with SSH for WSL import and post-check
- 2026-03-02T08:13:00Z [add]: WSL2 Tell-Show-Tell video assembled — wsl2-demo-tst.mp4 (3:48, 1920x1080); opening-tell.html + closing-tell.html rendered via chromium headless; letterboxed SBS race (2400x700→1920x1080); concat: 55s+128s+45s
- 2026-03-02T07:08:41Z [add]: WSL2 race demo tape — wsl2-race.tape recorded clean take; Ubuntu 129s to live prompt, RHEL 47s via import; video at ~/Videos/wsl2-race.mp4
- 2026-03-01T16:00:00Z [state]: WSL2 demo recording blocked on AWS — t3.medium lacks nested virt for Hyper-V/WSL2. Pivoting to RHDP Azure (Dv3/DSv3 supports nested virt). AWS Windows instance terminated. Ansible playbook at ~/chloe/tools/aws/spin-up-windows.yml — includes OpenSSH + authorized_keys user data. UBI9 rootfs exported to /tmp/rhel9-wsl.tar.gz (209MB). Ubuntu WSL install timed at 67s on AWS before pivot.
- 2026-03-01T03:30:00Z [add]: Lab 13 — Alexa Voice Control Building Ops Skill; issue #88; labs.html hero count 10→13; deployed to ROSA
- 2026-03-01T03:15:00Z [fix]: north pod CrashLoopBackOff — alexa_skill import wrapped in try/except; ConfigMap north-app-fixed updated; pod running; /stage and /present restored
- 2026-03-01T03:00:00Z [config]: chloe-ops service account created in qr-demo-qa; 1-year token stored at ~/.kube/chloe-token; kubeconfig context chloe-ops set as default — no more manual oc logins
- 2026-02-28T22:15:00Z [state]: farm inventory added — 2 registered Katahdin ewes, 3 lambs (ram twins b.2/17, ewe lamb b.2/26), CDT vaccination urgent, register all 3 lambs via KHSI
- 2026-02-28T14:35:00Z [cleanup]: removed 5 stale nlthm kubeconfig contexts (RHDP OHC Sandbox for SAP — expired today); kubeconfig now has 2 contexts, both rosa-rvdtn (6xtzb)
- 2026-02-28T14:20:00Z [fix]: westtrax-kpi-appliance Tier 2 test passing — OAuth transport fetch proven (R900072.ABA 591B + K900072.ABA 601B from jodonnel/westtrax-transports); Dockerfile collection path + permissions fixed; 3 commits pushed to jodonnel/westtrax-kpi-appliance
- 2026-02-28T14:00:00Z [fix]: westtrax-kpi-appliance dry-run end-to-end proven — exit 0, all 5 roles (transport_drop/import/job_submit/job_poll/deliver), job_count fact propagation fixed, RFC param dry_run guards added, tp rc [0,4,8], ansible.cfg /tmp redirects
- 2026-02-28T02:30:00Z [add]: West Trax partner logos — 9 PNGs (wordmark, KPI Analyzer, brand bullets) at ohc-demo-static/assets/logos/partners/westtrax/ via GitHub Pages
- 2026-02-28T00:00:00Z [add]: shared logo pool — ohc-demo-static/assets/logos/ on GitHub Pages; 5 Reverse-RGB logos (SAP co-brand, OpenShift, RHEL, AAP, RH wordmark); logos.html inventory; issue ohc-demo-static#1; MEMORY.md updated
- 2026-02-27T00:38:00Z [add]: CSX edge AI OS brief — corrected HTML (/private/csx-edge-ai-brief-corrected.html) and 7-slide PPTX (/private/csx-edge-ai-brief.pptx); removed internal personnel (MacDonald/Burke/Andrew Brown), fixed bearing detector vendor (Wabtec ATLAS), stripped Internal Use Only labels
- 2026-02-26T01:31:32Z [add]: present-csx.html — 5 edge yard nodes (Miami, New Orleans, St. Louis, Boston, Milwaukee) + 8 corridors + 5 scenario pool entries; phase count 36→41; deployed to ROSA
- 2026-02-25T23:54:03Z [add]: citation modals + footnote links across deck; dashboard auto-start loop on standalone open; pushed 15 commits to GitHub + Gitea; deployed to ROSA
- 2026-02-25T23:33:57Z [fix]: S11 close — red verdict line, drop 'And', add auditor/boardroom/phone kicker; Jenn Stafford / RegScale context saved to memory
- 2026-02-26T00:15:00Z [add]: present-csx.html — Leaflet interactive map replaces static SVG. CartoDB dark/ESRI satellite/Iowa NEXRAD WX tile layers. SVG overlay for yard nodes preserves pulse/alert animations. Layer toggle (OUTLINE/SAT/WX) in map top-right. Leaflet JS+CSS vendored to /assets/.
- 2026-02-25T23:10:00Z [add]: present-csx-deck.html — kiosk mode: click anywhere/spacebar advances, R resets to S1, Escape closes modals. S10 auto-starts scenario via postMessage (pre-warmed) or ?autostart=1 (cold load). NS2 modal on S9 with full SAP National Security Services / Railroads for National Defense answer.
- 2026-02-25T23:10:00Z [add]: present-csx.html — postMessage listener (startScenario/resetScenario from deck) + ?autostart=1 param support for kiosk auto-start.
- 2026-02-25T22:52:00Z [fix]: present-csx.html — iframe load time: removed CDN us-atlas fetch from buildMap() (was ~2MB on every load), added iframe detection to skip cinematic intro when embedded. present-csx-deck.html — iframe pre-warms on slide 9 instead of 10.
- 2026-02-25T22:52:00Z [fix]: arch-51.svg — all three column header subtitle lines moved to y=94 (were y=100, outside 30px header rect causing overlap with Purdue level labels).
- 2026-02-25T22:38:00Z [fix]: present-csx.html — full-width map layout (removed right panel column). Live feed + WO card + Run/Reset buttons moved into semi-transparent overlay on right side of map SVG. Scenario pool expanded to 24 events (mixed reporting marks: CSXU/BNSF/UP/NS/CN/TTX/NOKL/KTTX/ATSF), randomized 6-pick per run.
- 2026-02-25T22:15:22Z [fix]: arch-51.svg — Purdue Model level labels replace TIER 1/2/3 (Levels 0-3 OT Layer / Level 4 IT Operations / Level 5 Enterprise). DMZ crossing labeled "L3.5 DMZ / OT-IT Boundary". Component-level badges added (Level 0-1 / Level 2 / Level 3).
- 2026-02-25T22:15:22Z [fix]: present-csx.html — yard map SVG preserveAspectRatio="none" + height:100% so map fills available space (E-W stretch permitted).
- 2026-02-25T20:55:00Z [fix]: present-csx-deck.html — S6 competitive table removed entirely, replaced with 5 customer-positive capability cards + official product logos (AAP, OpenShift, RHEL Reverse). All competitor refs scrubbed. "RHEL for Edge" → "Red Hat Device Edge" throughout. S9 Q4 and S11 cleaned. Committed 2ee1fd6.
- 2026-02-25T20:40:30Z [deploy]: present-csx-deck.html — 11-slide tell-show-tell rewrite. Both stories (regulatory + technical). S2 Northeast Blackout, S3 East Palestine, S4 Mandate, S5 CSX Exposure, S6 Competitive (no vendor names), S7 Architecture, S8 Stack, S9 Proof Points, S10 Live Demo, S11 Close. Deployed ROSA, committed f85525d.
- 2026-02-25T21:40:00Z [fix]: present-csx-deck.html — brand team fixes: 6 official Red Hat SVG icons replace emoji (S4), co-brand SVG replaces text badges (S1/S6), copy fixes (eyebrow, S6 headline, S3 subhead, S2 verdict, FIPS caveat, close line typography), Tech Preview callout prominent
- 2026-02-25T19:18:32Z [deploy]: present-csx-deck.html — 6-slide OHC Lab 12 CSX presentation live at /present-csx-deck
- 2026-02-25T19:06:14Z [deploy]: present-csx.html — cinematic intro (2003 blackout + East Palestine) + Run Scenario + Reset + yard click modal
- 2026-02-25T17:30:00Z [add]: CSX Edge AI demo — added /csx/bearing-anomaly POST endpoint + /present-csx GET route to app.py. Created transport/csx/ (cabana_simulator.py, sap_pm_adapter.py, sap_mock_server.py, __init__.py). Created north/stage/present-csx.html (36-yard rail map, live SSE anomaly feed, SAP work order panel). Added csx→/present-csx to SHORT_URLS. Strategy brief written to docs/CSX-EDGE-AI-STRATEGY-BRIEF.md.
- 2026-02-25T17:30:00Z [docs]: CSX Edge AI OS strategy brief — 11-section Red Hat internal brief covering Ubuntu vs RHEL for Edge competitive analysis, TSA/FIPS regulatory angle, Tech Preview handling, engagement sequence, discovery questions, objection handling, demo script.
- 2026-02-24T05:16:18Z [fix]: present-lab06-mercedes.html — h2 headings rendering red on all slides. Root cause: .big CSS class had no color property. Fix: added color:var(--text) to .big rule + inline style on all h2 S2–S6. Committed f0c8a05.
- 2026-02-24T07:00:00Z [fix]: present-lab06-mercedes.html — Sonnet debate round: 4 code bugs fixed (fetchLiveData /events→/log, field paths payload.data.*, fetchLiveData called on S3 enter, WO year dynamic, timestamps UTC ISO). Strategic changes: S3 architecture disclosure line, S4 notification-first parenthetical, S5 "100% coverage"→"0 manual entry", S5 resale→warranty/audit/TCO framing, S6 close rewritten customer-first. CSS fix: SERVICE\nLIMIT → SERVICE\A LIMIT. Deployed.
- 2026-02-24T06:00:00Z [fix]: present-lab06-mercedes.html — debate-driven fixes: Mercedes badge removed from S1 (account team decision), VIN redacted to W1NKM4HB0···482 everywhere, SAP TM → SAP Fleet Management (EAM) in S3+S6, EIC → iFlow in S4 event flow, Fleet Maintenance Pool → Work Center WC-FLEET-POOL, WO delay 1800→800ms, S5 ledger counter animates 0→4 on enter. Deployed to rosa-rvdtn/qr-demo-qa.
- 2026-02-24T05:45:00Z [state]: Smartcar tier brief — Build plan ~$2/vehicle/mo unlocks scheduled webhooks (hourly push), batch requests, engine oil life, tire pressure, write endpoints. Key upgrade: webhook removes need for polling loop at booth. Oil life = better PM trigger story than odometer alone.
- 2026-02-24T05:00:00Z [add]: present-lab06-mercedes.html — 6-slide customer presentation for Connected Fleet Intelligence lab. Live Smartcar telemetry (odometer, fuel gauge arc, GPS route animation Tarrytown→Sleepy Hollow). SAP PM work order trigger button (simulates maintenance threshold crossing). Asset ledger timeline tied to VIN. Fleet scale close (500 vehicles, 0 manual logs, 100% EAM coverage). Deployed to rosa-rvdtn/qr-demo-qa.
- 2026-02-24T04:15:00Z [feat]: present-piport.html — full debate-driven polish cycle. 6→7 slides. Added S5 'Three gates to production-ready' (Zero/&lt;2s vs 12s typical/Live). S4 confirmed node red→blue. S3 third stat replaced (100% K8s→6 mo. migration window). S7 closer rewritten: customer outcome, no seller language. 'deal' removed throughout. S2 plain-language translation added for non-specialist buyers. S3 callout: 'Every SAP Edge problem has a Red Hat OpenShift solution. Every PI/PO migration has a proven path.' Deployed build #32 to rosa-rvdtn/qr-demo-qa.
- 2026-02-24T04:15:00Z [add]: DEBATE repo — 2-round AI debate process (Haiku x6 then Sonnet x2) used to polish piport deck. Pattern: Haiku for breadth/speed, Sonnet for depth with Haiku findings baked in. Sonnet caught buyer-language issues Haiku missed. Jim caught tone issue ('you're already late') that neither model flagged — PS/SI capacity is the real constraint, not customer willingness.
- 2026-02-23T12:00:00Z [feat]: blackjack-deck.html rebuilt — 7 slides (removed Act I caption), fade-to-black transitions, v1+v2 video auto-advance on ended. Committed to ohc-sap-demo docs/. GH issue #78 (closed).
- 2026-02-23T12:05:00Z [feat]: job coach deck — full narration pipeline. 8 MP3s via edge-tts at +20% rate. Andrew Neural (slides 1,3,5,7) + Ava Neural (slides 2,4,6,8). Kiosk mode: slides advance only after narration ends. Click-to-start overlay for browser autoplay policy. Key bug: audios array must init inside overlay click handler, not at parse time. GH issue #74 (closed).
- 2026-02-23T12:10:00Z [feat]: job coach slides 3+4 — timed diagram reveals synced to narration. CSS build-item/shown pattern. Timers cleared on slide exit. GH issue #75 (closed).
- 2026-02-23T12:15:00Z [feat]: job coach deck — Brian's Chores iframe embedded as slide 8 (between Live Demo intro and Close/Impact). Phone mockup, no narration, manual advance only, iframe reloads on entry. GH issue #76 (closed).
- 2026-02-23T12:20:00Z [state]: ROSA cluster rosa-rvdtn confirmed up. Token refreshed. qr-demo-qa: north+north-api+north-nginx+south-ui+redis all Running. Routes north + south-ui both 200.
- 2026-02-23T12:25:00Z [bug]: nginx stage out of sync with docs/. present-job-coach.html stale (21KB cluster vs 28KB local), brian-chores.html missing from cluster, audio/job-coach/*.mp3 missing from cluster. GH issue #77 (open).
- 2025-12-15T18:42:20Z: Initialized ENVIRONMENT.md & INVENTORY.yaml from /home/jodonnell/chloe/DIAG/reports/selective_2025-12-15T18:39:06Z.txt.

- 2025-12-17T08:04:04Z [obs/meet/firefox]: RHEL 10 Wayland+PipeWire: Firefox may not enumerate OBS v4l2loopback virtual camera in Google Meet. Fix: about:config media.webrtc.camera.allow-pipewire=false; restart Firefox; re-allow camera permission for meet.google.com. Verify /dev/video10 name and OBS holds it via fuser.
- 2025-12-17T08:14:28Z [cuda]: CUDA toolkit confirmed installed (cuda-toolkit-13-0 RPMs; /usr/local/cuda-13.0; nvcc V13.0.88). Updated state detection and PATH.
- 2025-12-17T08:18:17Z [fix]: Fixed update_state.sh stray 'BASH' delimiter line; ensured CUDA PATH via /etc/profile.d/cuda.sh; ensured chloe_mail helper in ~/.bashrc; ran update_state.sh.
- 2025-12-22T03:05:01Z [cuda/insights]: Removed global LD_LIBRARY_PATH from /etc/profile.d/cuda.sh; added /etc/ld.so.conf.d/cuda.conf + ldconfig. cuda.sh now sets PATH only (prefers /usr/local/cuda/bin).
- 2026-02-14T15:37:53Z [deploy]: Exported live qr-demo-qa Deployments, Services, Routes, ConfigMaps into deploy/base/ as clean manifests. Wrote deploy/base/kustomization.yaml and deploy/overlays/qa/kustomization.yaml. Validated with oc kustomize build (462 lines, no errors).
- 2026-02-14T16:11:18Z [cleanup]: Repo split — moved OHC demo code (north/, deploy/, transport/, tests/) to ~/ohc-sap-demo. Removed demo READMEs and dashboard.html.old. Wrote new Chloe-focused README.md. ~/chloe is now governance-only.
- 2026-02-14T16:43:19Z [cleanup]: Phase B cluster cleanup on qr-demo-qa. Deleted orphaned south-hello route+svc, broken south-send job, zman-demo deployment+svc+route. Patched revisionHistoryLimit to 3 on all deployments.
- 2026-02-14T16:54:34Z [cleanup]: Deleted stray north-route (no TLS, created today via ad-hoc oc expose). Not documented by any prior session. Namespace now has exactly 3 routes, all TLS edge.
- 2026-02-14T17:04:10Z [code]: Synced live /stage dashboard HTML into north/app.py (mute button, audio element, SSE event JSON, pod/transport tiles). Fixed chime overlap: cloneNode() instead of replaying single audio element. Commit fd8f829.
- 2026-02-14T17:10:00Z [license]: Added Apache-2.0 LICENSE to ohc-sap-demo. Commit 1d252d3.
- 2026-02-14T17:30:00Z [github]: Evaluated all jodonnel GitHub repos. Archived: OpenShift-with-SAP, my-brand, SAP-training-and-demos, sap-tower-projects, chicken-chores, SAP-SA-Training-and-Demo-Content. Unarchived: rhel-for-students (per user request). Active repos: ohc-sap-demo, rhel-for-students, plus 5 sap-linuxlab forks.
- 2026-02-14T17:35:00Z [github]: Authenticated gh CLI via SSH (id_ed25519). GH_CONFIG_DIR=/home/jodonnell/.config/gh required for non-interactive shells.
- 2026-02-14T18:00:00Z [quality]: Tier 1 repo scaffolding on ohc-sap-demo (redhat-cop alignment). Added: .github/ (CONTRIBUTING, CODE_OF_CONDUCT, PR template, issue templates), CODEOWNERS, SECURITY.md. Expanded .gitignore with secrets/credentials/IDE patterns. Overhauled README (architecture, quick start, layout, related projects). Added topic tags (openshift, sap, hybrid-cloud, demo, flask, kustomize, event-driven, red-hat). Commit fc90938.
- 2026-02-14T22:30:00Z [quality]: Tier 2 complete on ohc-sap-demo. Added .pre-commit-config.yaml (gitleaks, formatting hooks), .yamllint, .github/workflows/lint.yml (yamllint + python syntax + kustomize validation on PRs/pushes). Created first semver tag v0.1.0. Fixed yamllint CI failure (trailing blank lines in 3 manifests). Commits 4807890, ffbbc93.
- 2026-02-14T22:35:00Z [pages]: Enabled GitHub Pages on ohc-sap-demo (source: docs/ on main). Architecture diagram live at https://jodonnel.github.io/ohc-sap-demo/architecture.html. Synced through v8 (clickable device class toggling).
- 2026-02-14T22:40:00Z [github]: Authenticated gh CLI (SSH, id_ed25519). Requires GH_CONFIG_DIR=/home/jodonnell/.config/gh in non-interactive shells.
- 2026-02-15T10:20:00Z [test]: Full e2e south→north test passed. All 5 event types (tap, swipe, error, status, metric) return 200 with correct count. SSE stream delivers events in real-time (canary probe confirmed). CORS headers allow cross-origin POST from south-ui. Latency ~120ms per event (workstation → ROSA AWS).
- 2026-02-15T10:45:00Z [cleanup]: Deleted south-hello-site from cluster and repo. Removed deployment, service, route from qr-demo-qa. Removed 3 manifests from deploy/base/ and updated kustomization.yaml. Namespace now: 2 components (north, south-ui), 2 routes, both TLS edge. Commit 391c276.
- 2026-02-15T11:55:00Z [deploy]: Deployed wumpus game (south-ui), redesigned stage dashboard, and QR code page to cluster. Updated north-app, north-stage-dashboard, south-ui-html ConfigMaps. Added /south-ui volume mount to north deployment. New routes: /play (wumpus), /stage (file-served dashboard), /qr (SVG QR code pointing to /play). Fixed app.py to use absolute paths for container mounts. Commits a39f799, e158d8d.
- 2026-02-15T12:15:00Z [deploy]: Added /pod-name endpoint to app.py. Dashboard fetches pod name dynamically. Updated ConfigMaps and restarted north pod. All routes verified (200): /stage, /play, /qr, /pod-name, /state, /ingest. Pod: north-5bb567bf8f-brrrs. Commit 9fa2eae.
- 2026-02-15T14:50:00Z [deploy]: Wumpus v3 deployed (room tasks, 3-task win gate, kickback on unprepared entry). Commit f0dc6cf.
- 2026-02-15T14:55:00Z [feat]: Telemetry aggregation + /log endpoint + Audience Telemetry tile on stage dashboard. app.py now aggregates battery/network/locale/device telemetry from CloudEvents. /telemetry returns stats, /log returns last 200 events. Dashboard has 4-column tile grid with 5s telemetry polling. All ConfigMaps updated, both deployments restarted. Verified: /telemetry returns data, /log captures events. Commit 651026a.
- 2026-02-15T15:30:00Z [feat]: Live presentation app deployed at /present (v1-v5 iterations from Claude web). 2000+ line self-contained HTML with inlined architecture SVG, QR code SVG, built-in event simulator, SSE + /telemetry polling, 10 slides. Generated QR code page at /qr-present. Commits 3d840c8 through 4025de5.
- 2026-02-15T16:00:00Z [fix]: south-ui now POSTs to absolute north URL for cross-origin ingest. Phones access south route naturally as edge devices; relative /ingest was hitting wrong container. CORS already enabled. Commit de2a750.
- 2026-02-15T17:00:00Z [feat]: Red Hat seller presentation variant at /present-rh. Same demo, OHC + Partner comp framing for RH sellers. Red Hat fonts (Display, Text, Mono) applied across all UIs (dashboard, south-ui, both presentations). Commit d99b8bd.
- 2026-02-15T17:30:00Z [docs]: README overhauled for sharing — architecture diagram, URL map, stack, "Built with" credits (Claude Code, Claude Web, ChatGPT). Commit 1e32c08.
- 2026-02-15T21:55:00Z [fix]: Dashboard, /present, /present-rh now hydrate from /state on load — counter seeds from server state instead of starting at zero. Resolves GitHub issue #2. Commit 13a910a.
- 2026-02-15T21:52:00Z [github]: Seeded 9 GitHub issues from session backlog. Set repo description, homepage URL, disabled empty wiki. Created v0.1.0 GitHub Release with full changelog.
- 2026-02-15T22:10:00Z [docs]: Added wumpus game screenshot to README (docs/img/). Headless browser can't capture CSS-animated dark UIs (dashboard, presentation render as dark rectangles). ConfigMap now requires `oc replace` instead of `oc apply` (too large for annotation — tracked as issue #9).
- 2026-02-15T22:15:00Z [state]: north-stage-dashboard ConfigMap now has 5 keys: dashboard.html, qr.html, present.html, present-rh.html, qr-present.html. north-app ConfigMap has app.py with 11 routes: /ingest, /events, /state, /stage, /play, /qr, /qr-present, /present, /present-rh, /telemetry, /log, /pod-name, /assets.
- 2026-02-16T00:30:00Z [feat]: Presentations updated — architecture slide now uses iframe to GitHub Pages interactive diagram (drop inline SVG). Commit e3e696b.
- 2026-02-16T01:00:00Z [feat]: Passive device fingerprinting — 25+ signals without permission prompts. classifyDevice() (phone/tablet/laptop), GPU via WebGL, performance tiering, timezone, battery/memory opportunistic. North aggregates by device class, OS, browser, GPU, tier. /telemetry returns full breakdown. Issue #11 (closed). Commit ed0f26a.
- 2026-02-16T01:30:00Z [fix]: Removed false Lenel/EIC claims from splash and end screens. Text now accurately describes CloudEvents on OpenShift. Issue #13 (closed). Commit 0f0e205.
- 2026-02-16T02:00:00Z [feat]: Narrative-driven investigation (INC-2026-0217). All 12 rooms rewritten as intrusion response — lost badge, camera tamper, SSH brute force, rogue device, fiber tap, BMS credential reuse, sensor tamper, active vault breach. 10 event classes: incident, compliance, network, surveillance, building, physical, access, sensor, alert, telem. Tasks added to Main Corridor and Vault. CloudEvents carry eventclass field. Dashboard shows event class breakdown. Issue #12 (closed). Commit d6719e5.
- 2026-02-16T02:30:00Z [issues]: Dashboard redesign issues opened: #14 (umbrella), #15 (human-readable events), #16 (event class visualization), #17 (device visualization), #18 (activity feed/timeline). Awaiting input from Claude web and Chloes.
- 2026-02-16T03:00:00Z [feat]: Stage dashboard redesign from Claude web — "Edge Operations Center" SOC layout. 3-column grid: rolling activity feed with human-readable event descriptions (left), hero counter + animated event class bars (center), device mosaic with pop-in icons (right). Hydrates from /log + /state on load. SSE-driven real-time updates. Built-in simulator for offline. Issues #14-#18 all closed. Commit 8500a7f.
- 2026-02-16T04:00:00Z [deploy]: Bulk ship from Claude web (ohc-ship.zip). Updated: present.html (clickable QRs, state fetch, touch swipe), present-rh.html (same + OHC/Partner framing), dashboard.html (full SOC redesign), south-ui/index.html (contrast boost, red button, 32px minimap). New: present-util.html (SAP for Utilities, NERC CIP, Metcalf). Added /present-util route to app.py. All 6 routes verified (200). Commit b76b042.
- 2026-02-16T04:00:00Z [issues]: 8 retroactive issues created and closed (#19-#26): presentation web app (#19), RH seller variant (#20), utilities variant (#21), game rename (#22), contrast fix (#23), clickable QRs (#24), interactive architecture (#25), Red Hat fonts (#26). Session total: 16 issues closed (#11-#26). 8 open issues remain (#1, #3-#9).
- 2026-02-16T04:00:00Z [feat]: Kiosk mode added to present-index. GitHub Pages landing page added. OHC Labs feature voting app live at /labs (localStorage voting). PI/PO EOL migration demo at /present-piport. Mercedes-Benz connected vehicle relay in transport/mercedes/. MII + substation presentation slides + arch SVGs added. Issues #40, #41, #51 closed.
- 2026-02-16T04:00:00Z [feat]: Issues #42–49 batch closed: GRC killchain scenario, shop-floor defect→QM, contractor overcharge detection, OpenBlue→SAP PM, MII/ME coexistence, blackjack presentation. Meta Glasses Job Coach demo added at /present-job-coach. /present-mii and /present-substation routes live.
- 2026-02-19T14:00:00Z [deploy]: PRODUCTION ARCHITECTURE CUTOVER COMPLETE. Zero-downtime migration from ConfigMap-based Flask to nginx+Redis+Flask. qr-demo-qa now runs: nginx pod (static files, 2Gi PVC), north-api (2 Flask/gunicorn replicas), redis (1Gi PVC). Old north deployment scaled to 0 (rollback available). 48-hour window now elapsed — safe to delete. Tags: pre-cutover-20260219-084041, post-cutover-20260219-091200.
- 2026-02-19T14:00:00Z [fix]: Cutover resolved 7 field issues: S2I CMD override (→python:3.11-slim), nginx permissions (→nginx-unprivileged), PVC multi-attach (nginx scaled to 1), missing API endpoint location blocks, ExternalName 503 (deployed direct to qr-demo-qa instead), image pull namespace mismatch (BuildConfig in qa), missing /play (south-ui/index.html→play.html on PVC).
- 2026-02-19T14:00:00Z [fix]: Post-cutover fixes: blackjack placeholders→actual videos (e219d90), nginx try_files for .html extension handling (6670451), job-coach color corrections per CW spec (e2ffe66, 6910389), Wumpus minigame responsive layout for mobile (d20b546). Issues #52, #53 closed.
- 2026-02-19T22:00:00Z [feat]: Mercedes vehicle relay: mock_relay.py generates realistic fake vehicle events (fuel, odometer, locks, tire pressure, location, battery). spec_relay.py attempts real Vehicle Specification API — blocked at 401 (Business tier approval pending). Fixed /ingest nginx routing to accept events. Commit 6f15c1e.
- 2026-02-21T02:21:00Z [state]: Chloe brain catchup — CHANGELOG + MAILBOX updated to reflect all work since 2026-02-16.
- 2026-02-21T07:30:00Z [deploy]: nginx+Redis+Flask cutover complete in qr-demo-qa. Route north → north-nginx (HTML baked into image, no ConfigMaps). north-api 2 replicas gunicorn+Redis. 4 field issues: unnamed service port (503, 2min fix), Haiku subagent Bash perms, binary build context mismatch, labs.html 600 perms (403). All resolved. All endpoints 200.
- 2026-02-22T16:00:00Z [add]: Brian's Chores app added to ohc-sap-demo. docs/brian-chores.html — phone-first task coach for Brian (IDD), step-by-step audio prompts via edge-tts Jenny Neural MP3s (17 files in docs/brian-audio/), Atkinson Hyperlegible font, morning/evening modes, offline-capable. New slide added to present-job-coach.html (slide 6 of 7) with live demo link.
- 2026-02-23T18:00:00Z [fix]: present-job-coach.html nav buttons fixed (prev()/next() calls were corrupting global `current` before goTo()). Brian's Chores iframe audio bleed fixed — iframe src deferred to slide entry, blanked on exit. Slide 3 timing: cap-1 5500ms, cap-2 11000ms, cap-3 15000ms.
- 2026-02-23T18:15:00Z [add]: SAP Insider Vegas 2026 research. Cross-referenced Jim's pods (SOUTHEAST_ENT_NC_SC + EAST_COMM_CORP_POD05) against SAP Insider reg report, Danielle's build-the-business file, Sontice's account list, East Region CY26 accounts. Top targets: Bridgestone, AutoZone (Sontice); ABB, Owens Corning, Ingersoll Rand (Danielle). Internal reg report: 9 RH attendees, Jim as speaker (Tue w/ Zman, Wed solo), Bellagio Boardroom Tue-Thu.
- 2026-02-23T18:20:00Z [add]: Outreach emails drafted: email_sontice_tagalk.txt + email_danielle_connochie.txt in ~/ohc-sap-demo/. Brian James briefing email drafted with full pod target list. Vegas_SAP_Insider_Targets_2026.xlsx created with color-coded tiers (red/orange/yellow), rep, account, renewals, Q1 pipeline, SAP confirmed, Vegas tier, why, action columns. Legend tab included.
- 2026-02-23T19:30:00Z [deploy]: shipped present-grc-sap-nist.html to cluster. Renamed from v2 suffix (no version needed — first version). Fixed /present-grc 404 via nginx ConfigMap redirect → /present-grc-killchain. Diagnosed and fixed 3 root causes: (1) BC dockerfile paths not set, (2) oc start-build --from-dir=. was uploading wrong cwd, (3) deployment not restarting after image rebuild. All GRC routes now 200.
- 2026-02-23T20:15:00Z [add]: organized ~/brand-assets/ from Downloads — 12 logo zips extracted, 3 large zips moved unextracted. Copied 15 official Red Hat SVGs into ohc-sap-demo/docs/assets/logos/ (co-brand, product, endorsement). Committed and pushed to GitHub.
- 2026-02-23T21:00:00Z [feat]: official Red Hat SVG logos dropped into GRC deck. SAP Platinum co-brand (Reverse) on slides 1+7. RHEL, Ansible AAP, OpenShift product logos on slide 6. Logos mirrored into north/assets/logos/ for nginx build. All served from cluster.
- 2026-02-23T21:30:00Z [fix]: GRC deck slide 6 logos brand-compliant. Fixed 44px hat alignment across all rows. Ansible 2-line logo scaled to 63px (44*350/244) so hat+text match single-line logos. West Trax placeholder badge centered under SAP co-brand in row 4. 200-210px logo column.
- 2026-02-23T21:45:00Z [fix]: GRC slide 6 — uniform 210px logo column, description text left-edge aligned across all rows.
- 2026-02-25T13:05:00Z [config]: Added Startup Protocol to CLAUDE.md — mandatory memory file reads + Chloe persona adoption + MCP tool check on every session
- 2026-02-26T05:00:00Z [fix]: job-coach narration audio deployed to north-nginx (slide-1..8.mp3, 1.3MB)
- 2026-02-26T06:30:00Z [cleanup]: both repos clean — ohc-sap-demo GitHub+Gitea synced, chloe Gitea synced, CSX brief scrubbed from git history, spotify-ctl gitignored
- 2026-02-26T06:00:00Z [security]: CSX-EDGE-AI-STRATEGY-BRIEF.md removed from public GitHub — marked internal, contained RH personnel/pipeline/competitive data. git filter-repo + force push. File in ~/private/.
- 2026-02-26T05:15:00Z [fix]: brian-chores.html deployed to north/stage — demo slide 8 iframe was blank
- 2026-02-28T14:00:00Z [fix]: westtrax-kpi-appliance dry-run proven end-to-end — exit 0, all 5 roles (transport_drop, transport_import, job_submit, job_poll, deliver), podman run --rm -e DRY_RUN=true
<\!-- /chloe-sync-v1 -->
