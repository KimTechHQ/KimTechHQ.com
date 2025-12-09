# OWNING YOUR PRESENCE ONLINE
## Version Control, Domains, and Deployment for Technicians

### Why Your Domain Matters
GitHub, and by extension Git, is not just for software developers. It is a standard tool for anyone who manages
versions, configurations, scripts, or documentation in general. Tech professionals often juggle network and
software configurations, automation scripts, and troubleshooting notes. GitHub helps you track changes,
maintain backups, store ideas, and collaborate efficiently with teams.
At the same time, your personal domain lets you take ownership of your online presence. It ensures people
can find the correct information about you and not someone else with a similar name. Whether you use it for a site, a portfolio, documentation, or even just a professional email, a domain becomes a stable place you
control.
Together, version control and a personal domain form the foundation of your digital identity as a technician:
how you manage your work, how you present yourself, and how you deploy the things you build.
This guide covers both pieces in detail, starting with Git and GitHub, and moving into domains, DNS
configuration, and deployment.

### ‘Git-ting’ to Know Git
GitHub, and by extension Git, is not just for software developers. It is a standard tool for anyone who manages
versions, configurations, scripts, or documentation in general. Tech professionals often juggle network and
software configurations, automation scripts, and troubleshooting notes. GitHub helps you track changes,
maintain backups, store ideas, and collaborate efficiently with teams.

### Why Technicians Should Use GitHub

Git provides change tracking, accountability, and rollback capabilities.
• Change tracking lets you see who modified a configuration file, when, and why.
• Accountability ensures that every change is tied to a technician’s commit message.
• Rollback means that if a configuration breaks a device or system, you can instantly revert to a previous
working version.
Instead of guessing what changed, you can review a complete history of edits, which is perfect for maintaining
consistency across multiple sites or devices.

### A Brief History of Git and GitHub
The following section was adapted from The Git Origin Story published by Linux
Journal. [1]

Before Git existed, Linus Torvalds and the Linux kernel community managed source code manually.
Contributors would send patches to mailing lists, and Linus would apply them directly to his local copy of the
kernel. There was no structured revision history… only large diffs between one release and the next. Although
open-source version control systems like CVS existed, Linus disliked them for being slow, centralized, and
prone to errors when handling simultaneous edits.
In 2002, Linus adopted BitKeeper, a commercial distributed revision control system developed by Larry
McVoy’s company, BitMover. BitKeeper introduced a revolutionary concept for its time: distributed
development, where every developer could have a complete copy of the project and merge changes
independently. This made collaboration on large projects like the Linux kernel far more efficient. However,
BitKeeper was closed source, and its licensing restrictions created friction within the open-source
community. Developers were uneasy that the world’s most important open-source project depended on
proprietary software.
The tension came to a head in 2005, when BitMover revoked free licenses after an attempt by Andrew Tridgell
(creator of Samba and rsync) to reverse engineer BitKeeper’s communication protocol. Overnight, the Linux
kernel lost its primary development tool. Rather than return to older systems like CVS or Subversion, Linus
decided to create a new system from scratch-one that combined BitKeeper’s distributed power with open-
source freedom.
In just a few weeks, Linus designed and built Git, focusing on three main principles:
• Speed: capable of handling massive projects and thousands of commits quickly
• Integrity: every file and commit identified by a secure hash (SHA-1)
• Distributed architecture: every developer has a full local repository
By July 2005, Git was already self-hosting and used for kernel development. Linus soon handed maintenance
over to Junio C. Hamano, who organized Git’s complex low-level commands into the user-friendly tools we
use today. The original core commands (called “plumbing”) were wrapped with higher-level “porcelain”
commands, making Git accessible beyond experts.
A few years later, in 2008, GitHub was launched by Tom Preston-Werner, Chris Wanstrath, and PJ Hyett.
GitHub provided a simple web interface for Git, allowing users to host repositories online, track issues, and
collaborate through pull requests. This made Git’s powerful distributed model easy for individuals and teams
to adopt.
Today, Git remains the foundation of modern software and system configuration management, while GitHub
serves as the world’s most popular platform for sharing, reviewing, and maintaining projects of every kind,
from codebases to documentation.

