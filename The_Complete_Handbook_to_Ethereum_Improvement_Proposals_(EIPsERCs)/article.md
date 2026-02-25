# The Complete Handbook to Ethereum Improvement Proposals (EIPs/ERCs)

## Executive Summary

Ethereum Improvement Proposals (EIPs) form the backbone of how Ethereum evolves as a protocol. Whether you're a developer building smart contracts, a researcher exploring consensus mechanisms, or simply curious about how a decentralized blockchain makes technical decisions, understanding EIPs is essential.

This guide walks through every major aspect of the EIP ecosystem: what they are, how they're created, who decides their fate, and why some succeed while others fade away. You'll find clear explanations organized from foundational concepts to advanced topics.

Think of this as your practical companion for navigating Ethereum's technical governance—not just a reference, but a way to understand how decisions get made and where you might fit into the process.

---

## 1. Fundamentals

Before diving into process and governance, it's important to understand what EIPs actually are and how they fit into Ethereum's technical ecosystem.

### What is an EIP?

An EIP, or Ethereum Improvement Proposal, is a formal document that describes a proposed change, improvement, or new feature for the Ethereum protocol. Think of it as the blueprint for how Ethereum evolves. Every change to the base Ethereum protocol—whether it's a modification to how transactions work, a new opcode that smart contracts can use, or a standards track that defines how applications should interact—starts as an EIP.

The EIP process exists to ensure that changes to the world's most actively used smart contract blockchain are thoroughly reviewed, discussed, and documented before being implemented. This isn't just about technical quality—it's about maintaining community consensus and ensuring that the decentralized nature of Ethereum is preserved even as the protocol advances. Anyone can submit an EIP, which reflects Ethereum's open, permissionless philosophy. The proposals go through a structured review process where they can be refined, challenged, or rejected by the community before ever becoming part of the protocol.

### What is an ERC?

An ERC, or Ethereum Request for Comment, is a specific type of EIP that defines a standard or convention for the Ethereum ecosystem. While all ERCs are technically EIPs (they're numbered within the same sequence), not all EIPs are ERCs. The ERC designation is reserved for standards that application developers, wallet providers, and other ecosystem tools are expected to implement.

The name "Request for Comment" was borrowed from the internet's RFC (Request for Comments) process, which has governed how internet protocols evolve for decades. This naming choice signals Ethereum's ambition to build a robust, standards-driven ecosystem similar to how the internet evolved through open, collaborative standard-setting.

### What is the difference between an EIP and an ERC?

The distinction is straightforward once you understand the categories: ERCs are a subset of EIPs specifically designated for standards. When someone creates a new token standard, a new way to interact with smart contracts, or a convention for how decentralized applications should behave, they submit an ERC. These are the proposals that affect developers building on Ethereum most directly.

Other EIP types serve different purposes. Core EIPs propose fundamental changes to how Ethereum works at the protocol level—things like consensus mechanism changes or modifications to the EVM (Ethereum Virtual Machine). Networking EIPs address how Ethereum nodes communicate. Interface EIPs deal with the way applications and users interact with the blockchain. Meta EIPs describe processes around Ethereum itself, while Informational EIPs provide guidance without proposing a specific change.

The practical difference matters because ERCs typically require broader ecosystem adoption to be useful. A token standard only makes sense if wallets can recognize it, exchanges can support it, and decentralized applications can interact with tokens following that standard. This creates a different adoption curve than core protocol changes, which get implemented by client teams and automatically affect all network participants.

### EIP-1 and the EIP Template

Every formal EIP starts with a common foundation: EIP-1, which serves as the foundational document that defines the entire EIP process. This meta-proposal outlines exactly how EIPs should be written, submitted, reviewed, and ultimately accepted into the Ethereum protocol. Think of EIP-1 as the rulebook—the document that tells you how to play the game of proposing improvements to Ethereum.

When you're ready to submit an EIP, you don't start from a blank page. The EIP template provides a standardized structure that every proposal follows. This template includes specific sections: a preamble with metadata (EIP number, title, author, status, etc.), an abstract that summarizes the proposal in a few sentences, a motivation section explaining why the change is needed, a detailed specification of the technical changes, and finally a rationale section that explains why the chosen approach was preferred over alternatives.

The template isn't just bureaucratic overhead—it ensures that every EIP contains the information the community needs to properly evaluate it. Without this standardization, comparing proposals or reviewing their technical merits would become chaotic. The format also uses RFC 2119 keywords (like "MUST," "SHOULD," "MAY") to precisely define requirements, borrowing a practice from internet standards that removes ambiguity from technical specifications.

### Categories and Types of EIPs

EIPs are organized into several distinct categories, each serving a different purpose in the Ethereum ecosystem. Understanding these categories helps you quickly identify what kind of proposal you're dealing with and what implications it might have.

**Core EIPs** are the heavyweight proposals that affect the fundamental workings of Ethereum. These involve changes to the consensus mechanism, modifications to the EVM (Ethereum Virtual Machine), or alterations to block production and validation. Core EIPs require the broadest consensus because they affect every participant in the network—they're the proposals that can fundamentally change how Ethereum operates as a blockchain.

**Standards Track EIPs** (which become ERCs when they define standards) are what most developers interact with day-to-day. These proposals establish conventions and standards that applications can implement—everything from how tokens work to how wallets interact with smart contracts. When you hear about "ERC-20" or "ERC-721," you're hearing about standards track EIPs that have reached final status.

**Networking EIPs** handle how Ethereum nodes communicate with each other. These proposals modify the network protocol layer, affecting things like how transactions are broadcast across the network or how nodes discover and connect to each other.

**Interface EIPs** deal with the ways external applications and users interact with Ethereum. This includes changes to the JSON-RPC API (the primary way applications talk to Ethereum nodes) or other interaction standards.

**Meta EIPs** are fascinating because they describe processes around Ethereum rather than technical changes to the protocol itself. EIP-3675, which defined The Merge, is a meta-EIP—it documented the entire process of transitioning from proof-of-work to proof-of-stake. Meta EIPs are powerful tools for coordinating complex, multi-phase upgrades.

**Informational EIPs** provide guidance and information without proposing a specific change. These might document design rationale, explain security considerations, or offer best practices. They don't require the same implementation pathway as other EIP types.

### EIPs and Network Upgrades

One of the most important things to understand is how individual EIPs connect to the larger concept of network upgrades, sometimes called "Hard Forks." Ethereum doesn't implement EIPs one at a time in isolation—instead, multiple EIPs are bundled together into coordinated upgrades that get activated across the entire network simultaneously.

For example, the London upgrade included not just EIP-1559 (the fee market change) but several other EIPs addressing various improvements. The Dencun upgrade that introduced proto-danksharding similarly bundled multiple EIPs together. This bundling approach allows for coordinated testing and deployment, ensuring that all nodes and clients are prepared for the changes together.

The relationship works in both directions: EIPs propose changes, and network upgrades provide the mechanism for implementing those changes on the mainnet. When an EIP reaches "Final" status, it means it's been accepted as part of the standards track, but the actual activation on mainnet happens when the network upgrade containing that EIP is deployed. This creates a clear pipeline: ideas become EIPs, EIPs get implemented and tested, and successful EIPs get bundled into network upgrades that ship to the entire ecosystem.

This section covers the core concepts: the distinction between EIPs and ERCs, the role of EIP-1 as the foundational document, the different categories of proposals, and how EIPs relate to network upgrades. You'll also find explanations of the various EIP types—Core, Networking, Interface, ERC, Meta, and Informational—and what each category implies for implementation scope and community review.

We address questions like what makes something an EIP versus an ERC, how proposals connect to hard forks, and what the relationship is between these proposals and the broader Ethereum roadmap.

---

## 2. The Proposal Process

Once the fundamentals are clear, the next logical question is: how does an idea become an EIP?

This section walks through the complete lifecycle from initial idea to final implementation. We'll cover who can submit an EIP (the answer might surprise you—it's not limited to core developers), what sections every EIP must include, and what separates a good proposal from one that gets ignored.

### Who Can Submit an EIP?

One of the most beautiful aspects of Ethereum's governance model is its openness. Anyone can submit an EIP—you don't need to work for the Ethereum Foundation, you don't need to be a core developer, and you don't need any special credentials. This permissionless approach to proposing improvements is fundamental to Ethereum's decentralized philosophy.

That said, actually getting an EIP accepted and implemented requires much more than just submitting a document. You'll need to champion your proposal through discussions, address concerns from the community and implementers, and build consensus around your approach. The title "EIP Champion" is earned by anyone who puts in the work to drive a proposal forward, regardless of their background.

### What is the Role of an EIP Champion?

The term "EIP Champion" describes anyone who takes responsibility for driving a proposal forward through the entire EIP process. This isn't a formal title or position—it's a role you earn by putting in the sustained effort required to see an idea become reality.

A champion does far more than write the initial proposal. They're the ones who present the idea to the community, respond to feedback and criticism, revise the specification based on what they learn, build relationships with client implementers, advocate for the proposal during All Core Devs calls, and keep the momentum going during inevitable slow periods. Many excellent EIPs have languished and eventually been abandoned simply because their original author couldn't maintain that level of engagement.

What makes someone successful as a champion? Persistence matters enormously—the EIP process moves at its own pace, and proposals can spend months or years in various stages. You need thick skin to handle criticism and the humility to accept that your initial idea might need significant revision. Technical competence helps, of course, but so does the ability to communicate with different audiences: researchers, core developers, application builders, and the broader community all bring different perspectives.

The good news is that you don't have to do it alone. Champions often build small teams around their proposals, with others contributing expertise, documentation, or simply helping to spread the word. The most successful EIPs feel like genuine community efforts rather than one person pushing their personal agenda.

### How is an EIP Proposed?

The formal process starts on GitHub. You'd clone the official EIPs repository, create a new file using the standard EIP template, and submit it as a pull request. But the informal process often begins much earlier—on the Ethereum Magicians forum, in Discord channels, or at community events. The best EIPs typically have months or even years of discussion behind them before the formal PR is ever opened.

When you submit your PR, EIP editors will review it for proper formatting, completeness, and basic technical soundness. They're not evaluating the merit of your proposal—that's the community's job—but they ensure your EIP meets the structural requirements and follows the format specified in EIP-1. Once editors accept your submission, your EIP gets assigned a number and enters the system as a Draft.

### The GitHub Workflow: From Idea to Pull Request

The formal submission process follows a specific workflow that ensures every EIP gets proper tracking and review. Understanding this process helps you avoid common pitfalls that trip up first-time submitters.

First, you need to work with the official EIPs repository on GitHub. The repository lives at github.com/ethereum/EIPs, and you'll need to clone it to your local machine to create a new proposal. Make sure you're working with the latest version by pulling recent changes before starting your submission.

