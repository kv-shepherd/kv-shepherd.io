# kv-shepherd.io

> Go Vanity Import server for KubeVirt Shepherd

This repository hosts the static files that power the Go vanity import for `kv-shepherd.io/shepherd`.

## What is Vanity Import?

Go modules can use custom domain names as import paths instead of Git hosting URLs. This decouples the module path from the Git hosting provider, enabling:

- **Migration flexibility**: Move repositories without breaking downstream users
- **Brand consistency**: Use your project domain in import statements
- **Professional appearance**: `import "kv-shepherd.io/shepherd"` vs `import "github.com/kv-shepherd/shepherd"`

## How it Works

When `go get kv-shepherd.io/shepherd` is called:

1. Go toolchain requests `https://kv-shepherd.io/shepherd?go-get=1`
2. This server returns HTML with `<meta name="go-import">` tag
3. Go follows the tag to fetch code from `github.com/kv-shepherd/shepherd`

## Files

| File | Purpose |
|------|--------|
| `index.html` | Root domain, redirects to GitHub org |
| `shepherd/index.html` | Vanity import for `kv-shepherd.io/shepherd` |

## Deployment

This site is deployed to **Cloudflare Pages** and bound to `kv-shepherd.io`.

## Adding New Modules

To add a new module (e.g., `kv-shepherd.io/shepherd-ui`):

1. Create `shepherd-ui/index.html` with appropriate meta tags
2. Push to main branch
3. Cloudflare Pages will auto-deploy

## References

- [Go Modules - Custom Import Paths](https://go.dev/ref/mod#vcs-find)
- [ADR-0016: Go Module Vanity Import Strategy](https://github.com/kv-shepherd/shepherd/blob/main/docs/adr/ADR-0016-go-module-vanity-import.md)

---

*Part of the [KubeVirt Shepherd](https://github.com/kv-shepherd/shepherd) project.*