### Installing Git
##### Standard Windows Installation
1. Go to the official site: https://git-scm.com/download/win
2. Download the 64-bit Git for Windows installer.
3. Run the installer:
• Keep defaults unless you know you need custom behavior.
• Recommended choices:
• Use Git from Git Bash and command prompt
• Use bundled OpenSSH
• Checkout Windows-style / commit Unix-style line endings
4. Finish installation; Git Bash will be available from Start Menu.
5. Verify installation
Open PowerShell or Git Bash:
git --version

#### Linux Installations
Debian/Ubuntu
sudo apt update sudo
apt install git git
--version
Fedora
sudo dnf install git
git --version
Arch Linux
sudo pacman -S git
git --version

#### Installation on macOS
Option A: Using Xcode Command Line Tools (recommended)
This is the simplest and gives you the Apple-maintained Git build.
1. Open Terminal Run:
xcode-select --install
A popup appears → click Install.
2. After installation, verify:
git --version
Option B: Homebrew (for latest releases)
1. Install Homebrew (if not installed):
/bin/bash -c "$(curl -fsSL
https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
(one line)
2. Install Git:
brew install git
Verify:
git –version

#### Post-install Setup
Before you start using Git, it’s important to tell Git who you are so your work can be properly identified. The
following commands set your global name, email, and preferred editor. These details are stored once on your
system and used automatically for all future commits, ensuring that every contribution is correctly attributed
and easy to manage.

### Set username and email:
git config --global user.name "Your Name" git
config --global user.email "you@example.com"
### Quality of Life
Git is the version control engine that handles cloning, committing, branching, and tracking changes. To use
Git, you need a shell (a terminal environment) to run commands in. On Windows, technicians typically choose
between two environments:
Git Bash gives you a Linux-style terminal and works with Git immediately after installation.
PowerShell is the Windows-native terminal and also runs Git without extra setup.
For PowerShell users, there is an optional enhancement called posh-git. This is not a replacement for Git. It
simply improves your PowerShell experience by showing the current branch, displaying file status, and
providing autocomplete for Git commands. You still run the exact same Git commands; the prompt just
becomes more informative.
In short: Git is the tool you use The shell is where you run it posh-git is an optional upgrade for PowerShell
users
#### Enabling posh-git in PowerShell (optional)
If you prefer working in PowerShell, you can enable posh-git for clearer prompts and better usability.
! Remember PowerShell is Case Sensitive.
Install posh-git:
Install-Module posh-git -Scope CurrentUser
#### Enable it:
Add-PoshGitToProfile -AllHosts
Once enabled, your PowerShell prompt will automatically display branch names and Git status whenever you
are inside a repository.

## Generate an SSH key - Link Git to your GitHub Account
Before you can securely connect your computer to GitHub or any remote Git server, you need a way for the
server to recognize who you are without constantly asking for a password. That’s where SSH keys come in.
They provide a simple, secure form of authentication that lets Git verify your identity automatically whenever
you push, pull, or clone a repository.
1. Run:
ssh-keygen -t ed25519 -C "you@example.com"
The “you@example.com” part is just a label added to the SSH key so you can identify it later. It’s usually set
to your GitHub email for convenience, but it doesn’t affect security and is not required to match your account.
You can use any email, your GitHub no-reply address, or even a simple description like “my laptop key”.
2. Press Enter to accept the default file location and create the key pair.
3. Start ssh-agent:
eval "$(ssh-agent -s)" ssh-
add ~/.ssh/id_ed25519
This starts a small background program that safely stores your private key in memory. Adding your key to the
agent lets Git use it automatically when connecting to GitHub, without asking for a password each time.
4. Copy the public key:
cat ~/.ssh/id_ed25519.pub
This displays your public key — the part you share. You’ll paste this into GitHub or
GitLab. It’s safe to show to others, unlike your private key.
5. Add it to GitHub/GitLab → Settings → SSH keys.
Pasting your public key here tells GitHub or GitLab to trust your computer. Once added, the site can
authenticate you securely using the matching private key on your machine.