Next, create your EIP file. The repository contains a directory for each EIP type—EIPs for core proposals, ERCs for standards, and so on. Your file should be named with your EIP number (you'll use a placeholder initially) and follow the exact naming convention: eip-draft-NAME-CATEGORY.ext. The standard extension is .md for Markdown files.

The file itself must follow the EIP template exactly. This template is defined in EIP-1 and includes all the required sections we discussed earlier: the YAML preamble, abstract, motivation, specification, rationale, and backwards compatibility. Editors will reject submissions that don't follow this structure.

Once your file is ready, create a pull request against the main repository. Your PR description should include a clear summary of what your proposal does and why it matters. This is the first thing editors and reviewers will see, so make it count.

After submitting, be prepared for a back-and-forth with editors. They'll likely request changes—formatting fixes, clarifications, or additional information. This isn't criticism of your idea; it's ensuring your proposal meets the standards the ecosystem expects. Respond promptly and respectfully to keep the process moving.

Your PR will stay open for at least two weeks during the Last Call period once it reaches that stage, giving the community ample time to review. Throughout this process, keep your PR updated with any changes and respond to comments from reviewers.

A word on EIP numbers: they're assigned sequentially as proposals are accepted into the process, not chosen by submitters. You might have noticed people discussing "sniping" numbers—this refers to the practice of quickly submitting EIPs to claim a particular number, often for a memorable or significant-sounding sequence. While the number itself has no technical meaning, some submitters do prefer certain numbers for visibility. The editors manage this transparently, and there's no real advantage to "sniping" beyond personal preference.

### Transferring EIP Ownership

Life happens, and sometimes the original author of an EIP can no longer maintain it. Perhaps they've moved on to other projects, lost interest, or simply don't have the time anymore. In these cases, transferring ownership to a new author is straightforward.

The process involves updating the author field in the EIP's YAML header to reflect the new maintainer. The original author should ideally formally acknowledge the transfer, but in practice, if someone steps up to champion an abandoned EIP and demonstrates they can carry it forward, the community generally supports the transition.

This is actually one of the strengths of the EIP system: ideas don't die just because their original proponent moves on. If you find an EIP that's been abandoned but addresses a problem you care about, you can volunteer to become the new author and continue the work. Many valuable proposals have been rescued this way, giving new life to ideas that might otherwise have faded away.

The key principle is that the proposal itself matters more than who submitted it. As long as someone is willing to do the work of championing it, the community welcomes new stewards.

### What Makes a Good EIP?

A good EIP starts with clear motivation: why does Ethereum need this change? What problem does it solve? The best proposals identify a genuine pain point and demonstrate that the proposed solution is the right approach after considering alternatives.

The specification must be precise and unambiguous. Remember, this document will be implemented by multiple client teams, so it needs to be detailed enough that different implementers will arrive at the same result. Using RFC 2119 keywords (MUST, SHOULD, MAY) helps establish clear requirements rather than suggestions.

Good EIPs also anticipate objections. The rationale section should explain why you chose your approach over alternatives, and the strongest proposals often include thorough analysis of why alternative approaches were rejected.

Finally, good EIPs have champions who stick around. Proposing an EIP is just the beginning—you'll need to respond to feedback, revise your proposal, and advocate for it in discussions.

### What are the Mandatory Sections of an EIP?

Every EIP must include several required components to be considered valid for submission. These aren't optional niceties—they're the essential building blocks that allow the community to properly evaluate your proposal.

The **Preamble** sits at the top of every EIP in a specific YAML format. This includes your EIP number (assigned upon acceptance), a clear title, the author(s) with their name and optional contact information, the current status, the date the EIP was last updated, and optionally the category and sub-category. The preamble gives reviewers the basic facts they need to categorize and track your proposal.

The **Abstract** follows as a brief summary—typically three to five sentences—that captures what your EIP accomplishes. Think of it as the elevator pitch for your proposal. If someone reads nothing else, they should understand the core idea from this section.

The **Motivation** section is where you make the case for change. Why does Ethereum need this improvement? What problem does it solve? The strongest motivation sections quantify the pain point when possible and demonstrate that the status quo is genuinely insufficient. This is where you win over readers who might be skeptical about whether the change is necessary at all.

The **Specification** is the heart of your EIP—the technical detail that implementers will use to build the change. This must be precise enough that different teams reading your words will arrive at the same implementation. Ambiguity here leads to client fragmentation, which is exactly what the EIP process exists to prevent.

The **Rationale** explains your design choices. Why did you approach the problem this way rather than that way? What alternatives did you consider and reject? This section demonstrates you've thought deeply about your proposal and helps reviewers understand your reasoning.

Finally, the **Backwards Compatibility** section addresses whether your change breaks existing functionality. Every significant EIP must address this—Ethereum takes backward compatibility seriously, and proposals that introduce breaking changes need especially thorough justification.

### The EIP YAML Metadata Format

At the top of every EIP, you'll find a YAML block called the preamble. This isn't just administrative overhead—it's what makes EIPs machine-readable and easily trackable across the ecosystem.

The YAML preamble contains essential metadata: the EIP number (once assigned), a concise title, the author's name and contact information, the current status, the date of last revision, and optionally the category and sub-category. This structured format allows tools and websites to automatically parse EIP information, generate status dashboards, and track proposals through their lifecycle.

The format looks something like this in practice:

```
eip: 1559
title: Fee Market Change
author: Vitalik Buterin (@vbuterin), Eric Conner (@econoar)
status: Final
type: Core
category: Core
created: 2019-04-13
```

Why does this matter? First, it ensures consistency across hundreds of proposals. Second, it enables the official EIPs website to automatically display current status, category, and author information. Third, it makes it straightforward to build tools that track EIP progress, generate reports, or alert the community about important changes.

When you're submitting an EIP, getting the YAML right matters more than you might think. Editors will reject proposals with malformed metadata, and even small errors can cause your EIP to be missed by tools that aggregate proposal data.

### Timeline and Duration: How Long Does the Process Take?

There's no fixed timeline for an EIP—the process moves at the speed of community consensus, which can be remarkably fast for urgent issues or agonizingly slow for controversial proposals.

For straightforward ERC standards that solve clear problems, you might see an EIP go from Draft to Final within a few months if there's strong community support and no substantive objections. The review periods alone take time: Last Call requires a minimum of two weeks, and substantive feedback during Review can easily stretch into weeks or months.

More complex proposals can take years. EIP-1559, for instance, was discussed in various forms for over two years before being implemented in the London upgrade. The Merge (EIP-3675) was in development for even longer—years of research, implementation, and testing went into transitioning Ethereum's consensus mechanism.

The honest answer is that the timeline depends entirely on the proposal's complexity, controversy, and the availability of implementers to build it. What you can control is how responsive you are to feedback and how effectively you build consensus around your approach.

### How Does an EIP Get Implemented Into the Blockchain?

This is where many people get confused. Getting your EIP to Final status doesn't automatically mean it's running on mainnet—it means the standard has been accepted and is ready for implementation.

The actual implementation happens in Ethereum client software. Teams building clients like Geth, Nethermind, Besu, Erigon, and others read the finalized EIP specification and write code that enforces the new rules. Each client team decides independently when and how to implement a given EIP.

Once a client implements the EIP, it must be activated on the network. For most EIPs, this happens through a network upgrade (hard fork). The upgrade bundles multiple EIPs together, and all clients must support the new rules for the upgrade to activate successfully. If a significant portion of the network doesn't implement the upgrade, you risk a chain split—which is precisely what the coordinated upgrade process is designed to prevent.

For ERC standards, the path is different. Since ERCs define application-level standards rather than protocol changes, there's no network upgrade required. Implementation means wallet developers, exchange operators, and dapp builders choosing to support your standard in their software. This adoption happens organically when the standard proves valuable.

### How Do Testnets Play a Role in EIP Implementation?

Testnets are the essential proving ground where EIPs get validated before touching real money. These separate Ethereum networks allow developers to experiment with new features without risking mainnet funds or stability.

When an EIP moves toward implementation, client teams typically deploy it on testnets first. This serves multiple purposes: it verifies that the specification is implementable across different clients, it allows security researchers to find vulnerabilities in a low-stakes environment, and it gives the broader developer community a chance to build and test against the new features.

Major testnets like Sepolia and Holesky (or the older Goerli and Ropsten) serve different purposes. Some are closer to mainnet conditions, others are designed for specific testing scenarios. Implementers and auditors spend significant time on testnets before any mainnet deployment.

For ERCs, testnets matter less since there's no protocol-level change to test. But developers building applications that use new ERC standards still thoroughly test on testnets to ensure their implementations work correctly before deploying to mainnet.

---

## 3. Discussion and Governance

EIPs don't exist in a vacuum—they emerge from community discourse and are shaped by competing interests. This section explores the human side of Ethereum's technical governance.

### Where EIPs Are Discussed

The primary gathering place for EIP discussions is the Ethereum Magicians forum. This community-driven platform hosts in-depth discussions about proposals, allowing anyone to post ideas, ask questions, and provide feedback. Before most formal EIP submissions, you'll be expected to social your proposal on Ethereum Magicians—it's where the community hashes out ideas and identifies potential issues.

The GitHub repository also plays a crucial role, with pull requests serving as the formal submission mechanism and issues providing a venue for tracking problems and enhancements. All Core Devs calls (often called ACDE calls) are where core developers discuss and prioritize proposals, making them essential for understanding which EIPs are gaining traction.

### Ethereum Magicians

The Ethereum Magicians forum was created to provide a structured space for technical discussions that GitHub issues weren't designed for. It's where proposals go to be refined through community input, where concerns get raised and addressed, and where consensus-building happens publicly.

What makes Magicians special is its culture of thoughtful, technical discussion. This isn't social media—it's a forum where proposals receive rigorous examination from experts across the ecosystem. Many EIPs that look good on paper get significantly improved through Magicians discussions, and some that seemed promising are ultimately abandoned when fundamental issues are identified.

### Must Every EIP Be Discussed on Ethereum Magicians First?

There's no hard requirement that forces you to post your proposal on Ethereum Magicians before submitting a formal PR to the GitHub repository. However, skipping this step is generally a bad idea—and most submitters who've tried it have learned this the hard way.

The practical reality is that editors and reviewers will ask whether you've discussed your proposal publicly anyway. If you submit an EIP without any community discussion behind it, you'll likely face significant friction during the review process. The community values proposals that have been stress-tested through public discourse, and for good reason: the best ideas emerge from feedback, and proposals that haven't been discussed often have obvious gaps that could have been caught earlier.

Posting on Ethereum Magicians gives you a chance to refine your proposal before it enters the formal process. You get feedback from experienced community members, identify potential problems with your approach, and build early support for your idea. Proposals that come to the table with months of thoughtful discussion behind them tend to progress much faster than those that arrive without any community engagement.

There's also a social dimension: the Ethereum ecosystem values collaboration and inclusivity. Submitting a proposal without any prior discussion can come across as attempting to bypass community input—which is exactly the opposite of how Ethereum's open-source culture works.

So while it's not technically mandatory, discussing your proposal on Ethereum Magicians (or similar venues like the Ethereum Research forum, EIP Improvement Proposal discussions, or even community Discord channels) is essentially expected. Think of it as doing your homework before presenting to the class.

### EIP Editors

EIP Editors serve as the gatekeepers of the EIP process. They're volunteers who review submissions for proper formatting, ensure all required sections are present, verify technical correctness at a basic level, and help authors navigate the process. Think of them as the first line of review—they're not deciding whether an EIP is "good" or "bad," but rather whether it's properly structured and ready for community consideration.

The editor role is demanding and often thankless. Editors must understand the EIP format thoroughly, stay current with Ethereum's technical landscape, and handle a steady stream of submissions with patience and consistency. The current roster of editors is listed on the EIPs website, and new editors are added as the community recognizes individuals who contribute significantly to the process. 

### Who are the Current EIP Editors?

The EIP editor roster changes over time as dedicated volunteers step up to help maintain the process. The current list of editors is always visible on the official EIPs website at eips.ethereum.org, where you can see who's actively reviewing submissions and shepherding proposals through the process.

What might surprise you is that editors aren't hired or paid by any organization—they're community members who've demonstrated commitment to Ethereum's technical health and have earned the trust of the broader community. The role involves reviewing submissions for proper formatting, ensuring technical soundness at a basic level, and helping authors navigate the sometimes-complex process. It's work that demands both technical knowledge and patience.

If you're interested in becoming an editor, the path typically involves actively participating in the EIP process, demonstrating good judgment, and eventually being nominated by existing editors or community members who've noticed your contributions.

### Who Approves a Core EIP?

This is where things get interesting, because Ethereum doesn't have a single authority who "approves" anything. Instead, approval emerges from a complex web of stakeholders reaching consensus.

Core EIPs require the broadest alignment because they change fundamental protocol rules. The process involves several layers: EIP editors verify the proposal meets basic requirements, then the broader community discusses and raises concerns through Ethereum Magicians and other venues. But the decisive moment typically comes during All Core Devs calls, where client implementers discuss which EIPs are ready for inclusion in upcoming network upgrades.

What this means practically is that a Core EIP needs to satisfy multiple groups: it must have a clear specification, it must be implementable across different clients, and most importantly, the core developers must agree that it's worth including in the next upgrade. No single person can approve a Core EIP—approval is a social process that requires building consensus across the ecosystem.

### Understanding Ethereum's Governance Model

The question of "who really decides" gets at something fundamental about Ethereum: the governance is deliberately decentralized and somewhat informal compared to traditional organizations.

The Ethereum Foundation plays an influential role—they fund research, coordinate events, and employ many core developers—but they don't control the protocol. Core developers have significant influence because they're the ones who actually implement changes, but they're also accountable to the broader community. Validators and miners (post-Merge, it's validators) have economic power to reject changes they disagree with. Users and application developers vote with their feet by choosing which chains and standards to support.

This creates a system of checks and balances where no single party has absolute control. Proposals succeed when they build broad consensus across these stakeholders, and proposals fail when they can't overcome objections from key groups. It's messy sometimes, but that's the nature of decentralized governance.

### What is the ACDE Call?

The All Core Devs Execution call (ACDE) is a weekly synchronous meeting where the people actually building Ethereum gather to discuss what's happening. Think of it as the operational heart of Ethereum's technical coordination.

These calls include representatives from all major client teams—Geth, Nethermind, Besu, Erigon, and others—along with researchers and Ethereum Foundation staff. They discuss which EIPs are ready for implementation, review progress on upcoming network upgrades, coordinate timing for testnet and mainnet deployments, and flag any issues that need broader community attention.

For EIPs, the ACDE is crucial because this is where the rubber meets the road. Even a finalized EIP won't go anywhere without the support of client teams willing to implement it. The ACDE calls are where implementers signal whether they're comfortable with a proposal, where concerns get raised directly, and where decisions get made about what goes into the next upgrade.

These calls are publicly accessible—you can listen in on the Ethereum Foundation's YouTube channel or participate live through the appropriate channels. The meetings are documented in the Ethereum PM repository, giving you a permanent record of how decisions were made and what issues were discussed.

We also explore the tension between Ethereum's "implicit" governance (informal norms and social consensus) and the "explicit" governance that EIPs represent, plus where ideas originate before they become formal proposals—through EIPIP, Discord channels, research forums, and more.

### Governance Fatigue

Anyone who's spent time in Ethereum's technical discussions has felt it: that glazed-eye exhaustion when yet another EIP sparks months of debate, when familiar arguments resurface for the hundredth time, or when it seems like nothing ever gets resolved. Governance fatigue is that sense of burnout that comes from participating in endless technical discussions about the protocol's future.

It manifests in a few recognizable ways. You'll notice people stop responding to threads even when they have opinions—the same voices show up in every discussion while others tune out. You'll see proposals that clearly have merit get stuck in limbo because the energy to push them forward simply isn't there. You'll hear frustration that "we've been talking about this for years" without resolution.

The fatigue is real because Ethereum's governance is genuinely demanding. The process requires deep technical engagement, and the same people often end up reviewing proposal after proposal. When you're someone like a core developer who needs to evaluate dozens of EIPs per year, each requiring careful consideration of security implications, implementation complexity, and ecosystem impact, the cognitive load adds up.

What makes governance fatigue particularly tricky is that it tends to concentrate among the most active participants. Those who disengage are often exactly the voices the community needs most—the experienced implementers, the security-minded reviewers, the people who've seen similar proposals fail before. Meanwhile, newer participants may not realize they're joining a conversation that's already exhausted its veteran reviewers.

The community has developed some coping mechanisms. Breaking large discussions into focused working groups helps—rather than debating everything at once, specific stakeholders can hash out details in smaller settings. Setting clearer timelines creates urgency that prevents indefinite deliberation. Celebrating incremental progress keeps morale up when full solutions seem far away. But governance fatigue remains one of the honest challenges facing Ethereum's decentralized decision-making.

### Where Ideas Come From Before Becoming EIPs

The formal EIP process starts with a pull request, but the ideas themselves have a much longer genesis. Understanding where proposals originate helps explain why some succeed and others struggle.

