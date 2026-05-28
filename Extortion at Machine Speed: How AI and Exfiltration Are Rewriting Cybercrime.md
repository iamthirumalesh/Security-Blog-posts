The cyber extortion story has changed: attackers increasingly do not need to lock your files when stealing your data, weaponizing disclosure pressure, compliance deadlines, and negotiation speed instead of pure operational disruption.


# Out of the Crypt: When Extortion Stops Encrypting and Starts Accelerating


How modern cybercriminals learned that stolen data, regulatory pressure, and AI-assisted speed can outperform ransomware at its own game.

Cyber extortion used to announce itself with a detonation. Systems froze, files changed extensions, and ransom notes appeared like flare signals across the enterprise. That model is still alive, but it is no longer the whole story. A quieter, faster, and in many ways more dangerous economy has taken hold: one where the attackers often skip encryption entirely, steal what matters, and let the victim’s own legal, regulatory, and reputational exposure do the coercion for them. 

Unit 42 reported that encryption appeared in 78% of extortion cases in 2025, down sharply from the near-or-above-90% levels observed between 2021 and 2024, while Resilience separately found extortion demands aimed only at suppressing stolen data rose from 49% in the first half of 2025 to 65% in the second half. That drop is more than a tactical adjustment. It signals a structural shift in how attackers calculate leverage, speed, and profit . [industrialcyber](https://industrialcyber.co/news/resilience-2025-cyber-risk-report-reveals-evolving-economics-of-extortion-material-cyber-losses/)

The old ransomware equation was brutally simple: deny operations, then monetize recovery. The new equation is colder. Exfiltrate first, move quickly, threaten exposure, and force the victim to negotiate against a shrinking clock shaped by disclosure mandates, litigation risk, customer trust, and executive panic . In this model, downtime is optional. Pressure is not.


## The leverage moved


Why would an attacker skip encryption, the most visible and historically effective extortion tool in the playbook? Because defenders got better at surviving it. Unit 42 points to improved backup and recovery, stronger endpoint controls, faster automated disruption, increasing exfiltration speed, and the rising weight of compliance-driven fallout as key reasons the extortion market is shifting toward data theft and exposure . 

That last driver matters more than many teams admit. The breach itself is no longer the only crisis. The countdown that follows can become part of the attack surface. Unit 42 argues that disclosure rules such as the SEC’s four-day window and GDPR’s 72-hour reporting expectation create a negotiation environment where threat actors know organizations may be racing internal assessment, legal review, board communication, and customer impact analysis at the same time . Put differently, compliance has become a force multiplier for extortion pressure .

The financial logic is equally blunt. Unit 42 says the average cost of data-theft extortion reached $5.08 million, and broader U.S. breach costs can exceed $10 million, which means the mere exposure of stolen data can rival or surpass the operational pain once dominated by encryption events . The attacker no longer has to prove they can cripple your business if they can prove they can complicate every decision you make next .

## The new playbooks

This shift is not abstract. Unit 42 describes multiple threat clusters whose methods reflect different entry points but the same underlying idea: pressure without necessarily encrypting .

One path begins in the software supply chain. Unit 42 says TGR-CRI-1135, also linked publicly to TeamPCP, has conducted more than 20 supply chain compromise attacks and injected malicious code into over 500 software packages, then used those intrusions to exfiltrate high-value secrets such as cloud access tokens, SSH keys, and Kubernetes secrets . The report adds that the group has monetized access by collaborating with extortion-as-a-service and ransomware-as-a-service operators, including LAPSUS$ operators and actors associated with Vect ransomware, showing how intrusion specialists and monetization specialists increasingly function as an ecosystem rather than isolated crews .

Another path begins with people instead of packages. Unit 42 says Bling Libra continues to use vishing to lure victims to phishing infrastructure that captures credentials and MFA codes, then registers attacker-controlled devices for persistence in targeted SaaS environments . That workflow is especially revealing because it turns identity into the intrusion path, the persistence layer, and the extortion enabler all at once . The compromise is not merely technical. It is operational, procedural, and psychological .

The pressure tactics also broaden. According to Unit 42, Bling Libra supplements data theft with DDoS attacks and leaks to media outlets, while another cluster, CL-CRI-1116, has used swatting as an additional coercive mechanism, pushing extortion beyond digital disruption into physical-world intimidation . That is a significant development because it collapses the traditional separation between cyber incident response and executive protection, between SOC workflows and crisis management .

## Speed is the story

If the modern extortion economy has a defining characteristic, it is not only theft. It is velocity. Unit 42 notes one case where threat actors moved from initial access to data exfiltration in just 39 seconds, and says that in AI-assisted scenarios the time from initial access to exfiltration has dropped to as little as 25 minutes . Those numbers should change how defenders think about dwell time, containment, and the practical meaning of “early detection” . 

A 39-second path to exfiltration does not leave room for slow escalation trees, manual evidence gathering, or a hunt program that starts only after the alert queue stabilizes. It demands detections that are already positioned around egress, identity abuse, unusual staging behavior, rapid privilege transitions, and SaaS control-plane anomalies before the first signal lands . In effect, the defender is no longer racing lateral movement alone. The defender is racing monetization .

This is where the report’s forward-looking warning becomes especially important. Unit 42 argues that frontier AI models will compress the intrusion lifecycle even further by helping threat actors identify vulnerabilities, chain them faster, and automate portions of the attack path . The report cites an example in which Anthropic disclosed that Mythos identified approximately 23,000 potential vulnerabilities across 1,000 open source software projects, and Unit 42 estimates there may be only a three-to-five-month window before frontier models are meaningfully weaponized by threat actors . Whether that exact timeline holds or not, the strategic point is clear: extortion operations are being optimized for speed, scale, and lower operator friction .

## What defenders should change

The defensive implication is not simply “focus on ransomware less.” It is to treat extortion as a choreography of identity, access, staging, exfiltration, coercion, and external pressure . Unit 42 recommends deploying DLP across cloud, endpoint, and network egress points; baselining abnormal egress volume and velocity; auditing SaaS OAuth grants and API permissions; enforcing conditional access; replacing OTP-based MFA with phishing-resistant methods such as FIDO2 or WebAuthn; hardening help desk verification against social engineering; and strengthening software supply chain integrity with dependency controls, secret rotation, provenance checks, and artifact signing .

For detection engineers and threat hunters, the practical lesson is sharper. Look for the behaviors that survive attacker rebranding: unusual egress, credential interception patterns, device registration anomalies, suspicious token use, CI/CD secret access, impossible-speed staging, and privilege changes that quickly lead to data collection . The extortion payload may never execute. The leverage may already be on its way out of the environment .

The metaphor that now fits best is not a bank robbery. It is a precision extraction. No shattered glass, no siren at the front door, just the sudden realization that the vault was emptied while everyone was still discussing whether the alarm was genuine . That is why this evolution matters so much. The attack is quieter, the negotiation starts earlier, and the blast radius is no longer limited to systems. It extends into legal deadlines, board pressure, public trust, and the physics of response time itself.

Cyber extortion has not abandoned ransomware. It has simply outgrown its dependence on it. 


Unit 42’s latest analysis shows the extortion economy is shifting away from encryption and toward pure data theft, regulatory pressure, and compressed attack timelines. The real story is not just ransomware evolving. It is extortion learning to move faster than response. 