### Creating Your First Repository
A repository (often called a repo) is the place where Git stores your project’s files and tracks every change you
make. Once your project is inside a repository, Git can record versions, manage branches, and sync
everything with GitHub. Creating your first repository is the foundation of working with Git.
1. Create a new folder for your project (or use an existing one):
mkdir my-first-repo
cd my-first-repo
This gives Git a dedicated place to track your work. Any folder can become a Git
repository as long as you initialize it.
2. Initialize the repository:
git init
This creates a hidden .git directory that stores all version history and configuration for
your project. Your folder is now officially a Git repository.
3. Add a file to the project, for example a README:
echo "# My First Repository" > README.md
You need at least one file for your first commit. A README is a common choice because
it describes the project.
4. Stage your new file:
git add README.md
Staging tells Git which changes you want to include in the next commit. You can stage
one file, many files, or all changes at once.
5. Commit your work:
git commit -m "Initial commit"
A commit is a snapshot of your project at a point in time. This first commit marks the
starting point of your project’s history.
6. Connect your repo to GitHub:
git remote add origin git@github.com:your-username/your-repo.git
git push -u origin main
If your GitHub repository uses the main branch, use main. If it uses master, replace main with master.
This links your local repository to a remote one on GitHub. Pushing uploads your commits so they are backed
up and accessible online.

### Cloning and Syncing Changes
Cloning is how you download a copy of an existing GitHub repository to your computer so you can work on it
locally. Once a project is cloned, you’ll regularly sync changes by pulling updates from GitHub and pushing
your own work back up. These commands form the core workflow of using Git every day.
1. Clone a repository from GitHub:
git clone git@github.com:your-username/your-repo.git
This creates a complete local copy of the project, including all files, branches, and
history. You only need to clone a repository once.
2. Move into the project folder:
cd your-repo
Git commands only apply inside a repository, so you must be in the correct directory to
work with it.
3. Pull the latest changes:
git pull
This updates your local copy with any changes that were made on GitHub since you last
worked on the project. Pulling regularly keeps your work in sync with others.
4. Make your changes locally Edit files, add new ones, or remove old ones.
Git will track all modifications inside the repository folder.
5. Stage your changes:
git add .
Using a dot stages every changed file at once. You can also stage individual files if you
prefer more control.
6. Commit your work:
git commit -m "Describe what you changed"
Each commit captures a snapshot of your progress and makes it easy to review or undo
changes later.
7. Push your changes to GitHub:
git push
This uploads your new commits to the remote repository so your changes are saved, backed up, and visible to
collaborators.
Every time you commit and push to GitHub, your work is versioned and safely stored in the cloud. This means
you automatically get a backup and a complete history of your project without setting up anything extra.

### Branching and Collaboration Basics
Branches let you work on new features or fixes without affecting the main version of your project. This makes it
safe to experiment, collaborate with others, and keep your work organized. When your changes are ready, you
merge your branch back into the main branch so the whole team can use them.
1. Create a new branch:
git branch feature-idea
A branch is a separate line of development. Creating one lets you work independently
from the main branch.
2. Switch to your branch:
git checkout feature-idea
This moves you into the new branch so any changes you make will belong to it.
3. Create or edit files, then commit your changes:
git add . git commit -m "Add
new feature"
Your work is safely stored in your branch, keeping the main branch clean and stable.
4. Push your branch to GitHub:
git push -u origin feature-idea
This uploads your branch to GitHub so others can review or collaborate on it.
5. Open a pull request on GitHub A pull request (PR) is how you propose merging your
branch into the main branch. It lets teammates comment, review changes, and
ensure everything is ready before merging.
6. Merge the pull request Once approved, GitHub will merge your branch into the
main branch. This updates the project with your new feature or fix.
7. (Optional) Delete the branch:
git branch -d feature-idea
After merging, deleting old branches keeps your repository tidy.

### Branching and Collaboration Basics (Advanced)
Branches allow multiple developers to work on different features or fixes at the same time without interfering
with each other. By understanding how to manage branches, keep them up to date, and collaborate through
pull requests, you maintain a clean project history and reduce the risk of conflicts.
1. Create and switch to a new branch in one step:
git checkout -b feature-idea
This command both creates the branch and moves you onto it. Branch names are usually short and
descriptive, such as feature-login, bugfix-typo, or docsupdate.
2. Work on your changes and commit them:
git add . git commit -m "Implement
new feature"
Each commit represents a logical step in your work. Smaller, clear commits make it
easier for reviewers to follow your progress.
3. Keep your branch up to date with the main branch:
git checkout main
git pull
git checkout feature-idea
git merge main
Regularly merging the latest changes from main reduces merge conflicts later and ensures your feature works
with the most recent project updates.
Tip: You can also use git rebase main instead of merge for a cleaner, linear history, but rebase rewrites
commit history, so use it carefully when collaborating.
Important: Do not rebase branches that teammates are already using. Rebasing shared branches rewrites
history and can cause conflicts or confusion for anyone who has already pulled the original branch.
4. Push your branch to GitHub:
git push -u origin feature-idea
Other contributors can now see your work, comment on it, or help finish it. Setting the
upstream branch lets you use plain git push or git pull without extra parameters.
5. Open a pull request (PR) A PR is where collaboration happens. Teammates review
your changes, discuss improvements, and check for issues. Good PR descriptions
explain what you changed and why. This helps maintain quality and consistency
across the project.
6. Address feedback and update your branch After reviewing feedback, continue
committing changes:
git add . git commit -m "Apply review
feedback" git push
Your PR updates automatically as you push new commits.
7. Merge the pull request Once approved, merge your branch into main using
GitHub’s interface. This integrates your work and triggers any CI workflows, tests, or
deployments configured in the project.
8. Clean up the finished branch:
git branch -d feature-idea git push
origin --delete feature-idea
Removing merged branches locally and on GitHub keeps the project tidy and avoids
confusion.

