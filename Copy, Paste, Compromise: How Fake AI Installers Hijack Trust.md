# The Installer Is the Phish: How Fake ChatGPT and Claude Downloads Became a Malware Delivery System


There is something uniquely effective about a fake installer. It does not need to fight for persistence in the victim’s mind, because the victim often grants it legitimacy before the first file is even downloaded. In the latest wave of AI-themed malware campaigns, that psychological shortcut has become the delivery mechanism: threat actors are impersonating ChatGPT and Claude installers, cloning branding, abusing search traffic and ads, and persuading users to run what looks like the beginning of productivity but is actually the start of compromise. [helpnetsecurity](https://www.helpnetsecurity.com/2026/05/27/deno-rat-malware-fake-chatgpt-claude-installers/)

This is not just a phishing story with better graphics. It is a story about how attacker tradecraft evolves when a brand becomes part of everyday technical workflow. Graphika reported that scammers used Google ads and convincing fake landing pages that imitated ChatGPT and Claude branding, sometimes instructing users to execute terminal commands such as PowerShell or curl-based install flows that actually installed malware instead of software. Malwarebytes separately reported that counterfeit installers hosted on GitHub and SourceForge delivered a backdoor called DinDoor, which then loaded a Deno-based remote access trojan capable of crypto-wallet theft and stealthy abuse of Microsoft Edge for screen streaming and persistence-related activity. [graphika](https://graphika.com/posts/malicious-commands-fake-claude-code-chatgpt-installers)

That combination is what makes this campaign so interesting. The deception is not limited to a malicious file download. It extends into developer culture itself. Modern users are comfortable with command-line installers, GitHub-hosted releases, unsigned side projects, beta software, and “copy this one-liner to get started” workflows. Attackers have recognized that the fastest path into a target environment may not be an exploit chain at all. It may be a branded command pasted by a willing user. [helpnetsecurity](https://www.helpnetsecurity.com/2026/05/27/deno-rat-malware-fake-chatgpt-claude-installers/)

## Trust, re-skinned

The mechanics are straightforward, but the psychology is refined. Researchers observed fake Claude installer pages promoted via Google Ads, carefully styled to resemble legitimate vendor pages, with most links either nonfunctional or looping back to the same landing page except for the download path. That design choice is not accidental. It minimizes complexity, narrows user focus, and turns the entire page into a funnel toward execution. [techradar](https://www.techradar.com/pro/security/threat-actors-are-clearly-adapting-to-the-widespread-interest-in-popular-ai-tools-ai-fans-beware-hackers-create-a-fake-claude-site-to-spread-backdoor-malware)

Graphika noted that several malicious sites replicated the visual identity of Claude and ChatGPT while using verified advertiser infrastructure to increase credibility, and in some cases pushed users toward terminal-based installation steps rather than ordinary downloads. That matters because terminal execution changes the victim’s mental model. A browser download may feel suspicious; a command-line install can feel advanced, intentional, and therefore safer to a technically inclined audience. [graphika](https://graphika.com/posts/malicious-commands-fake-claude-code-chatgpt-installers)

The most effective social engineering rarely argues with the target. It agrees with the target’s self-image. In this case, the target is the user who thinks, “I know what I’m doing.” The lure is not amateur urgency. It is professional familiarity.

## The malware chain behind the prompt

Underneath the branding, the delivery chains vary, but the logic remains consistent: get the user to run something that looks plausible, then pivot quickly into stealth and control. Malwarebytes reported that some fake AI software repositories instructed victims to open a terminal and paste a command that fetched either an MSI installer or a PowerShell script from GitHub, leading to the installation of DinDoor and then a Deno-based RAT. Sophos-linked reporting on fake Claude-themed installers similarly described a poisoned application package that used DLL sideloading to launch DonutLoader, which then deployed the Beagle backdoor. [techradar](https://www.techradar.com/pro/security/threat-actors-are-clearly-adapting-to-the-widespread-interest-in-popular-ai-tools-ai-fans-beware-hackers-create-a-fake-claude-site-to-spread-backdoor-malware)

This is a technically important detail. The lure is simple, but the payload chain is not. These operations are not relying on a single monolithic malware sample that can be blocked once and forgotten. They are using layered execution, staged loaders, and legitimate-looking packaging to increase resilience and reduce early detection. The fake installer is just the opening move. [helpnetsecurity](https://www.helpnetsecurity.com/2026/05/27/deno-rat-malware-fake-chatgpt-claude-installers/)

The infrastructure choice also tells its own story. Hosting on GitHub, GitLab pages, or SourceForge adds a borrowed legitimacy that many users still associate with developer authenticity and open tooling culture. Threat actors do not need to fully defeat user skepticism when they can route around it through familiar ecosystems. [graphika](https://graphika.com/posts/malicious-commands-fake-claude-code-chatgpt-installers)

## Why AI brands are such effective lures

Attackers are clearly adapting to the velocity of AI adoption. Popular AI tools now sit in the same category once occupied by remote administration utilities, browser add-ons, and collaboration software: frequently searched, urgently needed, and often installed outside traditional procurement controls. That makes them ideal bait for both consumers and technical users. [cybersecuritynews](https://cybersecuritynews.com/hackers-using-fake-claude-ai-installer-pages/)

The broader pattern is larger than a single article. Cybersecurity News separately reported fake Claude Code download pages dropping infostealers aimed at developers and IT professionals, while other campaigns have abused fake AI browser extensions and malicious developer packages that impersonate ChatGPT- and Claude-related tooling. The lesson is not merely that attackers like AI themes. It is that AI has become a believable software pretext across multiple layers of the ecosystem: desktop apps, browser extensions, developer dependencies, and command-line tools. [cybersecuritynews](https://cybersecuritynews.com/malicious-chrome-extension-steal-data/)

That breadth is what turns this from a scam into an operational trend. Once attackers discover that a theme converts across personas, they do not stay in one channel. They industrialize it.

## What defenders should learn from this

The immediate defensive advice is familiar: verify domains, avoid sponsored links, distrust terminal one-liners from unofficial pages, and prefer official vendor distribution channels. But the more interesting lesson is organizational. Many security teams still think of malware delivery as an event users download by mistake. These campaigns show that malware delivery increasingly looks like a workflow users believe is normal. [cybersecuritynews](https://cybersecuritynews.com/hackers-using-fake-claude-ai-installer-pages/)

That means detections should key off behavior, not just brand-themed filenames. Watch for browsers spawning shells, PowerShell launched from unusual parents, terminal sessions followed by network retrieval from code-hosting platforms, unsigned binaries dropped into user download paths, and child processes executing shortly after MSI or script-based installer activity. The phishing page may disappear. The execution chain is what remains.

There is also a training gap hiding here. Users have been taught for years to fear attachments and sketchy macros. Many have not been taught to fear polished fake software portals that ask them to copy a command into a terminal. For developers, analysts, and administrators, that distinction matters, because the scam is now speaking their language. [cybersecuritynews](https://cybersecuritynews.com/threat-actors-using-fake-claude-code/)

## The real compromise starts before execution

What makes these campaigns so compelling is that the compromise starts before the malware runs. It starts the moment the attacker successfully borrows legitimacy from a trusted AI brand and reframes unsafe behavior as standard setup procedure. By the time the victim reaches the payload stage, the social engineering has already succeeded. [cybersecuritynews](https://cybersecuritynews.com/hackers-using-fake-claude-ai-installer-pages/)

That is the deeper story here. Fake ChatGPT and Claude installers are not just malware droppers. They are evidence that attackers understand the modern software user well enough to package compromise as onboarding. The interface looks productive, the instructions feel familiar, and the malware arrives dressed as acceleration. [helpnetsecurity](https://www.helpnetsecurity.com/2026/05/27/deno-rat-malware-fake-chatgpt-claude-installers/)

The prompt was never the product. The installer was the intrusion. [graphika](https://graphika.com/posts/malicious-commands-fake-claude-code-chatgpt-installers)


Threat actors are turning fake ChatGPT and Claude installers into malware delivery systems by cloning branding, abusing ads, and pushing users toward terminal-based “install” steps. The attack is not just technical deception. It is workflow deception. [graphika](https://graphika.com/posts/malicious-commands-fake-claude-code-chatgpt-installers)
