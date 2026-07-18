# GitDiscuss

A lightweight, self-hosted discussion board that turns GitHub Discussions into a Reddit-style community forum — no backend, no database, just a single static HTML page.

🔗 **Live demo:** https://gitdiscuss.github.io/GitDiscuss/

## Overview

GitDiscuss is a single-page site that wraps [giscus](https://github.com/giscus/giscus) — a comments widget powered by GitHub Discussions — in a custom dark-themed UI. Instead of a single comment thread, GitDiscuss adds a topic filter so visitors can switch between different discussion categories (much like subreddits or forum boards), and the page reloads the giscus widget scoped to the matching GitHub Discussions category.

Because everything runs client-side against the GitHub Discussions API via giscus, there is no server, database, or authentication system to maintain. Comments, replies, reactions, and upvotes are all stored as GitHub Discussions on the host repository.

## Features

- **Topic/category filter** — a dropdown lets users switch between General, Announcements, Q&A, Ideas, Polls, and Show and Tell, each mapped to its own GitHub Discussions category.
- - **Reddit-style layout** — a dark, card-based header with a community avatar, title, and subtitle above the comment feed.
  - - **Powered by giscus** — upvotes (reactions), threaded replies, and markdown support all come from GitHub Discussions under the hood.
    - - **Zero backend** — the entire app is one static `index.html` file, deployable anywhere that can serve static files (currently hosted via GitHub Pages).
      - - **Sign-in via GitHub** — since comments are backed by GitHub Discussions, visitors authenticate with their GitHub account to post.
       
        - ## How it works
       
        - 1. The page defines a map of topic keys (`general`, `announcements`, `qa`, `ideas`, `polls`, `showAndTell`) to their corresponding GitHub Discussions category IDs.
          2. 2. A `loadGiscus(categoryKey)` function injects (or re-injects) the giscus embed script into the page, pointed at the selected category.
             3. 3. Changing the dropdown re-runs this function so the comment feed reloads scoped to the newly selected topic.
                4. 4. On first load, the "General" category is loaded by default.
                  
                   5. ## Tech stack
                  
                   6. - **HTML/CSS/JavaScript** — 100% vanilla, no frameworks or build step.
                      - - **[giscus](https://github.com/giscus/giscus)** — comments engine backed by GitHub Discussions.
                        - - **GitHub Pages** — static hosting/deployment.
                         
                          - ## Repository structure
                         
                          - ```
                            GitDiscuss/
                            ├── index.html      # The entire app: markup, styling, and giscus loader script
                            ├── GitDiscuss.png  # Site logo / favicon
                            └── giscus.png      # Icon used for the "Giscus" credit link
                            ```

                            ## Using / forking this project

                            To reuse GitDiscuss for your own repository's discussions:

                            1. Fork or clone this repository.
                            2. 2. Enable **Discussions** on your own repository and create categories matching the topics you want (or edit the topic list to match your own categories).
                               3. 3. Install the [giscus GitHub App](https://github.com/apps/giscus) on your repository.
                                  4. 4. Update the `categories` object in `index.html` with your repository's actual Discussions category IDs (available from the giscus configuration tool at giscus.app).
                                     5. 5. Replace `GitDiscuss.png` with your own logo/branding if desired.
                                        6. 6. Enable GitHub Pages for the repository (or host `index.html` anywhere) to publish your board.
                                          
                                           7. ## Credits
                                          
                                           8. - [giscus](https://github.com/giscus/giscus) — the comments engine this project is built on top of.
                                              - - Built and maintained by [treatwashere](https://github.com/treatwashere).
                                                - 