### Using GitHub for Documentation
GitHub isn’t just for code. It’s also a powerful platform for writing, organizing, and publishing documentation.
Whether you’re explaining a project, writing tutorials, or maintaining technical notes, GitHub’s Markdown
support and version control make your documentation easy to update, track, and collaborate on.
1. Create or edit documentation files:
echo "## Project Overview" > README.md
Markdown (.md) files format cleanly on GitHub and are ideal for documentation. The
main README often acts as the front page of your project.
2. Organize your docs using folders:
mkdir docs
echo "## Installation Guide" > docs/installation.md
Grouping related documentation into a docs folder helps keep your repository structured
as it grows.
3. Commit changes to Git:
git add .
git commit -m "Add initial documentation"
Commits create a record of who changed what and when, making it easy to revert
mistakes or review documentation history.
4. Push documentation updates to GitHub:
git push
Your updated docs appear instantly on GitHub, making them accessible to collaborators or anyone viewing
your repo.
5. Use GitHub’s built-in Markdown renderer GitHub automatically formats
Markdown into clean, readable pages. Headings, lists, links, code blocks, and
images all display beautifully without any complex setup.
6. (Optional) Enable GitHub Pages for documentation websites If you want your
documentation to appear as a polished website, you can enable GitHub Pages
directly from your repository settings. It can use a docs/ folder or a dedicated
branch to publish a full website
7. Review and discuss documentation using pull requests Treat documentation
changes the same way you treat code changes. Creating pull requests lets your
team review updates, suggest improvements, and keep the docs accurate.

### Tips and Common Mistakes
Working with Git becomes much easier once you understand a few simple habits and pitfalls. These tips will
help you avoid frustration and keep your projects organized as you learn.
• Commit often with clear messages Frequent commits make it easier to track
your progress and roll back changes if something goes wrong. Good commit
messages explain why a change was made, not just what changed.
• Pull before you push
git pull
Running a pull before pushing helps prevent conflicts, especially when
collaborating with others. It keeps your local branch up to date with any changes
from GitHub.
• Don’t forget to stage your changes New users often edit files but forget to stage
them with:
git add .
If your commit seems empty, it’s usually because nothing was staged.
• Avoid committing large or secret files GitHub stores everything you commit,
even if you delete it later. Avoid committing things like credentials, API keys, or
large binary files. Use a .gitignore file to exclude them.
• Use branches instead of working directly on main Branches make it safer to experiment without
breaking your main project. They also make collaboration smoother.
• Read error messages carefully Git’s errors look intimidating, but they usually tell you exactly what’s
wrong. Most issues come down to missing a pull, forgetting to add files, or pushing to the wrong
branch.
• Don’t panic nothing is ever truly lost Git stores your history extremely well, and even if something goes
wrong, commits can often be recovered. As long as you regularly pull and push your work to GitHub,
your changes are safely backed up and easy to restore, which makes Git far less scary than it seems at
first.
• Keep your repository clean Delete old branches after they’re merged, and use organized folder
structures for documentation and assets. A tidy repo is easier for you — and collaborators — to
navigate.

