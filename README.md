# CBSUA Frappe Framework

CBSUA-maintained fork of the [Frappe Framework](https://github.com/frappe/frappe). This repository supplies the framework layer used by the CBSUA Helpdesk application image and by other Frappe applications in the CBSUA ecosystem.

## Purpose and boundaries

Frappe Framework is the underlying application platform: it provides the site/bench model, DocTypes and database-backed application layer, authentication and permissions, APIs, background jobs, and core Desk facilities.

This repository is a **shared platform dependency**, not the CBSUA ticketing product. CBSUA Helpdesk business behavior belongs in the Helpdesk fork or a dedicated CBSUA extension where appropriate. Avoid placing Helpdesk-specific behavior in this framework fork unless it is genuinely a reusable framework-level requirement.

## Where it is used

- **CBSUA Helpdesk deployment:** included in the combined image built by [cbsua-app-helpdesk-deployment](https://github.com/AgeReapor/cbsua-app-helpdesk-deployment).
- **Local development:** installed into a bench managed by [CBSUA Pilot](https://github.com/AgeReapor/cbsua-app-pilot).
- **Other Frappe applications:** may use this fork when their runtime baseline intentionally targets the CBSUA-maintained framework changes.

The deployment repository's workflow and `config/source-lock.json` define the actual framework ref and commit used for a published image. Branch names such as `develop` are moving references; use immutable commit SHAs or release tags for reproducible releases.

## Local development

Pilot manages the bench and its Frappe runtime. Typical setup begins with:

```bash
pilot new cbsua-app-bench
pilot -b cbsua-app-bench start
```

Follow the Pilot setup wizard and the CBSUA deployment repository's compatibility baseline. Do not initialize a bench from an unrelated upstream branch and then install apps built for a different framework line.

## Compatibility and release discipline

Frappe is a foundational dependency. Before changing or promoting this fork:

1. Review the framework version and Python/Node/database requirements.
2. Check compatibility with the selected Helpdesk and Telephony refs.
3. Run framework checks and the app-level test suite in a clean bench.
4. Build the combined image and validate site creation, migrations, assets, workers, and realtime behavior.
5. Record the exact commit in the deployment source lock.

## Upstream maintenance

Keep this fork synchronized with upstream Frappe deliberately. Document CBSUA patches, their rationale, and any upgrade implications. Avoid silently carrying unrelated upstream changes into a production image.

## References

- [Frappe Framework documentation](https://docs.frappe.io/framework)
- [Upstream Frappe repository](https://github.com/frappe/frappe)
- [CBSUA Helpdesk deployment](https://github.com/AgeReapor/cbsua-app-helpdesk-deployment)
- [CBSUA Pilot](https://github.com/AgeReapor/cbsua-app-pilot)

## License

See [LICENSE](LICENSE) for the license applicable to this fork and its upstream-derived code.
