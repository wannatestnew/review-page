---
title: How I Built This Digital Garden (Quartz 4)
date: 2026-02-28
tags:
  - technology
  - tutorials
  - quartz
---

# My Quartz 4 Setup Guide

This note documents the process of setting up this site using **Quartz 4**, **Obsidian**, and **GitHub Actions**.

## 🏗️ The Core Workflow
To publish a note, I follow a three-step system:
1. **The Editor:** I write Markdown in **Neovim** or **Obsidian**.
2. **The Generator:** **Quartz 4** turns those Markdown files into a website.
3. **The Host:** **GitHub Pages** serves the files to the world.



## 🚀 Key Commands
I use the following commands in my Arch Linux terminal to manage the site:

| Command | Purpose |
| :--- | :--- |
| `npx quartz sync` | **The "Publish" Button.** Pulls from GitHub, commits local changes, and pushes to the web. |
| `npx quartz build` | Builds the site locally to check for errors. |
| `npx quartz build --serve` | Starts a local preview at `http://localhost:8080`. |

## 🛠️ Critical Troubleshooting
If the site shows a **404 error**, I check these three things:

1. **The Deployment Workflow:** Ensure `.github/workflows/deploy.yml` exists and has the correct permissions (`pages: write`).
2. **GitHub Settings:** Go to `Settings > Pages` and ensure the **Source** is set to `GitHub Actions`.
3. **The Base URL:** In `quartz.config.ts`, the `baseUrl` must match my GitHub repository subfolder (e.g., `wannatestnew.github.io/review-page`).

---

## 📽️ Reference Materials
* **Tutorial:** [How to publish your notes for free with Quartz](https://www.youtube.com/watch?v=6s6DT1yN4dw) by Nicole van der Hoeven.
* **Documentation:** [Quartz Official Docs](https://quartz.jzhao.xyz/)

> "A digital garden is a collection of evolving notes, not a series of finished posts."
