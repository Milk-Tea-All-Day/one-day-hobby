---
title: Basic Automation
date: 2025-01-05 08:11:14
tags: [automation, github actions, ssg, self-hosted runners, personal projects]
categories:
- [web-dev]
---

Now that I have my new server and site up and running, it's time to tackle some of the small annoyances and automate them away. Today’s goal (ODH): set up basic automation to streamline my blogging process. Ideally, I want to write a post, push it to GitHub, and have the site automatically build and deploy itself. These are the kind of conveniences I’ve come to take for granted at work.c

# Setting Up a GitHub Organization

I started by appreciating how much easier life is with my work setup. Our team’s non-profit status gives us extra capabilities on GitHub, including access to shared runners and other organization-level features. Unfortunately, these aren't available for personal accounts—GitHub doesn’t allow sharing self-hosted runners across repositories in personal accounts. Since they charge for minutes used, it makes sense this is reserved for organizations, which are more likely to pay.

After ruminating for a bit on what I wanted to do, I decided to setup a new Github Organization. I already had an old organization for [Heavy Robot](heavyrobot.com), but I wanted a fresh start. Enter [Milk-Tea-All-Day](https://github.com/milk-tea-all-day)—a blank slate ready for new projects.

While brainstorming this setup, I also considered another approach: spinning up a local GitLab instance. The idea was to use a self-hosted GitLab instance for my primary repository and workflows, then mirror said repos to GitHub for visibility. This would let me keep GitHub’s public-facing benefits but ignore the scale and features I don’t currently need while using a self-hosted solution. It’s an idea I may revisit in the future, especially if I run into limitations with GitHub. For now, though, laziness won—there are other things I want to focus on, and I didn’t want to get bogged down in scope creep.

With my organization in place, I could finally configure a shared self-hosted runner. This setup allows me to centralize automation across all my repositories within this new organization. First on the list? Automating this blog, of course! I’ve even made the repository public in case anyone is curious to see what’s under the hood. You can check it out [here](https://github.com/Milk-Tea-All-Day/one-day-hobby). Have fun digging into the "boring" details! 😂

# Configuring the Automation Workflow

Setting up the workflow was fairly straightforward. Here's what I did:

1. **Checkout the repository:** This step pulls the latest changes to the runner.
2. **Install dependencies:** Using npm install to fetch all required packages.
3. **Build the static files:** Running the site generator to produce the deployable files.
4. **Deploy to the server:** Using rsync to copy the static files to my web server.

This process ensures that every time I push a new post to GitHub, the site automatically updates itself. You can view the full workflow configuration in the repository’s [deploy.yml](https://github.com/Milk-Tea-All-Day/one-day-hobby/blob/main/.github/workflows/deploy.yml) file.

# Lessons Learned
I picked up a few little tidbits today:

* **The Value of Work Tools:** The conveniences I have at work—like shared runners and organization-level automation—are features I often forget about, this was a nice reminder of some of those niceities.
* **Automation Is Awesome:** Spending some extra time upfront to automate things can save a ton of time and hassle in the long run. And they're perfect challenges for one day hobbies!
* **Scope Creep is Real:** Sometimes, going with the answer that's right in front of you is the best choice. You can always come back to alternate ideas, like a GitLab setup, when the timing feels right.

# The Result
If everything works as expected, this post will be live on the site about a minute or so after I push it. It's a small but satisfying milestone: my blog now deploys itself, and is all static files! This automation makes the process smoother and allows me to focus on writing rather than worrying about little technical hurdles every time I want to update the site. Not to mention, I don't have to do  it from my main workstation solely any longer 🥳