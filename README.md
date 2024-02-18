# Project Ideas

The ideas I have for my side/joy/passion projects.
The info here will be a summary for the actual note I took. True notes is kept in a private repo :)

Check my progress in the [Side Project Backlog project board](https://github.com/users/Abrifq/projects/3).

**ASSUME PROJECTS ARE OPEN-SOURCED UNLESS SAID OTHERWISE**

I will hold the summaries here but if I feel like I want to add more detail, I'll make a separate file for it:

## Projects

In no order, here is all of them:

- [Database Maiden](#database-maiden)
- [Discord Profile Manager](#discord-profile-manager)
- [dump.idea](#dumpidea)
- [FeatureHunt](#featurehunt)
- [Github Projects Project Maintainer Bot](#github-projects---project-maintainer-bot)
- [NoTrack Login](#notrack-login)
- [Outage Notifier](#outage-notifier)
- [P!MOLA project](#parallelized-media-organizer-library-manager-and-archiver)
- [Repository Manager](#repository-manager)
- [Urban Upload](#urban-upload)
- [USB-PD to Proprietary Plug](#usb-power-delivery-to-proprietary-power-plug-project)
- [VSCode Profile/Workspace Manager](#visual-studio-code-profileworkspace-setting-manager)

### Database Maiden

A database helper for juniors/newcomers to help them build complex relations withing their queries.

Mostly intended for demos and SQL report queries (select this.column where bla bla)

[Go back to the project list][back-to-list]

### NoTrack login

Seriously, why does using a 3rd party provider **always** means they are entitled to your data?

This is just a library/platform for a login platform, doesn't track you, just lets you login and handout user token.
Simple\* as that. I'll do my best to follow best practices. You are free to [bike-shed][bikeshed] anytime.

\*: Simple as a concept, things might not be inherently simple.

[Go back to the project list][back-to-list]

### FeatureHunt

Basically _just another commission platform_ but for open source developers. Lets them also build a background, which is great for CVs... _I guess_
I also want people to be paid for their work, which also encourages people to contribute. Not just "do a pr and get 1 cent" or something like that, the money on the line is determined by the requester of the work. Essentially commissioning.

I also would like to tie this for my [supporting system][support-me] for the "founding" phase of this platform, giving money to me will help me help you.

[Go back to the project list][back-to-list]

### Discord Profile Manager

One of the "I do it because I can" projects.

Allows you to record your profile info (like name, bio, avatar, decorations) and share it with a link and apply it.

I guess it's useful for pranks where everyone is Jeff.

[Go back to the project list][back-to-list]

### dump.idea

A platform to share coding ideas privately (accessible with link) or publicly (accessible from homepage & search), [bikeshed][bikeshed] together and perhaps reach a conclusion.

[Go back to the project list][back-to-list]

### Repository Manager

The repository I mean here is git repos, specifically, but the git-ness doesn't matter that much. It should be just a parameter and repository initiation string at the end of the day.
Notable features:

<!-- TODO: move these details to a separate page-->

- `repoman init`: Take a few arguments and start with a template.
  - Has default options filled in from the config, for example license.
  - Has interactive options like:
    - _tags_, to search/categorize in folders in a better way
      Tag selector is also keeping a track of used tags to recommend while typing it out, making sure they are getting re-used for a better organizing.
      If you type a unknown tag and press enter, that will create a new tag.
    - associated _vscode profile_ -- hey, if it's a thing with neovim people, I will implement for it too.
      Basically running `vscode '%s' --profile '%s'` (or workspaces, depending on your config :slightly_smiling_face: )
  - Can also use urls to clone into the repoman folders.

- `repoman clean` or `cleanse`: Clean a repo's build artifacts and other junk that won't be needed when moving it to another computer
  Can also be triggered with `--all` to cleanse all repos, in parallel
  - If a `Makefile` with clean target is found, that is used. otherwise:
  - `js`: clean node_modules folder by default. I plan to add a script that checks for installed packages for other ways of cleaning.
    This might be getting rid of build artifacts, test/coverage reports, etc.
  - `c/c++`: clean root project folder and `bin/` for any linked elf files
  - Other languages can be added as well but need to work on it... or, you know, i could document it well and accept PRs :slightly_smiling_face:

- Stow like `repoman adopt`: Move the project folder to a known place for easier backups and management.
  Also accepts `--tag` to add tags to adopted folder.

- `repoman backup`, making backup files an ease.
  - Removes junk with `repoman cleanse`
  - Creates a tar file with the repo, pipes it into `xz`
  - If `--all` is used, it archives the library folder holding the repos, instead of archiving each repo, this should result in a better compression.
  - If `repoman restore` is used, repoman should read the .repoman-info.yaml file to read the tags and adopt the repo accordingly
    Otherwise, it's a tar file for god's sake, just decompress and untar with `tar -xvaf repo.tar.xz` and get your files back!

Might be a bash script, might change it to make a C program but i think i will keep it depending on [a variant of dialog](https://manpages.debian.org/testing/dialog/dialog.1.en.html) to make it easier to build a UI for it.

More details TBD.

[Go back to the project list][back-to-list]

### Parallelized Media Organizer, Library manager, and Archiver

P!MOLA in short.

<!-- Summarize this and then move the details to another page, possibly reference to github.com/p-mola for proper project timeline-->

- Utilizes `youtube-dl` or a youtube-dl compatible variant like `yt-dlp` to obtain media. Downloads it by itself to optimize downloading times
- Uses `atomicparsley` and `ffmpeg` to do Media Organizing, like ID3 (music tags), subtitles or chapter timestamp data
- Uses/will use a self made project called media-player **standards**, so you can just dial in your favorite media player**S** and when downloading the media, either optimize it for the best common denominator or create separate libraries!
- Archiving the last used mediums in temp/cache folders like `%TEMP%` or `~/.cache/` - possibly compressed even though I'm not sure if it will compress anything meaningful - so you don't have to re-download the same media when you just added a new media player or decided you want to recode it to 1080p instead of just 720p.
  I plan to make it keep track of the:

  1. How big is the cache folder, and how big it can get?
  2. How full should the disk containing p!mola files before it should clean it's cache, even though the cache limit is not hit.
  3. What files were last used?

  Which in turn should make it easy to clean the cache automatically without user's notice.
  I also look forward to allow the cache or the cache-cleaner to be disabled altogether.

The above points are what I call my MVP ideas.
Here are more details:

- Creating a not-so-bad UI for managing the P!MOLA system
- Creating mobile apps (probably only sync'ing with your PC/server to stay in the guidelines)
- Also a web interface to remotely manage your library.
- Also support for importing and exporting the library metadata (not including the files but the recipe how you made and organized the media)
- Keeping in touch with developers to make the **standards** project self-sustain it's updating process.
- Create scenarios, verification methods, and test files to verify a media player feature is working or not. This one is **utopic** in the kindest way. I don't expect this to be done before 2030.
- Also periodically publish test data so if someone is trying to implement a thing into their encoder/player, they can see if it is worth it or not. I dunno. I'm not a manager or a data analyst, I'd rather provide the data to them and let them decide for themselves. I guess other player developers can see if their features are considered broken, and reply to the reports or fix their bugs or implement common features they didn't think about. The only limit is out imagination:tm:.

[Go back to the project list][back-to-list]

### USB Power Delivery to Proprietary power plug project

Does what it says on the title:tm:.

What I aim to conquer is small electronic devices, like household combo routers that have annoying "different" plugs, old game consoles accepting DC power, rechargeable battery chargers, etc.

Features:

- Smol, Just the USB-C female side and male proprietary power plug side and enough room for the components necessary to take and transform the power.
- Most of them might need a certified 5 Ampere cable.
  If you ask me, it's better to buy strong 5A USB-C PD cables and re-use them for your laptop, iPad or whatever
  rather than just spending the same-ish money on your proprietary:tm: power cable and then have it broken in a few months again.
- My first commercial-open project, I do expect things to be amateur and learn on the way. Hopefully we can do a great job.

Glory to Right to Repair, Open Source Hardware and coffee!

[Go back to the project list][back-to-list]

### Github Projects - Project Maintainer bot

Because let's admit it, Github is not doing a perfect job and it's not in their interest. After all, I'm just a freeloader to them by being a Student/Free tier customer.

- English like describing of `event`s, `step`s and other things.
- Make it an action, if possible.

[Go back to the project list][back-to-list]

### Urban Upload

Perhaps it does sound close to Theo's UploadThing, but what I try to change is not the uploading process in DX but the uploading process in the opaque layer. The one we don't see.

Especially in Turkey, while the infrastructure is getting better, sometimes people are not getting good upload speeds, whether it's due to the greediness of their ISP or really on the copper level, packet losses do occur, and most of the time it will corrupt things.

I want to introduce the protocol in web form first, then maybe a standard for binary.
(Yes technically all transport streams are binary-- that's not something i wanna worry about now! I just wanna make new alpha versions to iterate until i'm satisfied with it, then produce a standard version.)

[Go back to the project list][back-to-list]

### Outage Notifier

Once again, an open collaborate for people.

A central service will check up with services, fetch their current outages, and notify people.

How to check the services? By crawling the web of course!
Where does the people come in? When we need to add more services or fix parsing or fix the fetching url... you name it.

[Go back to the project list][back-to-list]

### Visual Studio Code Profile/Workspace Setting Manager

Kind of like [repoman](#repository-manager), but for managing vscode profiles and workspace files. -- I need to investigate a bit to see and learn the differences between these two.

- CLI and Extension: Create new profile and assign in vscode
- Extension: Bring this option to base setting (user, base profile / workspace file)
- Stow like adopt and update strategy. Windows users are human too, guys.
  - If on Windows probably just diff, compare & update via CLI/extension.
  - If on linux, manage it via GNU Stow or manually (see windows)

[Go back to the project list][back-to-list]

### Terraria Resource Pack Sorter

Terraria has Resource Packs that has music or texture or text changes since 1.4.
However, after each update the previous version's order of the resource packs are lost.
This client will be:

- Help categorizing and sorting your resource packs
- Have a different format/file for this sorting, so you can just re-apply it after a new update (though, i think the file format does not change, it may be easier to add metadata + order into the same file)
- If you are ordering an older list and changed your resource pack subscriptions (will require steam id or steam login), it will show the not added ones so you can easily add them to the end of their respective categories with ease.
- Also since this is a web based editor, you can easily share your config with your friends without installing anything shady!

### Mubert Play Clients

[Mubert](https://mubert.com) is an "AI" that produces music. There are many resources covering how it works if you are interested in it.

I want it to work like the Mubert Play app in the app stores. -- Well, if they don't do it first, haha, why not?

I want to make small clients that connect to Mubert, let you choose your genre like in the app, and play, even when you close to tray.
If you want to interact with the stream (liking, resetting, etc.) you can use the tray icon's context menu or the app's interface.

After the MVP, i want it to have media player standards like [MPRIS](https://wiki.archlinux.org/title/MPRIS) built in.

### Simple Turn-based Game Framework

For board games, like uno or pishti. I may build on it to make more things.

TODO: Will fill this in later on, need to find more notes.

---

May have text based templates and builder clients.
May introduce a platform for creating and sharing the games you made.
Absolutely free as in free beer, so if you want to monetize it, you can do that.

### Offline YOK Atlas

For Turkish students. I'm sorry, rest of the world.

Basically, will intrepret a list of rows from an excel file, the user will give hints for the file (the file is human readable, so we need human help to build filters and convert to machine readable stuff.)

After that, build machine readable stuff (maybe sqlite) to publish/serve.

It can help the simple questions of "What branches I can reasonably apply in X city" of many Turkish students & consulting teachers.
Of course, the paid alternatives, like [ÇİTA](https://tercihalani.com/), might be better, but hey this is what you get for absolutely free.

[Go back to the project list][back-to-list]

[back-to-list]: #projects
[bikeshed]: https://www.bikeshed.com/ "More info on bike-shedding"
[support-me]: https://github.com/sponsors/Abrifq "My Github Sponsors page"
