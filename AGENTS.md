# Split TON Connect manifest: rules for every change

Hosts `ton-connect-manifest.json`, Split's public TON Connect application
identity (name, URL, icon). Wallets read it at connection time, so a change is
public as soon as it is served.

## Documentation map

| Topic | Read first |
| --- | --- |
| What this repository owns, entry points | [Repository catalog: split-tonconnect](https://github.com/split-tg/split-documentation/blob/main/repositories/README.md#split-tonconnect) |
| How to orient, trace and validate a change | [Agent workflow](https://github.com/split-tg/split-documentation/blob/main/guides/agent-workflow.md) |
| Wallet tooling and consumers | [TON contracts and wallet tooling](https://github.com/split-tg/split-documentation/blob/main/architecture/ton-contracts.md) |
| XTR frontend, which loads this manifest | [Repository catalog: xtr-frontend](https://github.com/split-tg/split-documentation/blob/main/repositories/README.md#xtr-frontend) |

## split-documentation (required for every task)

Shared knowledge about Split lives in
[split-documentation](https://github.com/split-tg/split-documentation). Use it in
every task in this repository, even when the request does not mention
documentation:

1. **Before changing anything**, update your checkout of split-documentation
   (`git pull --ff-only`) and read this repository's
   [catalog entry](https://github.com/split-tg/split-documentation/blob/main/repositories/README.md#split-tonconnect) and the pages for the
   area you change (see the map above).
2. **In the same task**, update the pages your change affects: features,
   behavior, API and message contracts, configuration, deployment and operational
   procedures. Add a page when none covers the topic, and register it in its
   index. Changes that add no useful knowledge (typos, formatting, dependency
   bumps without behavior change) need no update.
3. **Publish it.** split-documentation has only `main`: commit and push there
   directly, without a pull request, after `python3 scripts/check_docs.py` and
   `git diff --check`. A task is not finished while documentation edits are
   uncommitted or unpushed.
4. **In this repository's pull request**, link the documentation commit or say
   why no update was needed.
5. **When the documentation and the code disagree**, the code on the right branch
   is the authority. Correct the page in the same task instead of following
   stale text.

Follow its [contributing guide](https://github.com/split-tg/split-documentation/blob/main/CONTRIBUTING.md) and
[agent workflow](https://github.com/split-tg/split-documentation/blob/main/guides/agent-workflow.md): keep each page's language,
link instead of copying, mark proposals and unverified assumptions, and never
write credentials or private user data.

## Branches

`main` is the only maintained branch. Branch from it and open a pull request
against it; never push to `main` directly, and merge only when asked.

## Before you finish

```bash
python3 -m json.tool ton-connect-manifest.json >/dev/null
```

Check that the `url` and `iconUrl` it names are reachable, and search the other
Split repositories for references to the manifest before changing its identity.
