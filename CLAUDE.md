# CLAUDE.md — build notes for two-person-rule

Part 5 of the macula-demos OT series. Build last; it reuses part 1's freezer sim and
gateway.

## The one claim

Dynamic authority: high-risk commands require two distinct operator nodes; approvals can be
revoked, and the controller never sees a half-approved command.

## Open decisions (resolve before/at start of build)

1. **Policy shape**: which procedures require two signers (e.g. `ot/start_freezer_defrost`
   and target changes beyond a threshold), declared where — per-procedure capability policy
   vs a gateway-side policy map.
2. **Approval transport**: where pending commands live (gateway state), how approvals are
   sent (a separate `ot/approve_command` capability? signed approval facts over pubsub?),
   and how the dashboard renders a pending command with its signers.
3. **Enrollment and revocation**: how the second operator enrolls (the realm fixture granting
   two operator nodes) and how revocation is expressed mid-demo. Decide whether approvals
   already given by a revoked operator are invalidated retroactively — the demo beat works
   best if the revoked approval stops counting.
4. **Realm**: whether this repo can use real `macula-realm` membership by build time; if
   not, the lab fixture stands in, stated honestly.
5. **Scope honesty**: this proves an approval workflow in the gateway, not a consensus or
   cryptographic threshold scheme.

## Carry-over rules (from part 1)

Same fixture caveats, sealed payload vs visible routing metadata, in-memory state caveats
(the approval ledger starts in memory; state its durability honestly), honest
`WHAT_THIS_PROVES.md` — all carry over unchanged.

## Do not

- Do not weaken or change part 1's mesh-side policies (sealing, callers, command guard)
  except where the dual-control claim requires the write policy to change.
- Do not touch the sibling repos.