The Ethereum Improvement Proposal Initiative, or EIPIP, serves as an informal working group that discusses potential improvements before they become formal proposals. Think of it as the conceptual stage where problems get identified and potential solutions get brainstormed. These discussions happen in dedicated channels on the Ethereum Discord server and occasionally in Ethereum Foundation research forums. The output isn't EIPs yet—it's problem statements, rough designs, and early feedback from researchers and developers.

The research forums at ethresear.ch (now largely migrated to the Ethereum Research discussion space) are where more academic exploration happens. When someone is thinking about fundamental changes to consensus, new cryptographic primitives, or complex economic mechanisms, they often start here with a research post rather than jumping straight to an EIP. The tone is more exploratory—there's no expectation of a polished proposal, just the goal of getting expert feedback on early ideas.

Discord has become increasingly important for day-to-day technical conversation. Client teams have their own channels where implementation challenges get discussed. Working groups form around specific initiatives (like the account abstraction work that led to ERC-4337). Informal conversations in these spaces often plant the seeds for formal EIPs—the difference is that Discord discussions tend to be more ephemeral, so the challenge is capturing good ideas before they get lost in chat history.

The Ethereum Magicians forum remains crucial for proposals that are closer to formal submission. By the time an EIP PR is opened, the author should have already spent weeks or months discussing the idea publicly. The forum's structure, with threaded discussions and category organization, is better suited than Discord for capturing the back-and-forth that shapes a proposal.

What distinguishes successful proposals is that they've been stress-tested in these early venues before entering the formal process. An EIP that arrives on GitHub having only been discussed among a small group of collaborators will face tougher scrutiny because reviewers don't know the history. Proposals that have evolved through community feedback tend to be more robust—the process is designed to catch problems, but it works best when submitters have already done significant self-review.

### How Different Stakeholders Influence EIPs

Ethereum's governance isn't controlled by any single group, which means proposals need to build support across a diverse ecosystem. Understanding who the stakeholders are—and what they care about—explains why some EIPs sail through while others get stuck.

**Core developers and client implementers** hold enormous practical power because they're the ones who actually write the code. Even a brilliant proposal will go nowhere if no client team is willing to implement it. Their concerns tend to be implementation-focused: Is this feasible? Does it create technical debt? Will it conflict with other ongoing work? When a proposal has strong implementer support, it tends to move forward; when implementers are skeptical or too busy, the proposal stalls regardless of community enthusiasm.

**Validators** (post-Merge, replacing miners) have economic skin in the game. They run the infrastructure that secures the network, and they're paying attention to changes that affect their operations. A proposal that increases validation costs without clear benefits will face pushback from this group. After the Merge, validators also have voice through their stake in the protocol's long-term health—they're not just running nodes today but expecting to do so for years.

**Users** might seem distant from EIP discussions, but they exercise power through adoption. If an EIP would make the network harder to use, more expensive, or less reliable, users will vote with their feet—by using alternative chains, by holding rather than transacting, or simply by complaining loudly enough that developers notice. The challenge is that users are a diffuse group with diverse interests, making their influence harder to organize than other stakeholders.

**Wallet developers and dapp builders** sit in a crucial position. They implement standards that users actually interact with, so an ERC that wallets refuse to support will struggle to achieve adoption regardless of its technical merit. These developers are often the first to identify problems worth solving—they're building applications on top of Ethereum and know where the pain points are. Their support can make an ERC successful; their opposition can doom it.

**Exchanges and other infrastructure providers** matter particularly for token standards. If a new ERC isn't supported by major exchanges, it won't achieve the liquidity that makes a token useful. These players are businesses with their own development priorities, so they tend to focus on widely-adopted standards rather than novel proposals.

**The Ethereum Foundation** plays a unique role—more influential than any single participant but not controlling. The Foundation funds research, coordinates events, and employs many core developers, but they can't mandate outcomes. Their support can accelerate a proposal by providing resources and legitimacy; their opposition can make proposals DOA. But the Foundation also learned from early controversies that they can't force anything through—the community will resist perceived top-down mandates.

What makes EIP governance work is that no single group can push through a controversial proposal alone. A proposal needs to satisfy enough stakeholders to build broad consensus. When it fails, it's usually because some key group wasn't convinced—and when it succeeds, it's because the proposal addressed concerns across the ecosystem.

### Unwritten Rules and Norms of EIP Participation

The EIP process has formal rules documented in EIP-1, but the community operates according to a set of informal expectations that newcomers often stumble upon. Understanding these unwritten rules helps proposals move forward smoothly.

**Do your homework before posting.** The worst way to start an EIP discussion is to present an idea that clearly hasn't been researched thoroughly. Reviewers will immediately ask: Has this been tried before? What are the alternatives? Why isn't a simpler solution sufficient? Coming with evidence that you've considered existing work and can articulate why your approach is better makes a huge difference. The community respects proposals where the author has demonstrated genuine understanding of the problem space.

**Engage with criticism rather than dismissing it.** When someone raises an objection to your proposal, your response matters enormously. The quickest way to lose credibility is to dismiss concerns, argue dismissively, or disappear after receiving feedback. Even if you disagree with a criticism, engage with it respectfully and explain your reasoning. Often, the best proposals emerge from exactly this back-and-forth—the author addresses concerns, revises the specification, and ends up with something stronger.

**Be patient with the timeline.** Ethereum moves at its own pace. A proposal that was "almost ready" six months ago might still be in progress because new issues emerged, implementation took longer than expected, or the community needed more time to deliberate. Getting frustrated with the process or pushing for faster progress rarely helps. The champions who succeed are those who maintain steady engagement over months or years without losing momentum.

**Give credit where it's due.** If your proposal builds on someone else's work, acknowledge it. If someone contributed significantly to your thinking, credit them. The Ethereum technical community is relatively small, and building a reputation for generosity with attribution serves you well in future proposals. Conversely, appearing to take credit for others' ideas is a quick way to lose trust.

**Respect the venues.** Different spaces serve different purposes. Ethereum Magicians is for substantive discussion, not hot takes. GitHub issues are for tracking problems with existing EIPs, not brainstorming new ones. Discord is for real-time conversation, not formal proposals. Using the right channel for the right type of communication shows that you understand the ecosystem's norms.

**Support other proposals generously.** Reviewing other people's EIPs is genuinely valuable work that keeps the ecosystem healthy. When you provide thoughtful feedback on others' proposals, you're contributing to the commons—and people notice. Champions who are known for helping others tend to get more help when they have their own proposals.

These norms aren't enforced by anyone, but they're taken seriously by the community. Proposals that follow them tend to progress smoothly; proposals that ignore them often find themselves stuck despite technical merit.

### Building Consensus in EIP Discussions

Consensus in the EIP process isn't like a parliamentary vote—there's no formal tallying of ayes and nays. Instead, consensus emerges through a gradual process of discussion, refinement, and alignment. When you're championing an EIP, your job is to gather feedback, address concerns, and evolve your proposal until it no longer faces significant objections.

The practical reality is that consensus means "no strong opposition from key stakeholders." You'll know you've reached consensus when the major concerns have been addressed, the relevant implementers signal they're comfortable with the proposal, and discussion naturally winds down rather than reigniting with new objections. This often takes the form of a "seems good" or similar acknowledgment from core developers or other influential participants.

What this means practically is that you need to actively seek out dissenting voices, not just wait for comments. The loudest participants in a discussion aren't always the most important stakeholders. Sometimes the critical feedback comes from someone who only speaks up when they see a genuine problem. Champions who succeed in building consensus are those who make a point of asking: "Does anyone see a reason we shouldn't move forward?"—and then genuinely listening to the answer.

The process rewards patience and responsiveness. Proposals that rush toward completion without adequately addressing concerns tend to stall later—sometimes years later, when implementation reveals problems that discussion could have caught. Proposals that take the time to build genuine consensus tend to progress smoothly once they reach the final stages.

### Handling Competing or Conflicting EIPs

Sometimes multiple people or groups have ideas that solve similar problems in different ways. This creates a natural tension: which approach should the ecosystem adopt? The EIP process handles this through a combination of discussion and, eventually, convergence.

When competing EIPs emerge, the community's first instinct is usually to see if the approaches can be merged. Often, the best solution combines elements from different proposals. This is where the collaborative nature of the process shines—rather than treating it as a competition, the most productive outcomes come when authors work together to synthesize the strongest elements from each approach.

If merging proves impossible, the community typically lets the proposals evolve in parallel until one clearly gains more traction. This isn't a formal competition—it's emergent consensus. The proposal with stronger implementation support, better-aligned stakeholders, and more robust design tends to win adoption naturally. Trying to force a specific approach when the community favors another rarely works in the long run.

There's also the case of one EIP replacing another. Sometimes an author will explicitly mark their proposal as replacing an earlier one, acknowledging that the new proposal supersedes the old. This often happens when the original author agrees their approach was inferior or when the new proposal builds on the original work in a way that makes the older version obsolete.

The honest truth is that having multiple competing proposals isn't necessarily a problem—it's often a sign of healthy interest in an important area. The community benefits from exploring multiple approaches, and the best ideas tend to emerge from that competition naturally.

---

## 4. Understanding EIP Statuses

Every EIP carries a status that reflects where it stands in the process. Understanding what each status means is crucial for tracking proposals.

### The Status Journey

An EIP typically progresses through several status stages on its way to becoming part of the protocol. Starting as a **Draft**, the proposal is considered a work in progress. At this stage, the author is actively developing the specification and incorporating feedback from initial reviews.

From Draft, an EIP moves to **Review** status, indicating that the proposal is ready for broader community examination. This is when substantive technical discussions typically occur—reviewers are looking for completeness, correctness, and whether the proposal achieves its stated goals without introducing unintended consequences.

The **Last Call** status is the final review period before a standards track EIP can be marked as Final. During this time, the community has one last chance to identify any remaining issues. Last Call typically lasts at least two weeks, giving everyone a chance to thoroughly vet the proposal. If no substantive issues arise, the EIP moves to Final status.

A **Final** EIP represents an accepted standard that has been implemented and is considered stable. For ERCs, this means the standard is ready for broad adoption by wallets, exchanges, and decentralized applications. For Core EIPs, Final status indicates the change has been accepted and will be included in an upcoming network upgrade.

### Draft vs Review: What's the Difference?

The distinction between Draft and Review matters because it signals the author's confidence in their proposal. When an EIP is in Draft status, the author is essentially saying "this is still a work in progress—expect significant changes." The specification may be incomplete or have known issues that need addressing.

Review status signals that the author believes the proposal is complete and ready for serious evaluation. It's an invitation to the community: "please look at this now, we've done our homework." Moving an EIP to Review is a meaningful commitment—it suggests the author is prepared to defend the proposal against scrutiny and may have already incorporated significant feedback from earlier discussions.

### What is Last Call?

Last Call is the community's final warning before a proposal becomes locked in. It's designed to catch edge cases and last-minute issues that might have been overlooked. During Last Call, editors are particularly vigilant for problems, and the community is encouraged to review proposals carefully.

The two-week minimum period ensures adequate time for reviewers in different time zones and with different schedules to see the announcement. If serious issues are discovered during Last Call, the EIP can be moved back to Review or even to Draft for fixes.

### Can a Final EIP Be Changed?

Yes, but it's rare and carefully controlled. Final EIPs can be updated through a process that requires clear justification and community consensus. The key principle is backward compatibility—whenever possible, changes to Final EIPs must not break existing implementations.

For living standards like ERC-20, the evolution continues even after Final status. Extensions and improvements can be proposed as new EIPs, and the original standard may be updated to address clarifications or edge cases. The goal is stability—inventorying standards that thousands of projects depend on—but not rigidity.

### Withdrawn vs Rejected

These statuses sound similar but have different implications. **Withdrawn** means the author decided to stop pursuing the proposal. Perhaps the author lost interest, found the approach unworkable, or decided to pursue a different direction. Withdrawn EIPs remain in the historical record but are no longer actively developed.

**Rejected** means the community decided against accepting the proposal. This happens when fundamental objections can't be resolved or when the proposal conflicts with Ethereum's direction. Unlike Withdrawn, a Rejected status carries the community's judgment that the proposal should not be implemented.

### Stagnant EIPs

An EIP becomes Stagnant when there's been no activity for an extended period—typically six months. This status prevents the repository from filling up with abandoned proposals while still preserving them as part of the historical record.

Stagnant EIPs can be resurrected if someone steps up to champion them. If you find a Stagnant EIP that addresses a problem you care about, you can volunteer to take over as the new author and move the proposal back into active development.

This section details each status level: Draft, Review, Last Call, Final, and what it means when an EIP is Stagnant, Withdrawn, or Rejected.

### Exact Criteria for Status Transitions

Moving between statuses isn't arbitrary—each transition has specific requirements that ensure proposals don't advance prematurely.

**From Draft to Review** requires that the author believes the specification is complete. There's no formal vote or approval needed at this stage—it's the author's decision that the proposal is ready for serious scrutiny. However, editors will likely flag issues if they see obvious problems, and the community will provide feedback quickly once the proposal is in Review status.

**From Review to Last Call** signals that the author believes the proposal has survived community examination and is ready for final vetting. This transition also has no formal approval process—it's the author's call. However, the Last Call status comes with a time requirement: at least two weeks must pass during Last Call before the EIP can move to Final. This gives the community a predictable window to identify any remaining issues.

**From Last Call to Final** happens automatically after the waiting period if issues no substantive are raised. If serious problems are discovered during Last Call, the EIP moves back to Review (or even to Draft) to address them. The distinction between "substantive" and "minor" issues is sometimes debated, but the practical reality is that community consensus determines what blocks Final status.

### Updating Final EIPs

Final doesn't mean frozen forever. Changes to Final EIPs are possible, but they're treated carefully to avoid breaking the ecosystem.

