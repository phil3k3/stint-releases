# Stint Privacy Policy

*Last updated: October 17, 2026*

Stint is a macOS menu bar app that tracks how you spend your working day.
This page explains, in plain language, what data it touches and where that
data goes. If anything here doesn't match what the app actually does, or you
have questions about specific behavior, contact us — see below.

## The short version

Everything Stint tracks — app usage, window titles, browser URLs, file
edits, AI agent sessions — is stored **only** on your own Mac. Stint has no
backend server, no account, no analytics SDK, and no crash reporter. The
only request Stint makes over the internet on its own is the update check
described below.

## What's stored locally, and never leaves your Mac

- The active application, window title, and duration, captured whenever you
  switch focus.
- The URL of the active tab, for supported browsers (Safari, Chrome,
  Firefox, Brave, Edge), without its query string or `#fragment`, which is
  where reset links, login codes and search terms usually are.
- The file path of the active window's document, when the app reports one,
  and a list of your project folders (found in the folders you've chosen and
  in the activity above), so time can be grouped by project.
- File paths and timestamps (never file contents) for files changed inside
  folders you've chosen in Setup or on the Permissions page.
- The name and working directory of development processes (for example
  `node`, `python`, `make` or `aider`) running inside the folders you've
  chosen, sampled once a minute.
- Claude Code session metadata (session ID, tool name, working directory,
  timestamps) — only if you've opted in by installing the Claude Code hooks
  from the Setup or Integrations page.

This data lives in `~/Library/Application Support/Stint/` and is readable
only by your own macOS user account. You can inspect, export, or delete it
at any time — the database is a plain SQLite file. "Delete All Data…" in the
menu bar menu deletes every recorded activity; deleting that folder (or
uninstalling the app and removing it) removes everything, settings included.
"Pause Tracking" in the same menu stops all recording until you resume.

## What Stint never records

These rules are applied before anything is saved, and again to data that's
already recorded (at every launch and whenever you change your exclusions):

- Password managers and credential stores (for example 1Password,
  Bitwarden, Keychain Access, Passwords, KeePassXC, LastPass, Dashlane),
  including their browser extensions and web vaults: nothing about them is
  recorded.
- Private and incognito browser windows in Chrome, Brave, Edge and Firefox:
  nothing is recorded. Safari doesn't let other apps tell its private
  windows apart, so for Safari, add sites you don't want recorded to your
  exclusions.
- Windows whose title, address or file path mentions passwords,
  verification or recovery codes, API keys or tokens, or contains something
  that looks like a secret (such as `password=…` or a key like `sk-…`): only
  the app name and the time are kept.
- Apps and websites you add on the Permissions page under Privacy.

Deleted data is overwritten in the database file rather than left behind.

Stint also keeps a small log of app events (launches, permission and hook
status, errors) in `~/Library/Logs/Stint/`. It contains no recorded
activity.

Stint's dashboard is served by the app itself on your Mac's loopback
interface (`127.0.0.1`). It isn't reachable from other computers, and every
request needs a random per-install key.

Because this data can incidentally include personal information that
belongs to *other* people — for example, a meeting title with attendee
names, or an email subject line — you're the one in control of it: it's on
your disk, it's never uploaded by Stint, and Stint's developer never sees it.

## What is sent off your Mac

**Checking for updates.** At launch and then once a day, Stint fetches a small public JSON file
from GitHub (`raw.githubusercontent.com`) to see if a newer version exists.
The request carries no personal data — only a generic `Stint/<version>`
user agent. GitHub, like any web host, sees your IP address; see
[GitHub's privacy statement](https://docs.github.com/site-policy/privacy-policies/github-general-privacy-statement).

**AI assistants you connect yourself.** If you connect an AI assistant (for
example Claude Desktop) to Stint's MCP server, that assistant can read your
tracking data on request — for instance to write a timesheet — and will
send what it reads to its provider as part of your conversation. This only
happens after you set it up, and only when you ask the assistant for it.
The provider's own privacy policy applies to that data.

**Feedback and problem reports, only when you choose.** "Send Feedback…"
and "Report a Problem…" in the menu open a prefilled issue on Stint's public
GitHub repository in your browser. Nothing is sent until you submit it there
yourself, and you can edit it first. A problem report contains diagnostics
only: Stint and macOS versions, permission and hook status, database size,
and recent lines of the app log, with your home folder shown as `~`. It
contains no recorded activity. **GitHub issues are public**, so remove
anything you don't want published; GitHub's privacy statement applies.

**Licensing.** Stint is free during the public beta and has no license or
payment flow. If paid plans are introduced, this policy will be updated
before any license data is collected.

## What Stint never does

No analytics, no telemetry, no automatic crash reporting, no third-party tracking
scripts, no cloud sync, no advertising SDKs.

## Your data, your control

Because tracking data is local-only, you already have full access, export,
and deletion rights over it — no request to us is needed. If you have
questions, reach out to us at the address below.

## Retention

Local tracking data is kept until you delete it yourself, since Stint has no
way to know when you consider a project finished.

## Children

Stint is a professional time-tracking tool and isn't directed at children.

## Changes to this policy

If this policy changes, the updated version will be published at this same
location with a new "last updated" date.

## Contact

Stint is developed by Fincloud Software GmbH. Questions about this policy
or your data: office@fincloud.software

---

*This is a plain-language description of a single-developer app's actual
data flows, not a substitute for legal advice. If you have specific
compliance requirements (e.g. as an EU business), please have this
reviewed by counsel before relying on it.*
