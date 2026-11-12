---
title: Documentation and support
---

# Repo Starter: documentation and support

Questions, bugs or ideas: email **[{{ site.support_email }}](mailto:{{ site.support_email }})**. We reply within 2 business days.

## Install

Open the **[installation link]({{ site.install_url }})** as a Bitbucket workspace admin, choose your workspace and approve the permissions. The workspace must belong to an Atlassian organization, which is how Bitbucket installs Forge apps.

## Quick start

1. **Mark a template.** In the repository you want to use as a template, open **Repository settings → Forge Apps → Repository template**. Give it a name and description, tick any extra branches to create (for example `develop`), choose whether to copy the repository details and Pipelines settings, and click **Mark as template**. You need to be an admin of that repository.
2. **Create a repository from it.** In the workspace sidebar, open **Apps → New repository from template**. Pick the template, a project and a name, and choose whether it's private. The page shows what will be copied before you click **Create repository**.
3. **Finish the listed steps.** The report links straight to the new repository's webhook and variable settings for anything Bitbucket doesn't let apps copy.

Already created the repository with Bitbucket's own **Create repository** button? Leave it empty, open its **Repository settings → Forge Apps → Repository template**, and use **Apply a template**.

Workspace admins can see every template under **Workspace settings → Forge Apps → Repository templates**.

## What gets copied

| From the template | In the new repository |
|---|---|
| Files on the main branch | All of them, as **one fresh commit** on a branch with the same name. Binary files, executable scripts (`+x`) and symlinks keep their contents and attributes. The template's history isn't copied. |
| Extra branches you ticked | Created from that same fresh commit |
| Description, language, fork policy | Copied (a public repository always allows forks, because Bitbucket requires it) |
| Pipelines | Enabled if the template has them enabled. Non-secured repository variables are copied with their values. |

## What you finish by hand

- **Webhooks.** Bitbucket doesn't let apps create webhooks, so the report lists each one with its URL and events. Webhook secrets can't be read back, so enter them again.
- **Secured Pipelines variables.** Bitbucket never reveals secured values; the report lists their names.

## What isn't copied

- **Branch restrictions and default reviewers.** Bitbucket applies your **project settings** to new repositories, so set them once on the project.
- **Permissions, Git history, Git LFS files and submodules.** The report lists any LFS files or submodules it skipped.

## Limits

- Templates of up to **500 files and 50 MB** can be copied. Bigger templates show a message instead of the **Create** button.
- **Apply a template** works only on empty repositories, so it can never overwrite existing work.

## Permissions

Repo Starter acts as **you** every time it talks to Bitbucket, so Bitbucket checks your own permissions:

- You only see templates you can read.
- You can only create repositories in projects where Bitbucket lets you create them.
- Only repository admins can mark, edit or stop using a template.

The app's code runs on Atlassian's infrastructure (Forge). It stores only each template's name, description and options, never your repository contents. See the [privacy policy](privacy).

## Troubleshooting

**A template is missing from the list.** You can't read its repository, or it was unmarked. Ask the repository's admins for read access.

**"Repository with this Slug and Owner already exists."** Pick another name; Bitbucket derives the URL from it.

**"This template can't be copied."** It's over the size limit. Move large assets out of the template, for example into Git LFS or a package registry.

**The repository was created, but copying files failed.** It's still empty: open its **Repository settings → Forge Apps → Repository template** and use **Apply a template**, or delete it.

**A setting shows "failed" in the report.** The files are in place; the message says why the setting wasn't applied. Set it by hand in the repository settings.

**"Only repository admins can change template settings."** Ask an admin of that repository to mark it.

## FAQ

**Does it keep a copy of my code?** No. File contents are read from the template while the new repository is being created and are never stored.

**Will repositories update when the template changes?** No. Each repository starts from the template as it is at that moment and is independent from then on.

**Can I use `{{ "{{" }}repo_name}}`-style placeholders?** Not yet. Tell us if you need them.

[Privacy policy](privacy) · [End user terms](terms)