The process for updating a Final EIP involves submitting a new EIP that modifies or extends the original. This new proposal goes through the full process again—Draft, Review, Last Call, Final. The key principle is backward compatibility: changes should not break existing implementations without strong justification.

For living standards like ERC-20, this is particularly relevant. The original ERC-20 specification has undergone clarifications and errata over the years, and new extensions have been proposed to add functionality. The community treats the "Final" status as meaning "stable and ready for adoption," not "never can be changed."

If you're implementing an ERC, it's worth checking whether there are newer EIPs that update or clarify the standard you're working with. The ecosystem evolves, and keeping up with those changes often leads to better implementations.

### Resurrecting a Stagnant EIP

Stagnant status isn't a death sentence. If you find an EIP that was abandoned but addresses a problem you care about, you can bring it back to life.

The process involves reaching out to the original author first—they may be willing to transfer ownership or might have context that would help. If you can't reach them or they prefer not to continue, you can essentially adopt the EIP by volunteering to become the new author.

Once you're the champion, you update the EIP to reflect current thinking, address any issues that were raised during the original discussion, and move it back into active status. Many valuable EIPs have been rescued this way, giving new life to proposals that the original author simply didn't have time to pursue.

This mechanism ensures that good ideas don't die just because their original proponent moved on. The EIP process is designed around the principle that what matters is the proposal itself, not who submitted it.

---

## 5. Technical Implementation

This section gets into the engineering side of EIPs: how they actually become code in the Ethereum clients.

### How Client Implementers Participate

Client implementers are the engineers who build the software that runs Ethereum—teams behind Geth (the most popular client), Nethermind, Besu, Erigon, and others. Their role in the EIP process is absolutely crucial because an EIP is just words on a page until someone writes code to implement it.

These teams participate in several ways. During the discussion phase, implementers provide technical feedback about whether a proposal is feasible, whether it creates implementation challenges, and whether it might conflict with other ongoing work. Their practical experience with the codebase is invaluable for identifying issues that theoretical discussions might miss.

When an EIP reaches the implementation phase, client teams decide whether and when to build support for it. A proposal with strong community support but no client implementation will never activate on mainnet. Different clients sometimes implement the same EIP differently, which can lead to compatibility issues—the EIP process exists partly to prevent this by providing clear specifications.

The relationship between client teams and EIP authors is collaborative. The best EIPs are those where authors have consulted with implementers early and often, incorporating their feedback into the specification. This is why you'll often see client developers actively participating in Ethereum Magicians discussions.

### Gas Costs and EIPs

Gas costs are the fees users pay to execute operations on Ethereum, and any EIP that affects computation must carefully consider how it impacts these costs.

When a new EIP introduces operations that weren't possible before, someone has to determine how much those operations should cost. Get this wrong, and you create security vulnerabilities or economic imbalances. Operations that are too cheap can be exploited by attackers; operations that are too expensive discourage legitimate use.

The process for determining gas costs involves analysis of the computational complexity, benchmarking against existing operations, and community discussion. Historical examples show the importance of this: some early EIPs had to be revised because their gas cost assumptions were incorrect once implemented and observed in the wild.

For users, this means that EIPs can directly affect what you pay in transaction fees. The introduction of new opcodes or precompiles always comes with a gas cost analysis that determines how expensive that new capability will be to use.

### Precompile EIPs vs Opcode EIPs

Understanding the difference between precompiles and opcodes helps you understand what's actually changing in the protocol.

**Opcodes** are the fundamental operations that the Ethereum Virtual Machine (EVM) understands natively. When you write a smart contract, your code gets compiled into EVM instructions—these are opcodes. Adding a new opcode means extending the virtual machine itself with a new capability.

**Precompiles** are different. They're special contracts built into the protocol that perform specific cryptographic or computational operations more efficiently than implementing them in Solidity would allow. Operations like elliptic curve signature verification (used in many scaling solutions) are implemented as precompiles because doing the math in native code is much cheaper than implementing it as a series of opcodes.

The practical difference matters for developers: new opcodes change what the EVM can do fundamentally, while new precompiles add optimized versions of operations that might be possible some other way. Both require EIP proposals, but they affect the protocol at different levels.

### EIPs and Backward Compatibility

Backward compatibility is one of Ethereum's core principles, and every significant EIP must address it.

The general rule is that existing smart contracts should continue to work after any change. Ethereum achieves this through careful design: new features are added in ways that don't break existing behavior, and when breaking changes are absolutely necessary, they're typically implemented through planned migrations rather than sudden cuts.

EIPs must include a "Backwards Compatibility" section that explicitly addresses how the proposal interacts with existing contracts and systems. If your EIP would break existing deployments, you need to explain why the break is justified and how the ecosystem should handle the transition.

This commitment to backward compatibility is what makes Ethereum reliable for developers building applications. You can deploy a smart contract today and trust that it will continue to work even as the protocol evolves—because every change is designed with compatibility in mind.

### EIP Formatting Rules

The EIP format isn't arbitrary—it follows specific conventions that ensure consistency and readability across hundreds of proposals.

**Markdown style** is the foundation. EIPs are written in Markdown, which provides a clean way to structure documents with headers, lists, code blocks, and links. The format is relatively permissive, but proposals should follow common Markdown conventions to ensure readability.

**RFC 2119 keywords** are crucial for technical precision. These keywords—MUST, SHOULD, MAY, MUST NOT, SHOULD NOT—have specific meanings that make requirements unambiguous. When an EIP says something "MUST" happen, that's a hard requirement. "SHOULD" indicates a strong recommendation but allows exceptions with justification. This precise language prevents misunderstandings about what's required versus suggested.

**Linking conventions** matter for navigability. EIPs should link to other EIPs using the standard format (like "EIP-20" or "ERC-20") rather than just mentioning them. External resources can be linked, but the primary reference should always be to other EIPs when discussing related work.

Following these rules isn't just about aesthetics—it ensures that EIPs are consistent, searchable, and properly integrated into the ecosystem's knowledge base.

### How EIP Dependencies Work

Sometimes one EIP relies on another to function properly. These are called dependencies, and the EIP process has a specific way of handling them.

When your proposal depends on another EIP—whether that's another proposal that defines functionality you're building on or an infrastructure EIP that needs to be finalized first—you explicitly reference that dependency in your specification. This tells reviewers and implementers that your proposal can't be fully understood or implemented without the dependent EIP.

The EIP format allows you to specify requires and required-by fields in the YAML header. This creates a clear paper trail showing the relationship between proposals. For example, if you're proposing a new token standard that builds on existing interface patterns, you'd reference those foundational EIPs so readers know what background they need.

Why does this matter? It helps the community understand the relationship between proposals and coordinate their development. When multiple EIPs have interdependencies, understanding those relationships helps everyone involved prioritize work and understand what needs to happen in what order. It also helps editors and reviewers assess whether a proposal is ready to move forward—if it depends on another EIP that's still in early Draft status, that might affect timing expectations.

---

## 6. ERC Standards Explained

ERC (Ethereum Request for Comment) standards are the most visible category of EIPs because they define how developers build applications. This section covers the standards track and what makes ERCs different from other EIP types.

### The Big Three: ERC-20, ERC-721, and ERC-1155

These three standards represent the most widely adopted ERCs in the ecosystem, each serving a distinct purpose in how digital assets work on Ethereum.

**ERC-20** emerged as the standard for fungible tokens—tokens where every unit is identical to every other unit, like currency. If you're building a utility token, a governance token, or any asset where one token equals another, ERC-20 is your foundation. This standard defines a common interface for transferring tokens, checking balances, and approving third-party spending. Its simplicity and widespread support made it the backbone of the ICO boom and continues to power the majority of tokens on Ethereum today.

**ERC-721** came along to solve a fundamentally different problem: non-fungible tokens, or NFTs. Where ERC-20 tokens are like dollar bills (each one is interchangeable), ERC-721 tokens are like unique collectibles—no two are exactly alike. This standard gained massive cultural traction for digital art and collectibles, but its applications extend far beyond that: it enables tokenized real estate, identity credentials, in-game items, and any asset where uniqueness matters.

**ERC-1155** represents a more flexible approach that can handle both fungible and non-fungible tokens within a single smart contract. This efficiency matters for gaming and other applications where you might need thousands of identical items (fungible) alongside unique assets (non-fungible). Rather than deploying separate contracts, developers can manage everything through one efficient system.

### Do Developers Have to Follow Finalized ERCs?

Finalized ERCs aren't law—you're not required to implement them. However, there are strong practical reasons to follow established standards. When you use ERC-20 for your token, wallets can automatically display balances, exchanges can list your token without custom integration work, and decentralized applications can interact with your token using existing tooling. Deviating from the standard means building everything from scratch and asking every counterparty to build custom support for you.

That said, some of the most successful projects have extended or modified standards to meet their needs. The key is understanding the trade-off: straying from conventions creates friction with the ecosystem, but sometimes that friction is worth it for a genuinely better solution.

### Why "Request for Comment"?

The name pays homage to the internet's RFC (Request for Comments) process, which has governed how internet protocols evolve since the 1960s. Just as the IETF uses RFCs to collaboratively develop internet standards, Ethereum uses ERCs to develop blockchain standards through public input.

The "Request for Comment" naming signals Ethereum's ambition to build a robust, standards-driven ecosystem. It's a nod to the successful model that's allowed the internet to evolve collaboratively, and a reminder that these standards emerge from community discussion rather than top-down mandates.

### ERC Process vs Other EIPs

ERCs follow the same basic process as other EIPs, but they face a particular challenge: ecosystem adoption. A core EIP becomes part of the protocol once it's implemented by client teams and activated through a network upgrade. An ERC becomes meaningful only when wallets, exchanges, and applications choose to implement it.

This creates a longer road to impact for ERCs. Your proposal might reach Final status, but if no one implements it, it hasn't actually achieved anything. The most successful ERCs are those that solve real problems in ways that benefit the broader ecosystem, making adoption the natural outcome.

### Why Do Wallets Support Some ERCs But Not Others?

If you've ever wondered why MetaMask supports ERC-20 tokens but maybe not that newer standard you read about, you're encountering a practical reality of the Ethereum ecosystem: wallet support isn't automatic or universal.

Wallets like MetaMask, Rainbow, Coinbase Wallet, and others make deliberate decisions about which ERCs to support based on several factors. User demand drives a lot of this—wallets prioritize standards that users actually want to interact with. When ERC-20 became the de facto standard for tokens, wallets had to support it or frustrate users who wanted to manage their holdings. Similarly, when NFTs exploded in popularity through ERC-721, wallet support followed quickly.

Development resources matter too. Adding support for a new ERC requires engineering time, testing, and ongoing maintenance. Wallet teams have to weigh whether the adoption of a new standard justifies the investment. Sometimes a standard is technically excellent but has too small a user base to warrant immediate support. Other times, wallets wait to see if a standard gains traction before committing resources.

Security considerations also play a role. Each new standard brings potential attack vectors, and wallet teams need to be confident that a standard is well-audited and stable before exposing users to it. This explains why some promising ERCs don't see wallet adoption right away—the wallets are waiting for more real-world usage and security validation.

Finally, there's the practical reality that supporting every ERC that reaches Final status would be overwhelming. The standard track is productive, with hundreds of finalized ERCs covering everything from token standards to metadata formats to interface patterns. Wallets necessarily curate which ones they support based on user needs, security posture, and development capacity.

### Other Important ERCs Beyond the Big Three

While ERC-20, ERC-721, and ERC-1155 dominate the conversation, the Ethereum ecosystem has produced many other valuable standards worth knowing about.

**ERC-4626** has become increasingly important as yield farming and staking have grown. It's a standard for tokenized vaults—smart contracts that pool assets and implement a specific investment strategy. If you've interacted with any DeFi protocol that lets you deposit tokens and receive a receipt token representing your share, you've likely encountered an ERC-4626 implementation. The standard creates consistency across different yield strategies, making it easier for users to understand and compare opportunities.

**ERC-4337** represents a major leap forward in account abstraction. Rather than requiring users to manage private keys directly for every transaction, ERC-4337 enables smart contract wallets that can implement arbitrary logic—recovery mechanisms, multi-signature requirements, spending limits, and more. This standard is gradually making crypto more accessible by enabling user experiences that were previously impossible with traditional externally-owned accounts.

**ERC-777** aimed to improve on ERC-20 with better backwards compatibility and additional features like hooks that let contracts react to token transfers. While it didn't achieve the widespread adoption of ERC-20, it influenced later standards and is used by some projects that needed its specific capabilities.

**ERC-721** also has extensions worth knowing about. ERC-721 Metadata lets NFTs contain URLs pointing to JSON data describing the asset. ERC-721 Enumerable provides efficient ways to list all tokens owned by an address. These extensions became so common that many implementations include them by default.

The pattern you'll notice is that the most successful ERCs solve genuine problems developers face. The ecosystem gravitates toward standards that make building easier, not just technically elegant ones.

### The Most Important ERC Standards

When people ask about the "most important" ERCs, they're usually looking for the standards that every Ethereum developer should know, regardless of what they're building.

**ERC-20** remains the foundation for everything related to tokens on Ethereum. Even projects that create custom token standards typically implement ERC-20 compatibility for interoperability. Understanding ERC-20 is essential for any Ethereum developer.

**ERC-721** has become equally fundamental for any application involving unique digital assets. Whether you're building a marketplace, a game, or a collectibles platform, ERC-721 is likely relevant to your work.

**ERC-165** doesn't get headlines, but it's critically important for interoperability. It provides a standard way for contracts to advertise which interfaces they support, enabling other contracts to query and discover capabilities at runtime.

**ERC-721 Metadata** and **ERC-1155 Metadata** are essential for any application that needs to display token information to users—the images, names, and descriptions that make NFTs meaningful.

**ERC-2612** adds permit functionality to ERC-20, enabling gasless token approvals through a signed message. This has become important for user experience in DeFi applications.

