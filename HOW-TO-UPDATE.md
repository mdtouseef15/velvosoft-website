# How to Update the GitHub Copy After Website Changes

This repository is a **static snapshot** of [velvosoft.biz](https://velvosoft.biz/).
It does **not** update automatically. When you change the live website, follow the
steps below to refresh the copy stored on GitHub.

---

## The big picture

```
Live site (WordPress/Elementor)  ──X no automatic link──►  Local folder  ──X manual push needed──►  GitHub
        edit in Elementor                                   re-snapshot            git push
```

- Editing the **live site** does NOT update GitHub.
- Editing the **local folder** does NOT update GitHub until a `git push`.
- Nothing is automatic. A push is always the trigger.

---

## The easy way (recommended)

1. Make your edits on the live site in **WordPress / Elementor** (`velvosoft.biz/wp-admin`) and click **Update** there.
2. Open this project in **Kiro** and simply say: **"The site changed, update GitHub."**
3. Kiro re-captures the site and pushes it for you, then confirms.

That's it. You don't need to remember any commands.

---

## The manual way (if you ever want to do it yourself)

Run these from inside the project folder (`~/Documents/Velvosoft`):

### 1. Re-capture the live site into `snapshot/`

```bash
cd ~/Documents/Velvosoft
rm -rf snapshot && mkdir -p snapshot
wget --mirror --page-requisites --convert-links --adjust-extension \
  --no-host-directories --directory-prefix=snapshot \
  --span-hosts --domains=velvosoft.biz,fonts.googleapis.com,fonts.gstatic.com \
  --no-parent --level=2 \
  --reject-regex='(wp-json|xmlrpc|/feed|/comments)' \
  -e robots=off \
  --user-agent="Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36" \
  https://velvosoft.biz/

# remove duplicate HTML page variants (keeps assets intact)
find snapshot -type f -name "*.html" -name "*?*" -delete
```

### 2. Commit the changes

```bash
git add -A
git commit -m "Update snapshot after website changes"
```

### 3. Push to GitHub

```bash
git push
```

After the push, the updated site appears at:
**https://github.com/mdtouseef15/velvosoft-website**

---

## Key facts to remember

- The snapshot captures the **public-facing result** (HTML/CSS/images visitors see), not the WordPress backend/database.
- GitHub is the **permanent cloud copy** — this laptop is just a working copy. To set up on a new machine: `git clone https://github.com/mdtouseef15/velvosoft-website.git`
- To actually change what visitors see, edit in **WordPress/Elementor**, not in this folder. This folder is a backup/portfolio copy.
