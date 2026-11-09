# two-person-rule

Part 5 of the macula-demos OT series: dangerous commands need two operators, not one.
A defrost is proposed, signed by two different operators, and only then executed —
and a revoked operator's approval stops counting the moment it is revoked.

**Status: planned.** Nothing is built yet. Build notes are in [CLAUDE.md](CLAUDE.md).

## The one claim this demo makes

Authority is dynamic, not a boot-time allowlist: a high-risk command (defrost) requires two
distinct operator nodes to approve it, approvals can be revoked mid-flight, and a command
that loses an approval never reaches the controller.

## Story

Part 1's gateway let one operator node do anything. Here the same gateway learns a policy:
`defrost` and target changes beyond a threshold need two signers. The dashboard shows a
pending command with its signers; operator B's approval lands and the command runs. Then:
operator A alone is refused; a third, revoked operator's approval is refused mid-demo. The
controller never sees a half-approved command.

## Planned layout

```text
apps/
  freezer_controller/   From part 1 (sim + audit)
  ot_gateway/           From part 1 + approval ledger, per-procedure policy, revocation
  admin_ui/             From part 1 + pending-command view, approve/revoke buttons
deploy/                 compose.yml, station/config.json
docs/                   DEMO_SCRIPT.md, WHAT_THIS_PROVES.md
scripts/                mesh-demo.sh, probes, reset
assets/                 demo.mp4, demo-poster.png (made when the video is asked for)
```

## The series

| # | Repo | One claim |
|---|------|-----------|
| 1 | [freezers-on-mesh](https://github.com/macula-demos/freezers-on-mesh) | A retrofit removes the inbound path and moves authority to the mesh |
| 2 | [warehouses-on-mesh](https://github.com/macula-demos/warehouses-on-mesh) | Federation: sealed cross-site calls with no inbound ports anywhere |
| 3 | [pumps-on-mesh](https://github.com/macula-demos/pumps-on-mesh) | The same gateway pattern behind a real Modbus TCP controller |
| 4 | [verifiable-coldchain](https://github.com/macula-demos/verifiable-coldchain) | Signed reading history an auditor verifies without Macula |
| 5 | **two-person-rule** | Dual control with dynamic enrollment and revocation |

## License

Apache-2.0. See [LICENSE](LICENSE).