The takeaway is that while dozens of ERCs have reached Final status, a handful form the foundation that most Ethereum development builds upon. Focus on understanding these core standards first, then explore others as your work requires.

---

## 7. History and Evolution

Understanding where EIPs came from helps explain why the process works the way it does today. This section traces the history of the EIP ecosystem from its origins to the present day.

### The Origins of EIPs

The EIP process was inspired by Bitcoin's BIP (Bitcoin Improvement Proposal) system, which had proven effective at organizing open-source protocol development. When Ethereum was being designed in 2014-2015, the founders recognized that a similarly structured process would be essential for managing a complex, constantly evolving blockchain platform. The formal EIP process was established early in Ethereum's history, with EIP-1 (the foundational document describing the EIP process itself) being one of the earliest proposals.

Vitalik Buterin played a central role in establishing the EIP process, drawing on his experience with Bitcoin and his understanding of how open-source protocols should evolve. The Ethereum Foundation provided institutional support, but from the beginning, the process was designed to be open and permissionless—anyone could submit an improvement proposal regardless of their affiliation.

The GitHub repository for EIPs was created to serve as the authoritative source for all proposals, with a clear workflow for submission, review, and publication. This approach borrowed from the successful model used by many open-source projects while adapting it for Ethereum's specific needs. The early community quickly embraced this process, using EIPs to hash out fundamental questions about how Ethereum should work.

### The First EIP Ever Created

Every journey begins somewhere, and for Ethereum's improvement proposal system, that beginning was remarkably foundational. EIP-1, titled "EIP Purpose and Guidelines," was the very first Ethereum Improvement Proposal. It established the rules of the road—the template that every subsequent EIP would follow, the status definitions that would govern how proposals progress, and the editorial process that ensures quality and consistency.

What makes EIP-1 particularly special is that it was created before Ethereum itself launched. The proposal was drafted during the early days of Ethereum's development, when the platform existed mostly as a whitepaper and a growing community of excited researchers. Creating a process for improvement before the thing itself was even live was a remarkably forward-thinking move. It signaled that Ethereum was being built not just as technology but as an open, governed system that would evolve through community participation.

The first few EIPs beyond EIP-1 addressed fundamental questions that would define Ethereum's architecture. These early proposals tackled topics like the Ethereum virtual machine specification, the structure of transactions, and the basic token mechanics that would eventually become ERC-20. Looking back at these foundational documents, you can see the early community working through the essential building blocks that would make Ethereum into what it became.

### How EIP-1 Has Evolved Over Time

Just as Ethereum itself has evolved, so too has the document that governs how Ethereum improves. EIP-1 has undergone several significant revisions since it was first created, each refinement learning from the community's experience with the process.

The earliest versions of EIP-1 were relatively simple—a basic template and a few guidelines. As the community gained experience with more proposals, the need for clearer structure became apparent. Different types of EIPs needed different treatment: core protocol changes required different review processes than standards that applications would implement. The categories we know today—Core, Standards Track (ERC), Networking, Interface, Meta, and Informational—emerged from this learning process.

The status workflow also matured considerably. Early on, the path from idea to implementation was less clearly defined. Over time, the community refined the stages: Draft for work in progress, Review for proposals seeking feedback, Last Call for final review, and Final for accepted standards. Each status change came with specific criteria that the community agreed would ensure quality without creating unnecessary barriers.

Perhaps the most significant evolution was in the rationale behind EIP-1. The original document focused heavily on format and process. Later revisions incorporated more guidance on how to write effective proposals, how to build consensus, and how to navigate the sometimes-challenging social dynamics of open-source governance. The document grew from a simple template into a handbook for effective participation.

### The Original EIP Editors

The EIP editorial team has evolved significantly since the process began, with dedicated volunteers shaping how proposals are reviewed and refined. The original editors were drawn from Ethereum's earliest contributors—people who had been there since the beginning and understood both the technology and the community dynamics.

These founding editors established many of the norms that persist today: the expectation that proposals be technically sound, the requirement that motivation be clearly articulated, and the insistence on backwards compatibility considerations. They set the bar for what constituted a well-written EIP, creating standards that continue to guide submitters.

The editor role has always been demanding. Editors aren't making value judgments about whether an EIP should be implemented—they're ensuring that proposals meet basic quality standards and follow the established format. But this gatekeeping function requires deep knowledge of both the technical landscape and the community's expectations.

Over time, the editorial team has expanded to include new contributors who bring fresh perspectives while honoring the traditions established by the originals. This evolution reflects Ethereum's broader growth: what started as a small group of founders has become a diverse ecosystem, and the editorial team mirrors that expansion.

### Notable Failed and Abandoned EIPs

Not every EIP reaches the finish line, and examining proposals that didn't make it offers valuable lessons. Some EIPs are formally withdrawn by their authors—perhaps they lost interest, found implementation too difficult, or decided another approach was better. Others are rejected, meaning the community decided against adoption.

What makes a proposal get abandoned? Sometimes it's simply loss of momentum. Championing an EIP requires sustained effort over months or years, and not every author can maintain that commitment.

Rejection tells a different story. Some EIPs are rejected because they propose changes that conflict with Ethereum's core values. Others fail because they introduce security risks that can't be adequately mitigated. And some are rejected because the community doesn't see the problem they're trying to solve as urgent enough.

The most interesting cases are proposals that were technically sound but arrived at the wrong time. An EIP that might have succeeded in an earlier era might face rejection as the ecosystem's priorities evolved.

### TheDAO Hard Fork and Its Impact on Governance

In 2016, TheDAO—a decentralized venture capital fund built on Ethereum—suffered a devastating hack that drained roughly 3.6 million Ether (worth around $50 million at the time). The response to this crisis would fundamentally reshape Ethereum's governance trajectory.

The community split over how to respond. Some believed the code was law and that the funds should remain where the hacker's contract sent them. Others argued that the hack exploited a vulnerability in the contract code itself—a bug, not intended behavior—and that the community should intervene to restore funds to their rightful owners.

The resulting hard fork split Ethereum into two chains: Ethereum (ETH) and Ethereum Classic (ETC). On Ethereum, the fork reversed the hack by returning funds to TheDAO's original holders. On Ethereum Classic, the chain continued with the original rules, maintaining the principle that code is law.

TheDAO crisis taught the Ethereum community invaluable lessons about governance. It demonstrated that the community would intervene in extraordinary circumstances, but that such interventions required broad consensus. It also showed that hard forks are deeply contentious—not just technically, but philosophically. These lessons shaped how the community approaches major protocol changes today, with much higher thresholds for contentious upgrades.

The incident also influenced how EIP governance developed. The community became more deliberate about distinguishing between changes that could achieve broad consensus and those that would fracture the community. This is why even years later, proposals that might introduce contentious forks receive especially thorough scrutiny.

### The EIP-155 Fork and Ethereum Classic

EIP-155 isn't just a number—it's a historical landmark that represents Ethereum's most significant fracture. When TheDAO hack occurred, the fork that created Ethereum Classic wasn't the original plan. The community initially hoped for a unilateral decision that everyone would accept.

EIP-155 specifically refers to the proposal that would have enabled a replay attack protection mechanism, but the number became forever associated with the fork debate. What emerged instead was a philosophical split: Ethereum Classic chose to maintain the unbroken ledger as a matter of principle, while Ethereum proceeded with the recovery fork.

The aftermath saw two functioning blockchains with deeply interconnected communities. Ethereum Classic continued developing its own roadmap, eventually moving to a proof-of-stake consensus mechanism (though on a different timeline than mainnet Ethereum). The split demonstrated that Ethereum's governance, while informal, could produce functional outcomes even in crisis mode.

The lesson for EIP governance was clear: the community will sometimes fork rather than reach consensus. This possibility hangs over every contentious proposal, creating pressure to find solutions that the entire community can accept. No one wants to be the proposal that breaks Ethereum.

### How ERC-20 Became the Token Standard

When ERC-20 was proposed in 2015, there was no guarantee it would become the dominant token standard. In fact, its adoption wasn't immediate or universally embraced.

The standard emerged from a practical need. Different token projects were creating incompatible contracts, making it difficult for wallets and exchanges to support multiple tokens without custom integration work. ERC-20 provided a common interface that solved this interoperability problem.

Was it controversial? Not particularly in the way we think of controversy today. There was discussion about whether the standard had the right functions, whether it should include certain extensions, and whether it was too minimal or too complex. But the community recognized the value of interoperability quickly, and adoption accelerated.

What made ERC-20 successful was timing and necessity. The 2017 ICO boom created massive demand for token standards—new projects launching token sales needed a way to get listed on exchanges and supported by wallets immediately. ERC-20 was ready to meet that demand. Its simplicity made it easy to implement, and its completeness meant it covered the essential use cases.

The standard's success also came from being "good enough" rather than perfect. It didn't try to solve every possible token use case—just the common ones. This restraint allowed for rapid adoption while leaving room for later standards like ERC-777 or ERC-4626 to address more specialized needs.

### The History of All Core Devs Calls

All Core Devs calls emerged organically from Ethereum's early development as a way to coordinate the multiple client teams building the protocol. In the beginning, these calls were informal—just a group of developers talking about what they were working on.

As the ecosystem grew, the calls became more structured. They became the primary venue where client teams coordinated implementation, where EIPs were discussed in detail, and where network upgrade timelines were set. Today, these weekly calls include representatives from Geth, Nethermind, Besu, Erigon, and other clients, along with researchers and Ethereum Foundation staff.

The calls are publicly accessible, with recordings posted to the Ethereum Foundation's YouTube channel and notes maintained in the Ethereum PM repository. This transparency is essential—anyone can observe how decisions are made, even if they can't participate directly.

For the EIP process, All Core Devs calls serve as a crucial coordination point. A finalized EIP won't go anywhere without client implementation, and the calls are where implementers signal their intentions and raise concerns. Champions who engage effectively with core developers tend to see their proposals progress faster.

### The History of Ethereum Magicians Forum

The Ethereum Magicians forum was created in 2017 to provide a better space for technical discussions than GitHub issues or Reddit could offer. The name came from the idea that the people working on Ethereum were like magicians—creating seemingly impossible things through technical skill and community coordination.

Before Magicians, discussions happened across multiple venues: the Ethereum subreddit, Gitter chat rooms, and GitHub issues. None of these platforms were ideal for the sustained, technical, threaded discussions that serious EIP proposals require. Reddit was too noisy, Gitter was too ephemeral, and GitHub issues mixed bug reports with high-level design discussions.

Magicians provided the structure that was missing. Categories for different EIP types, long-form posts that supported detailed technical discussion, and a community that valued thoughtful analysis over hot takes. The forum quickly became the place where proposals were refined before entering the formal EIP process.

Today, posting on Ethereum Magicians before submitting a formal EIP is essentially expected. The forum's archives contain years of discussion that have shaped how Ethereum evolves. Many proposals that seem straightforward on GitHub gained their complexity through the give-and-take of Magicians discussions.

### The Historical Context of EIP-1559

EIP-1559 didn't emerge from nowhere—it was the culmination of years of discussion about Ethereum's fee market.

Before 1559, users bidding for block space created a first-price auction every time they sent a transaction. This meant overpaying during quiet periods and uncertainty during busy ones. The system was simple but user-hostile. Research into better fee mechanisms had been ongoing for years, with various proposals circulating in academic and practitioner circles.

What made 1559 revolutionary wasn't just the mechanism—base fee that burns, tipping for priority—but the economic design that connected fee dynamics to Ether's value. Every transaction now destroys a small amount of Ether, creating a deflationary pressure that scales with network usage. This was audacious: it tied Ethereum's monetary policy directly to usage in a way that hadn't been done before.

The proposal was discussed for years before adoption. It went through multiple revisions based on community feedback, implementation challenges, and changing network conditions. The patience demonstrated in seeing 1559 through reflected a community willing to take the time to get such a fundamental change right.

When 1559 finally shipped in the London upgrade in August 2021, it immediately affected how users experienced Ethereum. Fees became more predictable, and the burning mechanism began removing Ether from circulation permanently. The success of 1559 demonstrated that the EIP process could deliver transformative changes when the community aligned behind a proposal.

### The Merge: Years of Evolution

The transition from proof-of-work to proof-of-stake—called The Merge—was one of the most anticipated events in Ethereum's history. It didn't happen overnight.

The original proof-of-stake vision was outlined in the Casper papers years before implementation. EIP-1011 (Casper PoS) was an early attempt that didn't reach completion. The design evolved significantly over time as research revealed new challenges and solutions.

What eventually became The Merge was delivered through EIP-3675, a meta-EIP that coordinated the transition. The timeline extended multiple times as implementation work revealed complexities. Each delay was accompanied by community discussion about the trade-offs between moving faster and being thorough.

The Merge demonstrated something important about Ethereum's governance: the community would wait for a properly tested implementation rather than rush to meet ambitious deadlines. The proof-of-stake transition affected every part of the protocol, and getting it wrong would have been catastrophic. The years of patience reflected a community that understood the stakes.

When The Merge finally occurred in September 2022, it reduced Ethereum's energy consumption by over 99% and began a new chapter in the protocol's evolution. The years of discussion, implementation, and testing that went into the transition became a model for how major upgrades should be handled.

Finally, we explore the relationship between the Ethereum Foundation and the EIP process, and how editor rosters have changed over time. We also examine which companies and institutions have been most influential in shaping proposals, and the unwritten dynamics of who actually drives Ethereum's technical direction.

### How EIP Editors Have Changed Over Time

The editorial team overseeing EIPs has evolved considerably since the process began, reflecting Ethereum's growth from a small research project to a global blockchain platform. Understanding this evolution gives insight into how the community has maintained quality control while scaling the process.

In the earliest days, EIP editors were essentially whoever Vitalik and the founding team trusted to maintain quality. There was no formal rotation or defined criteria—editors were community members who'd demonstrated commitment to Ethereum's technical health and had the respect of early participants. This small group handled everything from reviewing the first token standards to establishing the conventions that still guide submissions today.