### Choosing a Registrar
A registrar is the service that sells and manages your domain name. It handles your ownership records,
renewals, and DNS settings, acting as the official link between you and the global domain registry systems.
Buying a domain early is often the right move because it prevents someone else from taking the name you
want or spoofing your project later. Once a domain is registered, it’s gone unless the owner gives it up, and
popular or meaningful names disappear quickly. Securing your domain early protects your idea, your identity,
and your future brand before it grows into something others might try to imitate or claim for themselves.
Cloudflare offers transparent pricing, strong security defaults, and free WHOIS privacy, making it a solid all-
around choice for most users.
Porkbun provides low prices, free privacy, and a simple interface, appealing to anyone who wants an
affordable but reliable option.
Namecheap balances cost and usability, with straightforward management tools and free privacy on most
domains.
Njalla caters to users who prioritize anonymity; it acts as a privacy buffer by holding domain ownership on
your behalf, which can reduce personal exposure but may not fit every legal or organizational requirement.
GoDaddy remains one of the largest registrars, offering a broad ecosystem of services, though often at higher
prices and with more upsells.

### Choosing a TLD (Domain Ending)
Your TLD affects how trustworthy your domain looks and how easy it is for others to impersonate you. For
most people, .com is the safest choice. It’s the most recognized globally, the default people assume when
typing a domain, and the hardest for someone else to spoof. If your handle is available in .com, it’s usually
worth claiming for long-term stability.
.com
• Most recognized and trusted
• Often preferred for professional sites
• If you can get your name in .com, it’s never a bad choice.
.io
• Popular in tech - Good for portfolios or anything tech-related.
• Short, clean, modern
• Technically a country code, but widely accepted
.tech
• Clear meaning for technical work
• Usually easier to find available names
• Works well if your focus is technology or engineering.
.dev
• Secure by default (requires HTTPS)
• Recognized in developer communities
• More niche - Great for projects, documentation sites, or showcasing technical skills.
.me
• Personal and expressive
• Affordable
• Ideal for a personal site or resume-style domain.
.net, .org, others
• Solid alternatives if .com is taken
• Use these when you want something neutral or industry-appropriate.
If .com isn’t available or doesn’t fit your brand, modern TLDs like .io, .dev, or .tech are fine alternatives,
especially in technical fields. They’re more available and still widely accepted, but they do carry a slightly
higher impersonation risk simply because attackers often target unusual or trendy endings for look-alike
domains.
### Setting Up DNS Records
To make your domain actually do something, you set DNS records. These records tell the internet where to
send traffic for your website, email, or other services. Most domains only need a few basic types, and each
has a specific job.

#### A Record
Points your domain to an IPv4 address. If your server has an IP like
203.0.113.10, the A record tells browsers to load your site from that address.
#### AAAA Record
Same purpose as an A record but for IPv6 addresses. If your host supports IPv6, you can add both A and AAAA
records so users on any network reach your site.
#### CNAME Record
Points one hostname to another hostname instead of an IP. Useful when you want something like
www.yourdomain.com to point to your root domain, or when a service provider gives you a target like
username.github.io.
#### MX Record
Directs email for your domain to the correct mail server. If you use a custom email provider, they will give you
MX records that tell the world where to deliver mail for @yourdomain.com.
These four records cover almost everything a personal domain needs. Once they’re set up, your domain can
host a website, send and receive email, and cleanly redirect subdomains wherever you want.

