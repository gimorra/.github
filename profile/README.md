<p align="center">
  <a href="https://github.com/gimorra"><img alt="Gimorra" src="https://avatars.githubusercontent.com/u/322532366?s=200&v=4" height="120" /></a>
  <br />
  <strong>Gimorra — autonomous offensive security agent</strong>
</p>

<p align="center">
  <img alt="A gimorra scan start to finish: a prose brief resolves into flags, recon maps the target, the agent proposes candidates and the validator confirms three." src="./gimorra-scan.gif" width="900" />
</p>

Point it at a target and it runs the engagement end to end — **recon → scan → propose PoC → prove → report**.

- **Auto-detects the target** — URL, host, domain, IP, CIDR, repo, or a prose brief.
- **One dial for aggressiveness** — `passive · lite · balanced · aggressive`.
- **Steerable** — hand it a brief (`-p "focus on IDOR"`), a target list, an API spec, or captured proxy traffic.
- **Proves its own findings** — every candidate is replayed non-destructively before it lands.
- **Source audit too** — point it at a repo instead of (or alongside) a live target.
- **Reads back** — findings, markdown/HTML reports, and a hash-chained chain of custody.
- **Bridges your proxy** — imports Burp or Caido history and pushes confirmed leads back.

```bash
gimorra scan acme.test
gimorra scan acme.test -p "focus on IDOR and broken access control" --intensity aggressive
gimorra findings <id> -f md
```

Built with ♥ by [@j3ssie](https://github.com/j3ssie) · [@j3ssie on X](https://x.com/j3ssie)