As Ethereum grew, so did the editorial burden. What started as a handful of proposals per month became dozens, then hundreds. The community recognized that expanding the editorial team was essential to prevent bottlenecks. New editors were added based on their contributions to the EIP process itself—people who'd written well-received proposals, provided thoughtful reviews, or contributed to the EIP improvement proposals (EIPIP) that refine the process.

The editor roster has included people from diverse backgrounds: core developers from various client teams, researchers from the Ethereum Foundation and academic institutions, and active community members who've earned trust through sustained participation. Some editors have served for years, providing continuity; others stepped away after periods of significant contribution. This turnover is healthy—it brings fresh perspectives while the core traditions persist.

Perhaps the most significant change has been the formalization of the role. While editors remain volunteers (they're not employed by any organization), the community has developed clearer expectations for what the role entails: consistent application of EIP-1 rules, helpful feedback for submitters, and patience with proposals that need revision. The editors who thrive are those who treat the role as service to the ecosystem rather than gatekeeping authority.

What hasn't changed is the fundamental nature of the role: editors ensure proposals meet format requirements and basic quality standards, but they don't decide whether proposals are "good" or should be implemented. That judgment remains with the community. This separation of concerns—quality control versus merit evaluation—has remained constant even as individual editors have come and gone.

### Companies and Institutions Most Influential in EIPs

The EIP process is permissionless in theory—anyone can submit a proposal—but in practice, certain organizations have disproportionate influence over Ethereum's technical direction. Understanding who these players are explains a lot about which proposals succeed and which struggle.

The **Ethereum Foundation** remains the most influential institution, though its role has evolved. In the early days, the Foundation essentially bootstrapped the entire process, funding research, coordinating events, and employing many of the people who would become core developers. Today, while the Foundation still funds significant research, its influence comes more from convening power and legitimacy than from direct control. A proposal supported by the Foundation carries weight; a proposal opposed by the Foundation faces an uphill battle. But the Foundation learned from early controversies that it cannot mandate outcomes—the community will resist perceived top-down direction.

**Client teams** hold enormous practical power because they do the actual implementation work. Geth (the most widely used Ethereum client, developed by the Ethereum Foundation), Nethermind, Besu, Erigon, and others each have teams whose implementation decisions shape what actually runs on the network. These teams participate actively in EIP discussions, and their support (or lack thereof) often determines whether a proposal goes anywhere. When a proposal has all major clients committed to implementation, it moves forward; when clients are skeptical or too busy, the proposal stalls regardless of its technical merit.

**DeFi protocols and infrastructure companies** have become increasingly influential as the application layer has grown. Companies like Uniswap, Aave, MakerDAO, and OpenSea build products that depend on Ethereum standards, and their technical teams have become active in proposing and reviewing ERCs. When a major DeFi protocol champions a standard, wallet providers and exchanges pay attention because they know the standard will see real-world usage. This bottom-up influence has shifted some power away from core developers toward application builders.

**Wallet providers** like MetaMask, Rainbow, and Coinbase Wallet occupy a crucial position in the ecosystem because they're the interface through which most users interact with Ethereum. Their support (or refusal to support) can make or break an ERC. A token standard that wallets won't display isn't very useful. These companies increasingly participate in EIP discussions, advocating for standards that improve user experience or decline to support proposals they consider risky.

**Layer 2 projects** have become significant players as scaling solutions have matured. Teams building Optimism, Arbitrum, zkSync, and StarkWare participate in EIP discussions that affect their solutions, and they propose EIPs that help their technology work better with Ethereum. EIP-4844 (proto-danksharding) was heavily influenced by Layer 2 needs, demonstrating how this segment has gained voice in the process.

The honest picture is that Ethereum's governance involves many stakeholders, and no single entity controls the process. But influence is uneven—organizations with technical resources, real-world deployments, and sustained participation have more impact than individual contributors. This isn't necessarily problematic; these organizations have skin in the game and expertise to contribute. But it's worth recognizing that the "anyone can propose" ideal exists alongside practical realities of who has the capacity to drive proposals through.

### The Rollup-Centric Roadmap

In October 2020, Vitalik Buterin published a post titled "A Rollup-Centric Ethereum Roadmap" that fundamentally reshaped how the community thought about scaling. The vision shifted Ethereum's strategy from attempting to scale directly on the base layer to positioning Ethereum as a secure settlement layer while Layer 2 solutions handle the bulk of execution.

The reasoning was straightforward: scaling Ethereum's base layer directly was proving technically challenging and would take years. Meanwhile, rollups—Layer 2 solutions that execute transactions off-chain while posting compressed proof data to Ethereum—could deliver massive scalability gains immediately. The roadmap embraced this approach, with EIPs specifically designed to support rollup functionality.

This shift influenced several important EIPs. EIP-4844 introduced blob-carrying transactions, providing dedicated data space for Layer 2 proofs. Rather than storing rollup data as regular calldata (which gets stored forever), blobs provide ephemeral storage that significantly reduces costs.

The roadmap also meant Layer 2 projects became active participants in the EIP process. Teams building Optimism, Arbitrum, zkSync, and other rollups started contributing to discussions, proposing standards that help their solutions work better with Ethereum.

### Significant EIP Controversies

Not every EIP sails smoothly to adoption. Some proposals have sparked intense debate, revealing the fault lines within Ethereum's diverse community. Understanding these controversies helps illustrate how the governance process handles disagreement.

**EIP-999** remains one of the most contentious proposals in Ethereum's history. The proposal sought to restore wallet functionality for approximately 500 ETH (worth hundreds of thousands of dollars at the time) that had been locked in a multi-signature wallet when the Parity library was exploited. The technical details were complex, but the fundamental question was straightforward: should the community intervene to recover funds locked due to a smart contract bug, or maintain the principle that code is law? The proposal divided the community deeply, with some arguing that rescuing funds from a bug exploited the immutability that makes smart contracts trustworthy, while others felt the specific circumstances warranted an exception. After extensive debate, EIP-999 was never accepted, and the funds remain locked to this day—a permanent reminder of the trade-offs involved in blockchain governance.

**EIP-1559** generated significant controversy before its eventual adoption in the London upgrade. While the proposal eventually passed, the journey was rocky. Some miners opposed the change because it would reduce their transaction fee revenue by burning the base fee instead of awarding it to block producers. Others worried about the economic implications of permanently removing ETH from circulation. The debate was so intense that Ethereum Classic (the chain that split from Ethereum after TheDAO fork) cited EIP-1559 as evidence of Ethereum's willingness to make controversial changes, using it in their marketing as a reason to prefer the unchanged chain. Despite the opposition, EIP-1559 achieved broad consensus and has since been widely praised for improving user experience and creating deflationary pressure on ETH.

**EIP-3074** generated controversy in 2024 when its inclusion in the Pectra upgrade was delayed due to concerns about security implications and implementation readiness. The proposal would enable existing externally-owned accounts (EOAs) to delegate transaction execution to smart contracts, fundamentally improving user experience by enabling features like batched transactions and sponsor pays. However, some core developers raised concerns about whether the security model was sufficiently understood. The debate highlighted how the EIP process can slow down proposals that have strong community support when serious technical questions remain unresolved—a feature, not a bug, of Ethereum's careful approach to protocol changes.

These controversies demonstrate that the EIP process doesn't always produce quick decisions—sometimes it produces better decisions by forcing difficult conversations. The community has learned that proposals which face intense scrutiny often emerge stronger, while those that rush through without addressing concerns tend to cause problems later.

---

## 8. Notable EIPs and ERCs

Some EIPs transcend the technical process and become cultural landmarks. This section examines the proposals that have defined Ethereum.

### EIP-1559: The Fee Market Change

EIP-1559 stands as one of the most significant upgrades in Ethereum's history, fundamentally changing how transaction fees work on the network. Before this EIP, users manually set gas prices for their transactions, often overpaying during quiet periods and struggling to get included during busy times. The proposal introduced a base fee that automatically adjusts based on network demand, making fees more predictable and user-friendly.

What made EIP-1559 particularly notable was its economic design: the base fee is burned rather than paid to miners (or validators, post-Merge), meaning every transaction contributes to Ethereum's deflationary mechanics. This created a direct connection between network usage and the value of Ether itself, making the token more economically sustainable. The proposal had been discussed for years before adoption, showing how thoroughly the community wanted to vet such a fundamental change to Ethereum's economic model.

### The Merge: EIP-3675

The transition from proof-of-work to proof-of-stake—known as The Merge—represents Ethereum's most ambitious architectural change since launch. This wasn't a single EIP but a coordinated upgrade involving multiple proposals, with EIP-3675 serving as the meta-EIP that documented the entire transition process.

What made The Merge remarkable wasn't just the technical complexity of switching consensus mechanisms while maintaining network continuity. It was the years of research, multiple implementation attempts, and community patience that made it possible. Proposals like EIP-1011 (Casper PoS) laid the groundwork years earlier, and the final implementation incorporated lessons from those early efforts.

The Merge demonstrated that Ethereum could execute fundamental changes to its core architecture without fragmenting the community—a test that had proven fatal for other blockchain projects. The success owed much to the thorough EIP process, which allowed different stakeholders to voice concerns and ensured all client teams were aligned before activation.

### The Hall of Fame: ERC Standards That Power the Ecosystem

While Core EIPs change how Ethereum operates at the protocol level, ERC standards define how applications interact with the blockchain. Some ERCs have become so fundamental to the ecosystem that they're impossible to ignore.

**ERC-20** is the token standard that enabled the ICO explosion of 2017 and the entire DeFi ecosystem that followed. It defines a simple interface for fungible tokens—allowing any smart contract to implement basic functions like transfer, balance checking, and approval. What makes ERC-20 remarkable isn't just its technical elegance but its timing: it arrived when the ecosystem needed a common language for tokens, and it delivered. Early debates about the standard seem almost quaint now given how universally it's adopted.

**ERC-721** brought non-fungible tokens (NFTs) to Ethereum, defining a standard for unique, indivisible assets. While initially popular for digital art and collectibles, the standard has proven fundamental for gaming, identity systems, and real-world asset tokenization. The ERC-721 standard emerged from the CryptoKitties phenomenon—sometimes the best standards arise from solving real problems rather than theoretical design.

**ERC-1155** offered a middle ground, allowing both fungible and non-fungible tokens within a single smart contract. This efficiency gain matters for gaming and applications that need to manage large numbers of different asset types. The standard showed how the ecosystem learns: ERC-1155 addressed limitations that became apparent after years of ERC-20 and ERC-721 usage.

Beyond these famous standards, other ERCs have shaped specific domains. **ERC-4626** became the vault token standard that DeFi applications now rely on for yield optimization. **ERC-4337** introduced account abstraction, allowing smart contracts to function as accounts without changing the protocol itself—a capability that promises to dramatically improve user experience. **ERC-6551** extended ERC-721 tokens with associated wallet addresses, enabling a new paradigm of token-bound accounts.

What distinguishes a Hall of Fame ERC from a forgotten standard? The best ones solve genuine problems that many developers face, define clear and implementable interfaces, and gain adoption from wallet providers and infrastructure. ERC-20 succeeded because it arrived when tokenization was becoming important and because early exchanges and wallets committed to supporting it. Standards that try to predict future needs often fail; standards that respond to immediate pain points tend to thrive.

### What Makes an EIP Successful?

Looking across the notable EIPs and ERCs, certain patterns emerge. Successful proposals tend to solve problems that developers actually face, not theoretical improvements that would be nice to have. They arrive at the right moment—when the ecosystem is ready and the problem is well-understood. They have dedicated champions who maintain momentum through the inevitable delays and debates. And they build on previous work rather than reinventing the wheel.

The most influential EIPs often have another characteristic: they create new possibilities rather than just fixing existing ones. ERC-20 didn't just improve token handling—it made the entire tokenized economy possible. EIP-1559 didn't just change fee mechanics—it created the conditions for sustainable economic design. When your proposal enables things that weren't possible before, the ecosystem takes notice.

This section covers EIP-1559 (the fee market change that was one of the most significant upgrades in Ethereum's history), The Merge (EIP-3675), and the "Hall of Fame" ERCs that developers use every day. This section serves as case studies in what makes an EIP successful and influential.

---

## 9. Resources and Tools

Working with EIPs is easier when you know where to look and what tools exist. This section provides the essential links that every EIP practitioner should have bookmarked.

### Official EIPs Viewing & Listing

- **Main EIPs homepage** (overview, categories, statuses, search):  
  https://eips.ethereum.org/  
- **All EIPs list** (complete searchable table of every EIP/ERC):  
  https://eips.ethereum.org/all  
- **By category** (direct links):  
  • Core: https://eips.ethereum.org/core  
  • ERC (standards): https://eips.ethereum.org/erc  
  • Interface: https://eips.ethereum.org/interface  
  • Networking: https://eips.ethereum.org/networking  
  • Meta: https://eips.ethereum.org/meta  
  • Informational: https://eips.ethereum.org/informational  

### EIP-1 & Process Documents

- **EIP-1** (the official EIP process & template rules – "the bible"):  
  https://eips.ethereum.org/EIPS/eip-1  
- **EIP template** (Markdown file to copy for new proposals):  
  https://github.com/ethereum/EIPs/blob/master/eip-template.md  

### GitHub Repository (source of truth)

- **Official EIPs repo** (all raw files, PRs, issues, history):  
  https://github.com/ethereum/EIPs  
- **CONTRIBUTING.md** (exact submission workflow):  
  https://github.com/ethereum/EIPs/blob/master/CONTRIBUTING.md  
- **Repository structure & assets**: folders like `/EIPS/`, `/erc/`, `/assets/`, etc.

### Discussion & Governance

- **Ethereum Magicians** (main forum for EIP discussions – required before most submissions):  
  https://ethereum-magicians.org/  
- **Ethereum PM repo** (network upgrades, All Core Devs calls, hard-fork bundling):  
  https://github.com/ethereum/pm/

### Additional Helpful Links

- **Ethereum Stack Exchange** (Q&A for EIP/ERC technical questions):  
  https://ethereum.stackexchange.com/  
- **Ethereum.org EIPs section** (developer docs overview):  
  https://ethereum.org/en/developers/docs/standards/  

---

## 10. Security and Legal Considerations

EIPs can involve significant technical and legal implications. This section addresses the practical concerns around security audits, copyright, and intellectual property.

### How Security Audits Fit Into the EIP Process

Security audits occupy an interesting position in the EIP ecosystem. Unlike some blockchain projects that require formal security reviews before implementation, Ethereum's process doesn't mandate audits as a prerequisite for acceptance. This reflects the community's philosophy: the process should be open and accessible, not burdened by gatekeeping requirements that could slow innovation.

That said, the practical reality is different. Core EIPs that affect network security almost always undergo extensive security review—not because the process requires it, but because the stakes are too high to do otherwise. Client implementers have their own security teams that examine proposals. Independent security researchers contribute findings through the Ethereum Foundation's bug bounty programs. And for major upgrades like The Merge, dedicated audit firms were engaged to verify implementations across all client teams.

For ERC standards, the security landscape is more nuanced. An ERC that defines a token interface doesn't automatically require audit—it's just a specification that developers implement. But when that specification involves complex logic (as with ERC-4626 vault tokens or ERC-4337 account abstraction), audits become important because bugs in the standard could affect many implementations.

The EIP process does include security considerations as part of the specification requirements. Authors are expected to address potential vulnerabilities in their proposal, consider backward compatibility implications, and document any known security tradeoffs. The "Security Considerations" section isn't mandatory for all EIPs, but for any proposal touching sensitive areas, it becomes essential reading.

What you won't find in the EIP process is a centralized security review body. Instead, security emerges from the distributed efforts of implementers, researchers, and the broader community. This works remarkably well for established proposals but can leave experimental standards more exposed—which is why the ecosystem has developed informal norms around what warrants extra scrutiny.

### Understanding EIP Copyright

Every EIP submitted to the repository includes a specific copyright statement in its preamble. The default license used by Ethereum EIPs is the Creative Commons Zero 1.0 Universal (CC0 1.0) Public Domain Dedication. This means the proposal belongs to the public—anyone can use, modify, or build upon it without asking permission or paying royalties.

This licensing choice wasn't accidental. Ethereum's philosophy of open, permissionless innovation extends to its standards process. By releasing EIPs into the public domain, the community ensures that no single entity can control how Ethereum evolves. Anyone can implement an EIP, fork an implementation, or build a business on top of a standard without worrying about licensing negotiations.

The CC0 license applies to the EIP document itself—the formal specification. This is distinct from implementations of that specification, which can use different licenses. When client teams implement EIPs, their code remains under their chosen licenses (typically GPL for open-source clients). When developers build applications following ERC standards, their code belongs to them. The EIP is just the blueprint; what you build with it is yours.

### Can You Patent EIP Logic?

This is a question that comes up regularly, and the answer involves both technical and philosophical considerations.

Technically, you could attempt to patent concepts described in an EIP. The EIP document itself is public information, but that doesn't automatically prevent someone from filing patent applications on the underlying ideas—which is a quirk of how patent law works in many jurisdictions. However, doing so would fly in the face of Ethereum's open-source ethos and would almost certainly attract significant community criticism.

The practical reality is that patents on EIP concepts would be difficult to enforce in the blockchain space. The community would likely work around them, and implementing in a different (but functionally equivalent) way often avoids infringement issues. More importantly, the Ethereum ecosystem has historically rejected proposals where authors attempted to reserve special rights or exclusive benefits for themselves.

EIP-1 itself doesn't address patents directly, but the community norm is clear: EIPs exist to benefit the ecosystem as a whole. Authors who try to extract personal profit from their proposals face significant pushback. The most successful EIP authors build reputation and recognition rather than trying to monetize their specifications.

This approach reflects Ethereum's broader philosophy: shared standards create shared value. When everyone can implement a standard freely, the ecosystem grows faster and benefits everyone—including the original authors, who gain from the network effects their work helps create.

---

## 11. Layer 2 and Interoperability

Ethereum's scaling ecosystem relies on EIPs that affect Layer 2 solutions and cross-chain communication. This section explores how proposals interact with Optimism, Arbitrum, zkSync, and other Layer 2 protocols, plus what exists for interoperability between different blockchain networks.

### How EIPs Affect Layer 2 Solutions

Layer 2 solutions have become central to Ethereum's scaling strategy, and the EIP process directly shapes what these solutions can do.

The most direct influence comes from EIPs that add new capabilities to the Ethereum Virtual Machine or modify how data is stored. EIP-4844 introduced blob-carrying transactions, providing dedicated space for Layer 2 proof data. Before this EIP, rollups had to store proof data as regular calldata—expensive and permanent. After EIP-4844, rollups can use blob space that's significantly cheaper and automatically purges after a period.

Changes to gas costs, opcodes, or precompiles can also impact how rollups operate. When Ethereum modifies its base layer, Layer 2 teams must participate in EIP discussions to understand what's coming and plan accordingly.

The relationship works both ways. Layer 2 projects increasingly contribute to the EIP process, proposing standards that help their solutions work better with Ethereum. ERC-4337 (account abstraction) was heavily influenced by the needs of Layer 2 wallets. The line between "Layer 2 feature" and "EIP" has blurred as scaling solutions become more integral to the ecosystem.

For developers building on Layer 2, understanding the EIP landscape matters. The capabilities available to you tomorrow may depend on EIPs being finalized today.

### How EIPs Relate to Cross-Chain Standards

Cross-chain communication represents one of the emerging frontiers for EIPs, though the landscape is still maturing. As users want to move assets and data between Ethereum and other blockchains, the standards governing these interactions become increasingly important.

Several EIPs address cross-chain functionality directly. EIP-2930 introduced optional access lists that specify which addresses and storage slots a transaction will access—information that becomes crucial when Ethereum needs to validate state proofs from other chains. As cross-chain bridges become more sophisticated, this capability allows Ethereum to efficiently verify that events occurred on other networks.

The broader ecosystem has also developed standards outside the formal EIP process that serve similar purposes. CAIPs (Chain Agnostic Improvement Proposals) provide a naming convention for referring to different blockchains and their assets, making it easier to build applications that work across multiple chains. While CAIPs aren't part of the Ethereum EIP repository, they emerged from the same impulse—creating shared standards that enable interoperability.

The honest reality is that cross-chain standards are less mature than Ethereum's core standards. The space is more fragmented, with multiple competing approaches to bridging, asset transfer, and message passing. EIPs in this area tend to focus on foundational capabilities (like the access lists mentioned above) rather than specific bridge implementations. The community seems to be letting the space experiment first, with formal standardization likely to emerge once successful approaches prove themselves.

---

## 12. Relationship to Other Standards

EIPs don't exist in isolation—they interact with other standards and processes within the Ethereum ecosystem and beyond.

We compare Ethereum EIPs to Bitcoin BIPs, explain how proposals relate to network upgrades, and explore how EIPs interact with other Ethereum ecosystem standards outside the formal EIP process.

### How Ethereum EIPs Compare to Bitcoin BIPs

Ethereum's EIP system was explicitly inspired by Bitcoin's BIP (Bitcoin Improvement Proposal) process, which itself borrowed from the IETF's RFC system. Understanding the similarities and differences helps contextualize where Ethereum's approach came from and where it diverged.

The fundamental similarity is philosophical: both systems aim to organize open-source blockchain development through formal proposals that can be discussed, refined, and eventually accepted or rejected by the community. Both use numbered proposals (BIP-1, BIP-2... and EIP-1, EIP-2...), both maintain public repositories, and both require some form of community consensus before changes are implemented.

The structural differences reveal Ethereum's different priorities. Bitcoin's BIPs are categorized into three main types: Standards Track (describing changes that affect most or all Bitcoin implementations), Informational (design guidelines or general information), and Process (describing a process or changes to a process). Ethereum's categories are more granular, distinguishing between Core changes, Standards Track (ERC) proposals, Networking, Interface, Meta, and Informational categories. This reflects Ethereum's more complex technical landscape—a smart contract platform needs more categories than a pure cryptocurrency.

Perhaps the most significant difference lies in the role of standards. Bitcoin's primary standard is the blockchain itself and its transaction format; most BIPs deal with relatively focused changes. Ethereum's ERC standards have become a defining feature of the ecosystem, enabling the tokenized economy and DeFi applications. The ERC track has proven extraordinarily productive, with hundreds of standards addressing everything from token interfaces to metadata to novel use cases. Bitcoin doesn't really have an equivalent to ERC-20—its standards tend to focus on core protocol behavior rather than application-layer conventions.

The governance dynamics also differ. Bitcoin's development process is often described as more conservative, with changes to the base protocol receiving intense scrutiny given Bitcoin's role as a monetary asset. Ethereum's process has proven more willing to implement major upgrades (EIP-1559's economic changes, The Merge's consensus switch) while maintaining broad consensus. Neither approach is inherently better—they reflect different communities with different risk tolerances and priorities.

The two communities have influenced each other over the years. Ethereum's success with ERC standards prompted Bitcoin to consider similar application-layer standards (like BIP-70 for payment protocols, though it never achieved ERC-20-level adoption). Conversely, Ethereum's approach to EIP governance learned from Bitcoin's experiences with contentious forks and governance debates.

What unites both systems is the principle that open, permissionless participation leads to better outcomes. Anyone can propose a BIP or an EIP; the community evaluates proposals on their merits; and the best ideas rise through discussion and implementation. This shared philosophy has allowed both Bitcoin and Ethereum to evolve through coordinated community action rather than top-down mandates.

### How EIPs Interact With Other Ethereum Ecosystem Standards

The EIP process isn't the only way Ethereum develops standards—several other ecosystems and communities create specifications that interact with but exist outside the formal EIP framework. Understanding these relationships helps paint a complete picture of how Ethereum's technical standards evolve.

**CAIPs (Chain Agnostic Improvement Proposals)** represent the most prominent example of standards that emerged from the Ethereum ecosystem but weren't formally adopted as EIPs. Created by the same community that drives EIPs, CAIPs provide naming conventions for referring to different blockchains and their assets. This matters enormously for interoperability—when you're building an application that works across multiple chains, you need a consistent way to identify which blockchain and which asset you're talking about. CAIPs fill that role without being tied to Ethereum specifically.

The relationship between CAIPs and EIPs is complementary rather than competitive. CAIPs solve cross-chain problems that EIPs don't address (and arguably shouldn't, since Ethereum shouldn't dictate standards for other chains). Meanwhile, EIPs continue handling Ethereum-specific standards. The same people often participate in both processes, but the standards serve different purposes.

**Ethereum Improvement Proposals for Layer 2s** blur the line between EIPs and independent standards. Projects like Optimism, Arbitrum, and zkSync develop their own specifications for how their rollups work. Some of these eventually become EIPs when they affect Ethereum's base layer; others remain Layer 2-specific. The interaction is fluid: a standard might start as an independent spec, get proposed as an EIP for broader adoption, and either succeed in the EIP process or remain Layer 2-specific.

**Wallet standards and interface conventions** often develop outside the formal EIP process before being formalized. MetaMask and other wallets have their own conventions for how they interact with smart contracts. Some of these become EIPs when there's value in broader adoption; others remain proprietary or informal. The EIP process provides a path to standardization when the community decides coordination benefits everyone.

**DeFi protocol standards** represent another interesting case. When a DeFi protocol like Uniswap or Aave creates an innovative mechanism, other projects often want to adopt the same approach. Sometimes this leads to formal EIPs; other times, the "standard" spreads through imitation rather than formal standardization. The line between "informal standard" and "formal EIP" is porous—the community decides which approaches warrant the overhead of the full EIP process.

What emerges is an ecosystem where EIPs sit at the center but don't monopolize standardization. The EIP process provides a well-established path for proposals that need broad coordination, while other venues handle standards that are either Ethereum-agnostic or too specialized for the formal process. This flexibility serves the ecosystem well—not every standard needs the scrutiny and permanence that EIPs provide.

### How EIPs Relate to Network Upgrades

Network upgrades represent the mechanism through which EIPs actually reach the Ethereum mainnet. Understanding this relationship is crucial for anyone tracking when a proposal will affect the live network.

The connection between EIPs and network upgrades works like this: when an EIP reaches Final status (for Core EIPs), it means the specification has been accepted and is ready for implementation. But Final status doesn't automatically activate the change on mainnet. Instead, Final EIPs are bundled together into network upgrades—coordinated releases that activate multiple changes simultaneously.

This bundling approach serves several purposes. First, it reduces coordination burden—rather than activating changes one at a time, the ecosystem can prepare for and deploy multiple changes together. Second, it creates natural testing boundaries: when multiple EIPs activate in the same upgrade, they can be tested together for interactions. Third, it builds community momentum: upgrades like "London" or "Dencun" become memorable milestones that the entire ecosystem can celebrate and prepare for.

The network upgrade process involves careful coordination across all client teams. Each upgrade has a name (like "London," "Shanghai," or "Dencun") and a specific block height or time when it activates. Client teams implement the EIPs in the upgrade, test extensively, and then coordinate the timing of their releases. If even one significant client isn't ready, the upgrade typically gets delayed—chain splits would result if the network divided over incompatible rules.

Not all EIPs go into network upgrades. ERC standards (application-layer standards) typically don't require upgrades because they don't change protocol rules—they're conventions that applications follow. An ERC becomes "active" when wallets and dapps choose to implement it, not when a network upgrade occurs. Core EIPs affecting the virtual machine, consensus, or gas costs almost always require upgrades.

The relationship also works in reverse: network upgrades sometimes include changes that weren't proposed as formal EIPs. Technical adjustments, clarifications, or minor improvements might go directly into client code without the full EIP process. These tend to be non-controversial optimizations rather than substantive changes.

The key takeaway is that EIP status tells you whether a proposal is accepted as part of Ethereum's roadmap, but network upgrade timing tells you when it actually affects the live network. Tracking both—the formal EIP process and the upgrade schedule—gives you the complete picture of how Ethereum evolves.

---

## 13. Challenges, Criticisms, and the Future

Every process has its critics. This section honestly examines what's broken, what's difficult, and where the EIP process might be heading.

### How the EIP Process Prevents Spam

With a system that allows anyone to submit proposals, a natural concern is spam—low-quality submissions that waste reviewers' time and clutter the repository. Ethereum's EIP process has several mechanisms that naturally filter out most spam without requiring gatekeeping.

The first filter is the requirement for meaningful content. An EIP must follow the template, include all required sections, and address technical substance. Editors reject proposals that are obviously low-effort, poorly formatted, or clearly lacking technical merit. This basic quality control catches most attempts to flood the system with junk.

Beyond editorial filtering, the community provides a powerful disincentive. Submitting a poor-quality EIP damages your reputation in the Ethereum technical community. The ecosystem is relatively small, and people remember who submitted proposals that wasted everyone's time. Champions who are known for thoughtful contributions get their proposals reviewed promptly; those with a history of low-quality submissions face skepticism.

The status system itself acts as a filter. Stagnant proposals—those with no activity for six months—automatically receive that designation. This prevents the repository from filling up with abandoned ideas while preserving them for historical reference. If someone spams the repository with dozens of proposals and then abandons them, they'll simply become Stagnant and eventually fade from view.

For ERCs specifically, spam is less of a concern because adoption requires ecosystem support. A low-quality token standard might technically reach Final status, but if no wallets or exchanges implement it, it doesn't actually affect anyone. The practical barrier to impact is much higher than the formal barrier to submission.

That said, the process isn't perfect. Some genuinely spam-like proposals do enter the system and require editors to handle. And occasionally, proposals that seem like spam turn out to have merit—the line between creative new ideas and nonsense isn't always obvious. The community has generally found the right balance: open enough that good ideas aren't excluded, closed enough that the system doesn't get flooded.

### How the EIP Process Reflects Ethereum's Governance Philosophy

The EIP process embodies Ethereum's broader approach to governance: open participation, transparent deliberation, and consensus-building rather than command-and-control. Understanding the process reveals a lot about how Ethereum makes decisions.

The foundational principle is permissionlessness: anyone can submit an EIP regardless of their background or affiliation. This isn't just rhetoric—it's enforced by the process design. The editorial role is limited to quality control, not merit assessment. Whether your proposal gets implemented depends on community consensus, not whether you have connections or institutional backing. This reflects Ethereum's core belief that good ideas can come from anywhere.

Transparency is equally fundamental. All discussions happen in public forums. The GitHub repository, Ethereum Magicians, and All Core Devs calls are all accessible to anyone. There are no backroom deals or secret committees making decisions about Ethereum's future. This transparency serves a practical purpose—open source development works better when everyone can see what's happening—but it also reflects a philosophical commitment to decentralized governance.

The consensus-building process reflects Ethereum's belief that durable decisions require broad agreement. Proposals don't succeed through majority vote; they succeed when no significant stakeholder objects. This approach is slower than simple voting, but it produces decisions that more people can live with. The emphasis on building consensus rather than counting votes reflects a governance philosophy that values legitimacy over speed.

The tension between "code is law" and human governance shows up in the EIP process in interesting ways. Individual smart contracts are immutable and self-executing—but the protocol that runs those contracts changes through human deliberation. The EIP process is how Ethereum navigates this tension: proposals are public, discussed, and decided by humans, but once implemented, the code runs autonomously. This combination of mutable protocol and immutable execution has proven remarkably powerful.

Perhaps most importantly, the EIP process accepts that governance is ongoing, not resolved. There's no final constitution or permanent decision-making body. The process evolves through meta-EIPs and community norms. What works today might need revision tomorrow as the ecosystem grows and new challenges emerge. This experimental mindset—treating governance itself as something that can be improved through proposals—is itself a reflection of Ethereum's philosophical commitment to iterative progress.

### The Tension Between Code Is Law and EIP Governance

One of Ethereum's founding philosophies is "code is law"—the idea that smart contracts should execute exactly as written, without human intervention or override. This principle gives users confidence that the rules won't change unexpectedly, making the system trustworthy for valuable transactions.

But EIP governance sits in tension with this philosophy. When the community decides to upgrade Ethereum through an EIP, they're explicitly overriding what the previous code specified. The base fee burns ETH instead of paying miners. The Merge changed consensus entirely. These are fundamental changes to what "the code" does—and they happen through human deliberation, not autonomous execution.

This tension isn't a bug; it's a feature of how Ethereum operates. The community has decided that certain changes are important enough to warrant collective decision-making, even if that means departing from pure code-is-law principles. The EIP process provides a structured way to make these decisions: transparent proposals, public discussion, clear timelines, and broad stakeholder input.

What makes this work is that EIP governance applies to the protocol layer, not the application layer. If you deploy a smart contract, its code remains law for anyone interacting with it. The Ethereum protocol itself changes through EIPs, but individual contracts don't get modified retroactively. This distinction—protocol governance versus contract execution—preserves the core promise of code is law while allowing the protocol to evolve.

The tension manifests most visibly in contentious upgrades. When different groups have fundamentally different visions for Ethereum's future, the EIP process becomes the arena where those disagreements get resolved. Sometimes the resolution is elegant; sometimes it's messy. But having a process is better than the alternatives—either gridlock or fork.

### Balancing Innovation and Stability

Every blockchain protocol faces the challenge of evolving without breaking what's already built on top. Ethereum has users, applications, and businesses that depend on predictable behavior. At the same time, the ecosystem needs new capabilities and improvements to remain competitive and functional.

The EIP process handles this balance through several mechanisms. Backward compatibility is a core principle—whenever possible, new EIPs should maintain existing functionality. Breaking changes require especially strong justification and often face significant resistance. The process includes explicit "Backwards Compatibility" sections where authors must explain how their proposal affects existing systems.

The status system also helps by creating natural pause points. An EIP in Draft or Review can change significantly based on feedback. Once it reaches Final, the expectation is stability. This doesn't mean Final EIPs never change—some do get updated—but the bar is higher and the process more deliberate.

Living standards represent an interesting evolution in this balance. Standards like ERC-20 and ERC-721 reached Final status but continued evolving through supplementary EIPs that clarified edge cases or added capabilities. This approach allows standards to mature while preventing the instability of constantly changing the core specification.

What emerges is a pragmatic balance: the protocol moves forward steadily but carefully, with significant changes receiving extensive scrutiny. Minor improvements can happen relatively quickly; major changes take years of discussion. This pace frustrates some who want faster progress, but it protects users who build businesses on Ethereum.

### Finding Which EIPs Matter

With hundreds of EIPs in various stages, knowing which ones to pay attention to is a challenge. The honest answer: you don't need to track most of them—focus on what affects your work.

For application developers, ERC standards matter most. When a new token standard emerges or an existing one gets updated, pay attention.

For infrastructure providers and node operators, Core EIPs affecting network rules demand attention. When gas costs change or consensus mechanisms evolve, you need to be ready. These typically get discussed extensively before activation.

For researchers and protocol enthusiasts, the entire ecosystem is relevant. EIPs in early stages often change significantly—watching every Draft proposal wastes energy. The most important proposals tend to generate sustained discussion and appear on All Core Devs agendas.

Practical tools help: the official EIPs website shows current status and recent activity. The Ethereum Magicians forum highlights proposals seeking feedback. Twitter and Discord often surface proposals gaining traction before they reach formal milestones.

The simplest rule: if an EIP affects your work directly, track it. Otherwise, trust that the community will surface what's important.

### What Makes an EIP Champion Successful

Behind every successful EIP is someone who cared enough to push it through. The champion role isn't formal—it's earned through sustained effort and genuine contribution to the ecosystem.

Successful champions share certain characteristics. They have deep technical understanding of their proposal and can explain it to different audiences: researchers who care about correctness, developers who care about implementation, and the broader community who care about implications. They respond to feedback promptly and constructively, treating criticism as an opportunity to improve rather than an attack to deflect.

Persistence matters enormously. The EIP process moves slowly, and proposals often face years of discussion before reaching Final status. Champions who maintain momentum through these long timelines—who keep the conversation alive, who keep nudging implementers, who keep updating the specification based on new learnings—succeed more often than those with brilliant ideas but limited follow-through.

Building relationships is equally important. Champions who know the client teams, who participate in All Core Devs calls, who have credibility in the community: these people get their proposals attention. If you're unknown in the ecosystem, your proposal starts at a disadvantage—not because of unfairness, but because trust matters for something as consequential as changing Ethereum.

Finally, successful champions know when to compromise. The best proposal isn't necessarily the one that implements your original vision; it's the one that achieves broad adoption. Champions who insist on their specific approach often see their proposals stall while more flexible alternatives move forward. Knowing what matters fundamentally and what's negotiable distinguishes effective champions from those who can't let go.

### How Living Standards Evolve After Final Status

When an ERC reaches Final status, you'd think the story ends—the standard is set, implementations are complete, everyone moves on. But for many important standards, Final is just another milestone.

Living standards are ERCs that continue evolving even after reaching Final status. The community recognized that some standards need to adapt to new use cases, fix discovered issues, or add capabilities—all without breaking existing implementations.

ERC-20 is the canonical example. Finalized years ago, it remained static in its core specification but evolved through supplementary EIPs that clarified behavior, added metadata capabilities, and addressed edge cases. Implementations became more robust as the community learned from bugs and edge cases across different projects. The standard itself didn't change, but the collective understanding deepened.

ERC-721 followed a similar path. The non-fungible token standard gained extensions for metadata, enumeration, and URI handling—all as separate EIPs that built on the base specification without modifying it. This approach allows implementations to adopt new capabilities incrementally.

The key mechanism is backward compatibility. Extensions that add new functions don't break existing implementations that don't use them. Clients can choose which extensions to support based on their needs. And the core standard remains stable, preserving the "law" aspect of code is law for existing contracts.

This evolution requires discipline from the community. New extensions need broad support to become useful—there's no value in a standard that only one implementation follows. And major changes to the core specification should remain extremely rare, reserved for issues that truly can't be addressed through extension.

We address governance fatigue, how the process prevents spam, and the tension between innovation and stability that every protocol faces. The philosophical tension between "code is law" and human-mediated governance gets explored, along with practical questions like how to find which EIPs matter and what makes an EIP champion successful.

We also look at how living standards like ERC-20 and ERC-721 continue to evolve after reaching Final status, and what changes might come to the EIP process itself.

---

## 14. Meta EIPs

Some EIPs are about the process rather than the protocol. This section covers meta-EIPs and how they work.

### What Are Meta-EIPs?

Meta-EIPs are a unique category of proposals that describe processes or guidelines around Ethereum rather than changing the protocol itself. They serve as documentation for how the ecosystem coordinates complex, multi-phase initiatives that span multiple technical EIPs and involve many stakeholders.

The key distinction: a standard EIP proposes a technical change—a new opcode, a modified gas schedule. A meta-EIP proposes a coordination mechanism—a process for transitioning consensus mechanisms, a framework for large-scale upgrades.

Meta-EIPs matter because complex initiatives often span multiple technical EIPs and require alignment across teams. They become the reference document everyone involved agrees to follow.

### EIP-3675: The Merge as a Meta-EIP

The Merge (EIP-3675) represents the most significant meta-EIP in Ethereum's history, and examining it reveals why this category exists.

Transitioning from proof-of-work to proof-of-stake wasn't something that could be captured in a single technical specification. The effort involved years of research, multiple client implementations, coordination across all Ethereum teams, and careful sequencing of testnet and mainnet activations. It required specifying not just what changed but how the transition would work—when would proof-of-work stop, how would validators activate, what happens to pending transactions, how would the ecosystem communicate the change.

EIP-3675 served as the master document for all of this. It defined the technical conditions for the transition, the new constants and behaviors introduced by proof-of-stake, and the rationale for why the approach was sound. Crucially, it also served as a coordination point: everyone involved could look to this single document to understand how their work fit into the larger picture.

What made EIP-3675 particularly powerful was its role as a living reference. As implementation progressed and the community learned more, the meta-EIP evolved to reflect that understanding. It became the canonical source for "what we're doing and why"—reducing confusion and misalignment across teams.

### How Meta-EIPs Differ From Standard EIPs

**Scope**: Standard EIPs address specific, bounded changes. Meta-EIPs describe broader initiatives spanning multiple technical changes and team coordination.

**Status progression**: Both follow Draft → Review → Last Call → Final, but criteria differ. A standard EIP becomes Final when implemented across clients. A meta-EIP becomes Final when the initiative it describes is complete—when The Merge happened, EIP-3675 moved to Final.

**Implementation**: Standard EIPs are implemented in client code. Meta-EIPs are coordination documents—the implementation happens through the technical EIPs the meta-EIP references.

**Community attention**: Meta-EIPs attract broader attention because they represent major ecosystem events. Everyone wants to understand what's changing and when.

### When to Use a Meta-EIP

A meta-EIP makes sense when you're coordinating something involving multiple technical EIPs and requiring alignment across teams. The Merge was the obvious case—a transition affecting every aspect of Ethereum's operation.

A meta-EIP is less appropriate for focused changes, even significant ones. EIP-1559 was a major upgrade, but it didn't require the coordination framework meta-EIPs provide.

The guiding principle: if your initiative needs a coordination document to help diverse stakeholders understand how their work fits together, a meta-EIP provides that service. If your proposal can stand alone as a self-contained technical specification, use a standard EIP.

What makes meta-EIPs powerful is their ability to capture not just technical specifications but the reasoning and context surrounding major Ethereum initiatives. They become historical documents future developers can reference.