### Securing with HTTPS and DNSSEC
Once your domain is connected to your site, the next step is securing it. Two key pieces of that are HTTPS and DNSSEC. Both protect your visitors and strengthen your online identity, and they’re easy to enable when using
modern providers like GitHub Pages and Cloudflare.
#### HTTPS (SSL Certificates)
HTTPS encrypts traffic between your visitors and your site so no one can intercept or alter what they see. Most
hosting platforms automatically issue free SSL certificates, so you don’t need to buy or manually install
anything.
If you’re using GitHub Pages + Cloudflare, the workflow looks like this:
1. GitHub Pages serves your site over HTTPS by default.
2. Cloudflare sits in front of your site and provides an additional HTTPS layer.
3. Cloudflare automatically issues and renews SSL certificates without your involvement.
Once Cloudflare is enabled, you don’t have to worry about renewals or outages. Certificates rotate in the
background and stay valid on their own.
You get:
• Encrypted traffic
• A more trustworthy site
• No manual renewal work
HTTPS is one of the simplest but most important upgrades for any personal site.
#### DNSSEC (Domain Name System Security Extensions)
DNSSEC protects your domain from tampering by verifying that DNS records come from the correct source.
Without DNSSEC, an attacker could attempt to redirect your domain to a fake site. With DNSSEC enabled,
resolvers can verify that records have not been altered.
Cloudflare supports DNSSEC for free, and enabling it is usually just one toggle in your DNS settings. Your
registrar may require adding a DS record, but once it’s configured, DNSSEC also maintains itself without
future input.
DNSSEC matters because it:
• Prevents DNS spoofing
• Protects your visitors from being redirected
• Adds another layer of trust to your personal domain
Between HTTPS and DNSSEC, your site gains security that matches modern best practices with almost no
maintenance required.
### Privacy and Branding Benefits
Setting up your domain isn't just a technical step — it also protects your personal information and strengthens
your identity online.
Protecting WHOIS Data
When you register a domain, your personal information (name, city, phone, email) would normally appear in
the public WHOIS database. Anyone could search your domain and see your details.
Most modern registrars offer free WHOIS privacy, which replaces your information with placeholder contact
details. This prevents:
• Spam
• Unwanted contact
• Data harvesting
• Exposure of personal details
Using registrars like Cloudflare or Porkbun keeps your identity private by default.
Reinforcing Your Personal Brand
Your domain becomes the “home base” for your digital presence. No matter what platforms change or
accounts you move between, your domain is the stable anchor you own.
A strong domain reinforces your brand by:
• Making your work easy to find
• Presenting a consistent identity
• Avoiding confusion with others who share your name
• Providing a professional location for your portfolio, articles, and documentation
• Working as a simple, permanent link you can use anywhere
As you grow, your domain grows with you. It becomes the place where people can reliably find accurate
information about who you are and what you do.
In short, securing your domain and protecting your privacy gives you both safety and professional presence,
and it ensures your online identity is under your control, not someone else’s service or algorithm.
## Conclusion
Git and GitHub give field technicians a reliable way to manage configurations, track changes, and document
their work with confidence. Whether you are maintaining network settings, updating scripts, organizing
troubleshooting notes, or collaborating across teams, version control adds structure and safety to your daily
workflow. By learning the basics of repositories, branching, syncing changes, and secure authentication, you
gain a toolkit that reduces errors, speeds up troubleshooting, and preserves a complete history of your work.
As you continue using Git, these skills will become second nature. Start small, commit often, and make
GitHub your central source of truth for documentation and configuration management. With these practices
in place, you will always know what changed, when it changed, and how to get back to a known working state.
In the field, that kind of clarity is invaluable.
Owning your version control workflow and your domain gives you long term stability, structure, and control
over your work. With Git handling your history and deployments, and your domain anchoring your online
identity, you can grow your skills, publish your projects, and maintain a clean technical record of everything
you build.
Kimberly Cano
### References
[1] Linux Journal. *The Git Origin Story. 2009.
https://www.linuxjournal.com/content/git-origin-story
Cloudflare. DNSSEC Documentation.
https://developers.cloudflare.com/dns/dnssec/
Cloudflare. How to Choose the Best Domain Registrar.
https://www.cloudflare.com/learning/dns/glossary/choose-the-best-domain-name-registrar/
Porkbun. How to Enable DNSSEC.
https://kb.porkbun.com/article/216-how-to-enable-porkbuns-cloudflare-dnssec
Porkbun. Domain Management and Privacy Features.
https://porkbun.com/products/domain_registration
Namecheap. Domain Privacy Protection Overview.
https://www.namecheap.com/security/whoisguard/
Njalla. About Njalla: Privacy-Focused Domain Registration.
https://njal.la/about/
GoDaddy. DNS Records Explained.
https://www.godaddy.com/help/dns-for-beginners-680
Domcomp. Beginner’s Guide to Choosing a Domain Registrar.
https://domcomp.com/blog/best-domain-registrar-guide
Pragmatic Engineer. Domain Registrars Developers Recommend.
https://blog.pragmaticengineer.com/domain-registrars-which-developers-recommend/
StackExchange. Criteria for Evaluating Domain Registrars.
https://webmasters.stackexchange.com/questions/35569/on-what-criteria-should-i-evaluate-domain-
registrars
#### Official Git Documentation
The primary source for Git behavior, commands, and concepts.
• Git book (Pro Git) - https://git-scm.com/book/en/v2
• Git basics tutorial and command reference - https://git-scm.com/docs
Disclaimer: AI tools were used in the development of this document to assist with drafting and
refinement. All content has been reviewed and approved for accuracy.