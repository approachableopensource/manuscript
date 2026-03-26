---
title: The Four Files of Any Open Source Project
label: Chapter 4
tocOrder: 6
disabled: false
description: We frame every open source project against four files. I won't keep you in suspense. I prioritize the README, LICENSE, CHANGELOG, and CODE_OF_CONDUCT files. We cover an array of conceptual and technical topics, and get real real when talking about licenses.
---

Chapter Four

## The Four Files of Any Open Source Project

No matter the size of an open source project, there are norms that newcomers and seasoned developers alike will expect to find within your repository. Think of the products you encounter outside of tech—food, clothing, or hardware. We expect a tray of Oreos to suggest a serving size (so we can ignore it). We read the labels on garments so we know what size to buy, and how to care for them. Installation instructions tell us what tools we need, how to get started, and what to do if things go wrong. (FIG 4.1)

![FIG 4.1: Ikea’s instructions provide requirements, warnings, and guidance without any written words.](/images/90b208e8-81ee-4996-b34a-c1cb65c3d25e.png)  
FIG 4.1: Ikea’s instructions provide requirements, warnings, and guidance without any written words.

Confusing or absent documentation harms consumer agency and safety. Many companies make product documentation accessible via multiple languages. It’s hard to know where to begin, so I’ve defined what is essential to a project of any size. Let’s start with four files that act as a foundation for you and potential users or contributors: a README, a LICENSE, a CHANGELOG, and a CODE\_OF\_CONDUCT.

## README

The README document is the window into your project. It must juggle multiple competing needs and values simultaneously in order to be effective. And no, we cannot add an auto-rotating carousel to the top. Consider that different personas will be scanning this document in search of information. A developer evaluating your project needs to know what it does and how. A current user may need to dive deep into an API method’s return statement. A first-time contributor might look here to find out how to contribute to the project. Programs might scan the file for metadata. Structuring your README with intention—maybe even designing it with the spectrum of engagement in mind—can have an outsized impact on your project goals.

### What Makes a Good README?

One of the first recorded instances of a README file was within the DEC PDP-10 user group documentation for electrical circuit simulation programs, SPICE, SINC, and SLIC.<sup>[133](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715406118718)</sup> What they exactly do is a bit beyond my skillset, but in 1974 the guidance contained such nuggets as “many severe bugs. With this distribution I will no longer make any attempt to distribute that compiler nor answer any questions on it.” It ends with “Good luck!” which is a decidedly homebrew vibe. To its credit, it contains requirements, constraints, and performance metrics.

Luck is when preparation meets opportunity. Here’s my go-to list of README contents.

#### Demo

A screenshot or animated GIF providing a glance at the functionality one can expect. Macs can create a nice screenshot with command \+ control \+ shift \+ 4, and then hitting space to capture the whole window. Code or terminal snippets can be made with a free tool like Carbon.<sup>[134](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715406679155)</sup> Many of the code snippets in this text were created using Carbon.

#### Installation

Instructions how to install the project. This can be a multipart or single command depending on your needs. npm-based projects should specify the version of Node.js and npm to use, as these can have impact on how dependencies install.

1. The engines field within package.json can define your runtime requirements. All modern package managers parse it. npm and pnpm will emit warnings during an install command if your installed version does not match requirements, whereas Yarn will outright fail.
    
2. Adding an .nvmrc file can signal to users what version of Node.js to run. Tools like nvm<sup>[135](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715408322689)</sup> can read this file and wire up the proper versions. GitHub Action setup-node<sup>[136](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715408294600)</sup> will read this file or the engines field, reducing the number of magic strings in your code.
    
3. If your project is a command-line tool that can be installed and invoked in a single action, add npx<sup>[137](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715408364063)</sup> instructions. This downloads the executable if not already present and then runs the command.
    
4. If your project is large or nuanced, let the user know when install is complete by providing a health check command, or guidance to determine everything is working as expected.
    

#### Usage

A user-facing tour of project functionality. Usage implies that the tool is already installed and ready to be run. What does success look like? How about failure?

1. **Invocation:** how do you run the software? Start with a “hello world” or default example.
    
2. **API:** document the public-facing contracts that comprise your API. Detail the input and outputs. Provide examples. A documentation-first development model will reveal what actions a user can take.
    
3. **Configuration:** how can default behavior be deviated from? Documenting available options can help a user fit your software to their use case. Can configuration be shared, inherited, or overridden? Are configuration options validated? Do you have defaults, types, and lists of options defined?
    

#### Contributing

Outline how you’d like people to help with the project. We’ll talk about tooling that can help here in a bit, so focus more on the process. GitHub, GitLab, and others also encourage a discrete CONTRIBUTING.md document, which gives you are bit more focused area to discuss topics such as:

1. Branching strategy and issue etiquette. Large projects may suggest you open an issue first to confirm the behavior, the plan, and claim your interest in fixing it.
    
2. Development setup beyond user-installation
    
3. How to run tests locally
    
4. How production releases are created and published
    

The Day.js project embodies many of these concepts within their README. “Above the fold” on their README are links to translations, browser support, the size of the library, and an example of their API. (FIG 4.2)<sup>[138](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715408501726)</sup> Links to their official website follow, but staying in the file shows installation and API references too. It’s a thoughtful presentation of a lot of content. With any project there are competing needs colliding, so pave the cowpaths<sup>[139](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715408536546)</sup> and don’t overwhelm. README documents should have clear, scannable headings to help navigate.

![FIG 4.2: The Day.js README represents a well-thought-out introduction to their project, directing traffic for various incoming personas. Perhaps the logo is too big (j/k).](/images/8dc3286e-f9dc-44d8-8f01-4af27ac5d2b6.png)  
FIG 4.2: The Day.js README represents a well-thought-out introduction to their project, directing traffic for various incoming personas. Perhaps the logo is too big (j/k).

If you are looking for inspiration, browse around. You’ll start to notice nuance among projects of different intents and sizes. Katherine Oelsner built an online markdown editor<sup>[140](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715408563474)</sup> to help create README files. The company divio publishes a documentation paradigm designed around four user-centered needs: tutorials, how-to guides, technical reference, and explanation.<sup>[141](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715408605449)</sup> Ask someone unfamiliar with your project to navigate your README for particular tasks. Fresh eyes will reveal opportunities.

### Hello? Do You README?

Set the tone you expect others to follow with your README. Be welcoming and inclusive to newcomers. This is the first impression of your project. Use it to shape your code and community for success. The alex<sup>[142](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715408726323)</sup> tool validates the use of language in your project and calls attention to potentially insensitive word-choice and phrasing. (FIG 4.3)

![FIG 4.3: alex flags potentially insensitive and inappropriate language. ](/images/2e04d715-55f3-4fa4-a838-043d8a0d63cf.png)  
FIG 4.3: alex flags potentially insensitive and inappropriate language.

Many maintainers of projects advertise metadata about a project via shields<sup>[143](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715408774277)</sup>—dynamic images that display data such as download counts, versions, build status, code coverage, and so much more. The Day.js project earlier used them. Shields give an otherwise vanilla-looking document some visual flair and color, but I caution their overuse. They are far too easy to grow into a bumper-sticker-laden mess.

More importantly, they are usually inaccessible to screen readers like Apple VoiceOver, Microsoft Narrator, and JAWS, as their content is generated on the server with no means to affect the image markup alt tag. So we are left with literal read-outs of data URLs (FIG 4.4)<sup>[144](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715408861405)</sup>:

![FIG 4.4: A screen recording of Apple’s VoiceOver reading inaccessible README badges. Autogenerated data URLs are read verbatim. “Unlabeled image, unlabeled image. Slash 68747470733f2f70...](/images/329882b6-44ca-47d8-be55-6a37531b0777.png)  
FIG 4.4: A screen recording of Apple’s VoiceOver reading inaccessible README badges. Autogenerated data URLs are read verbatim. “Unlabeled image, unlabeled image. Slash 68747470733f2f70...

I cannot believe I have to say this, but... beware vendor lock-in with your README. It’s outstanding that sites like GitHub render markdown-based READMEs for you and your users. They continue to enhance what you can put into your structured content. There’s even a name for it: *GitHub-Flavored Markdown.*<sup>[145](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715408937651)</sup> Whether they are improving the medium or repeating the risk of browser-specific features is up for interpretation, however.

Take a look at the mermaid diagraming project,<sup>[146](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715408965695)</sup> which GitHub announced site-wide README rendering integration in February 2022. (FIG 4.5)<sup>[147](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715408993153)</sup> Without extensions installed, popular editors fallback to the text content. This is fine as a graceful degradation, but visiting the same project over on npmjs.com<sup>[148](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715409035526)</sup> was broken for months. (FIG 4.6) Users encountering your project from that landing-page would be left with a broken or diminished experience you may not have accounted for.

![FIG 4.5: A README containing a mermaid diagram rendering on GitHub...](/images/26a9d9fc-5637-474e-87ae-c1a25e41f0db.png)  
FIG 4.5: A README containing a mermaid diagram rendering on GitHub...

![FIG 4.6: ...and a broken view of npmjs.com attempting to render the same content. In an error state, the site logic claimed there was no README at all.](/images/8206ba9b-bfce-49d5-8382-af6fd93ae4c8.png)  
FIG 4.6: ...and a broken view of npmjs.com attempting to render the same content. In an error state, the site logic claimed there was no README at all.

A cherry-picked example, now fixed, you say? This fits a pattern. The site also supports admonition rendering such as “Note” or “Warning” blockquotes.<sup>[149](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715409314880)</sup> Feedback brought up concerns of accessibility, English-only features on a site with international audiences, and further specification fragmentation. There was also a brief technical preview of GitHub Blocks<sup>[150](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715409354974)</sup> in 2022 and 2023, declaring that “READMEs don’t have to be static.” With intentions to further render live demos, project stats, search, sortable tables, charts, and more, GitHub was positioning the README as a real homepage. It demoed well, but would other sites be able to render this content, or would editors with markdown previewers? Perhaps they could have pulled it off as a progressive enhancement.

This all might not matter to you, and I respect the net-positive impact GitHub has, but be aware of the value exchange you are creating here—an enhanced experience in one location at the expense of others. Know that this is a convenience not a requirement. When playing in someone else’s sandbox, you may someday come to find it hard to move your sandcastle. Jenn Schiffer puts it nicely when she said in a now-protected social media post, “keep an eye out for gardens growing walls.”

### README vs. Website

With so much functionality begging to be added to a README, it’s not a surprise that some projects opt to make a standalone website instead. The sky is the limit in terms of what functionality you wish to build into it. Often these sites become projects in and of themselves to host, maintain, secure, design, upgrade, translate, etc.

Given the landscape, and the ever-present temptation to make a site and devote untold time toward it, I feel responsible to provide some smart defaults in the Resources section at the end of the book. The npm publish process will package up a README file by default, meaning it is distributed to your end users’ machines. The same cannot be said of a website, which requires at least one initial network connection (crossed fingers they make it an offline-friendly progressive web app). I’ve had productivity stall on a dodgy bus Wi-Fi connection, or roaming while on a phone. So don’t discount your offline, lo-tech options when documenting.

## LICENSE

Distributing a LICENSE file tells other folks what they can and cannot do with your project. The legal side of open source licensing can get complicated really fast. Most people don’t think about it until something goes wrong. Let’s first focus on the basics here, ease into the complexity, and leave you with resources to turn to when you need to dive deeper. I promise, it’s anything but dry.

Projects you put on the World Wide Web retain proprietary copyright until you say otherwise.<sup>[151](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715409678024)</sup> If you accept contributions in this precarious format, you and the contributor intertwine restrictive copyright and lock-each other out of the car with the keys inside. This may feel confusing as a default, given how easy it is to share code on social platforms these days (GitHub’s terms of service don’t grant a license to code you host there, only that others can read it).<sup>[152](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1719022066157)</sup> It is best to be clearer in your intent at the outset.

The excellent resource choosealicense.com offers comprehensive education on open source licensing, with an interactive guide to suggest a license based on your values and project goals. (FIG 4.7) I like the user-centric viewpoint choosealicense takes here. The site suggests popular licenses based on the value exchanges important to a project. It also maps existing open source projects to these licenses so you can draw your own conclusions about which communities choose what license. I myself have gotten confused with terms like “permissive” “restrictive,” or “copyleft,” so let’s discuss.

![FIG 4.7: The choosealicense.com homepage provides user-centric guidance on which license is right for your project.](/images/48897f23-28db-40ba-bb03-144368a8f9b3.png)  
FIG 4.7: The choosealicense.com homepage provides user-centric guidance on which license is right for your project.

### Permissive vs. Restrictive Licensing

Licensing can be described across different dimensions, one of which is permissive vs. restrictive. Sometimes this can feel ill-defined or counterintuitive, depending on what perspective or concern you prioritize. *Does permissive mean people can use it for free? Does it mean companies can sell work based on it? Or is that restrictive?* We can make this clearer. On the permissive end we have the perception of public domain (which is not legally recognized everywhere). Permissive work is free to be remixed, re-sold, and incorporated into other work. On the restrictive end you have individual, exclusive copyright by default. Everything you make is yours until you say otherwise. The fun comes in the middle, where most licenses land.

Licenses:

* **Grant permissions:** what you *can* do with the software. Think “may statements” like, “you may sell derivative works.”
    
* **Define conditions:** what you *need* to do with the software. Think “must statements” like, “you must disclose the source code.”
    
* **Set limitations:** what you *cannot* do with the software. Think “cannot sue” sentiments. This is almost always in the form of an “AS IS” limitation of liability to project authors.
    

Using these statements as a rubric, we can compare the MIT and GPL license, both prominently displayed within choosealicense. (FIG 4.8)

![FIG 4.8: A comparison of the major differences between the MIT and GPL licenses. ](/images/f22cbb25-016d-4664-bc7c-97a241f8c0be.png)  
FIG 4.8: A comparison of the major differences between the MIT and GPL licenses.

With the MIT License, downstream users can do nearly anything with the code, even close the source and sell it commercially. Conversely, adopting the GPL as any part of your dependency tree is like adding !important to a CSS rule—it overrides the cascade and forces all downstream works to adhere to the GPL. This principle is sometimes referred to as *copyleft*<sup>[153](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715456887456)</sup> (the antithesis of *copyright*). Such-licensed software can still be used for commercial works, but the code must be available and extensible without cost. You can start to see why GPL-centric companies tend to offer services adjacent to the code like consulting and hosting as part of their business model.

Website content or project documentation may fall under the same license as the code, but if you want your technical writing, blog posts, or announcements to have broader reach consider something like Creative Commons licensing.<sup>[154](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715456936004)</sup> Their license terms and considerations are better suited for non-software works. Vice versa, code isn’t meant to be released under Creative Commons licensing, as they don’t offer the same permissions, conditions, and limitations that software requires, especially pertaining to distribution and patents.<sup>[155](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715456969916)</sup>

*Phew.* I hope that helped! But what if the current license is no longer meeting the needs of maintainers, the community, or defining the right value exchange? Can it be changed? The technical answer is “yes,” but let’s explore.

### Changing a License

I’ve focused on license differences between MIT and GPL as a reductive primer on the subject, but there are many more licenses. There are so many licenses that we teeter toward duplicity, fragmentation, and unenforceability.<sup>[156](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715457012062)</sup> Changing a license seems plausible, given the number out there. But once a project is open sourced under one license, it becomes harder and harder to change the license it is released under. Changing from MIT to GPL, for instance, would require the approval of every existing contributor. In general, each contributor to your project is granting their lines of code as a continuance of the current license. You might see this referred to as inbound=outbound. Some large projects try to avoid this consent problem by setting up Contributor License Agreements, or CLAs.<sup>[157](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715457064245)</sup> A CLA signed by contributors can make future license reassignment easier, among other things. Still following? These are not theoretical concerns. It can get ugly.

In 2018, the monorepo management tool Lerna<sup>[158](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715457091401)</sup> switched from the MIT license to an exclusionary, custom variant<sup>[159](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715457111703)</sup> that singled out companies allegedly doing business with United States Immigration and Customs Enforcement, or ICE. This move was in protest to the separation of adult and minor migrants at the US border<sup>[160](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715457136038)</sup> begun under the Trump administration and continuing into the Biden administration.<sup>[161](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715457209748)</sup>

Within hours of the change, users pointed out within the issue log that Lerna was no longer MIT License-compliant and should not describe itself that way.<sup>[162](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715457235290)</sup> Others pointed out that the license change could not be made unilaterally, even by maintainers, without explicit consent from all contributors. There was no CLA on file.<sup>[163](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715457258141)</sup> One contributor publicly requested that their prior contributions be removed from the code.<sup>[164](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715457280710)</sup> Amidst the chaos, the original pull request author limited all new issue creation within GitHub to maintainers.<sup>[165](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715457306592)</sup> They locked, closed, and shutdown attempts to criticize or clarify the licensing decision.<sup>[166](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715457323659)</sup> Discourse on GitHub, across multiple repositories, and on social media was heated, meandering, and devolved to personal attacks.

The Lerna maintainers and community were not ready to manage the mechanics, discussion, and impact of the licensing change. The move attracted a lot of attention from individuals outside the project on different sides of the political fault lines of open source software. Instigators pushing their own narratives muddied many earnest attempts at discussion. You can find hundreds of comments within contemporaneous issues that I won’t include here. Calls intensified to revert the license change and remove the original author of the pull request, citing harassment as a code of conduct violation.<sup>[167](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715457366685)</sup> Other maintainers did just that: revert the license *and* remove the author of the new license as a combined act.<sup>[168](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715457412379)</sup> This linking of the legal merits alongside the behavioral concerns drew a new round of criticisms.<sup>[169](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715457429854)</sup> The code of conduct was eventually updated to clarify responsibilities and outline good and bad behavior,<sup>[170](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715457460093)</sup> itself a move some claimed to stifle the freedom to debate. In all, the relicensing effort failed to achieve the goals its maintainers intended. Then again, I'm telling you about it, years later.

Events like this fade from memory only to renew, because open source licensing parallels the pace of change around us. For example, licenses may change for less noble reasons than moral resolve, such as a calculated pivot in business-model. Even acquisition. Recent events like Hashicorp’s BUSL,<sup>[171](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715457493550)</sup> Sentry’s FSL,<sup>[172](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715457510971)</sup> or Redis’s SSPL<sup>[173](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715457532751)</sup> relicensing come to mind. These companies are responding to competitors “free-riding,”<sup>[174](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715457555165)</sup> setting up SaaS copies of their open source projects. So they relicense, saying anyone but a competitor can use this. Oh, and they get to define who a competitor is. Certainly murky, uncharted legal territory with imbalanced value exchanges. A lawyer may see the worst in that language because the impact outweighs the intent and they are paid to worry. The effect on these projects’ communities and consumers is not yet resolved. The decisions may even be justified from a business perspective. Companies must make payroll—and answer to investors—but it’s a nuclear option with poor optics and questionable outcomes. Either seemingly forsake your values or reveal how flimsy they were to begin with. The press spins a narrative of open source failure. That the model and movement are incompatible with today's and tomorrow's world. The symmathesy wilts. But I suggest we're focusing on the wrong thing. Tom Calloway sums it up nicely on LinkedIn<sup>[175](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1718829923798)</sup>:

> *i've read a lot lately about how open source is dying, at a crossroads, can't keep up, must be less open.*
> 
> *nah.*
> 
> *open source is people.*
> 
> *people are still capable of amazing things. sure, open source faces challenges, but it always has. as long as there are people willing to collaborate, transparently, in good faith, that light won't go out.*

*Open source is people.* It always has been and always will be. Whatever the motivation or fallout, these relicensing events highlight foundations’ role as uncompromised stewards of open source. They, the foundations, loose federations of people, exist to make projects resilient to decision-making from singular entities. For instance, the Linux Foundation announced support for projects OpenTofu<sup>[176](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715457672977)</sup> and Valkey,<sup>[177](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715457688028)</sup> respectively open source forks of Hashicorp’s Terraform and Redis’s eponymously named product. These organizations respond to instability with a push for open governance, the learning system re-inventing itself in real-time.

In relicensing and fragmentation, projects are potentially alienating the very people that positioned them for success. You can see why this happens and also why communities may be upset. It can feel like a betrayal. The foundational contract of open source feels strained, even broken. We can directly observe big picture societal and market forces colliding with open source ideals. The repo is the battleground; the license in the weapon.

### Open Source and Politics

> *Author’s Note: We’re in the license section of this chapter right? Well, my former editors might have wanted me to remain on topic, but this one’s too important to omit. Besides, I can break the word count budget when I’m the one footing the bill!*
>
> *I wrote and rewrote and rewrote and rewrote these next sections. It created the most stress, editor comments, and self-reflection in the whole book. Please know how important it was for me to find my voice here. You can judge me for these words, but I hope you keep reading.*

It’s impossible to fully separate politics from open source software, as much as it is from public health policy, education, or nature conservancy. The roots of the free and open source movement are very political, as convenient as it is for us to ignore this fact. The economics, competing philosophies, and moral paradoxes of the material world often surface in software development. Occasionally, the protests, reforms, and conflicts of the material world do too. This is the interconnectivity of our modern ecosystem again. Open source licensing is not spared in all of this—no—at times it’s a flashpoint.

When Lerna relicensed, I was participatory as a user. I instructed my team to pin the dependency explicitly to before the relicensing, while it was still MIT. At the time, I didn’t have the wisdom or foresight to consider the impact of this license change on compliance, enforceability, or automated tooling, let alone its morality. This book’s concepts on the topic were not yet formed. My concern was stability. Lerna is one of hundreds of tools we use. We, like many teams, don’t have a lot of prioritized time to retool or refactor unplanned disruptions. The impact of this license change was not felt by the corporations deny-listed in the new license, but rather on the teams and individuals juggling their own work/life balance. We and many others were collateral damage. It’s a near-impossible value exchange to achieve without harming one constituency or another.

I waver…and think…that is in part the point. I empathize with the position of the maintainer but disagree on the approach. Aside from the poor execution of the change, I find it uniquely ineffective due to the systems within which open source software operates. People just forked it, atop the technicality that maintainers had no legal standing to relicense in the first place. The result seemed net-negative—the spectrum of engagement overreached.

Is a tool maker culpable for the violent actions of its users? How culpable is the manufacturer of a screwdriver if a murderer uses it against someone? What if the screwdriver is used to construct a combat drone? Here I see degrees of separation and intent that we must account for. How many degrees is necessary to sleep at night? I don’t know. Does the tactile nature of the hardware matter? Moving to software, is an open source maintainer liable for the actions of their derivatives? This wasn’t an AI model being trained to identify airstrike targets. That approaches simpler clarity—*the intent is to harm*. But what about an open source GPS system added to a missile guidance system? This isn’t hyperbole.

The value exchange of toolmaker is precarious, whether we’re assessing intent, impact, or liability. The JSHint essays, aptly named *You May Finally Use JSHint for Evil*,<sup>[178](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1718669558917)</sup> document the paradox of licensing neutrality. Look for more on that in the Resources section of the book. The EU Cyber Resiliency Act “upends this value exchange and tries to place liability upstream in the open source project for downstream security issues.”<sup>[179](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715458241938)</sup> Does the maintainer have agency to act here? Lerna maintainers answered: yes. The Open Source Definition would have us believe this is a simple answer: no. But life is far more complicated than that. We all need to draw our own conclusions and act according to our values and invested energy.

### Open Source as Protest. Open Source as Progress.

Change is slow and haphazard, yet it’s encouraging to see to the arc of time bend toward better licenses. The Ethical Source movement inverts the established neutral structure of open source licenses and instead asserts basic human rights. The Organization for Ethical Source advocates for licenses defining value exchanges based on accessibility, safety, and privacy. They use the legal permissions, conditions, and limitations we defined earlier to communicate these values.<sup>[180](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715458299731)</sup> One license they promote, the Hippocratic License, features a license builder feature that allows maintainers to adopt modules that reflect their specific values, such as forbidding fossil fuel companies, militaries, or repressive governments from using the software.<sup>[181](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715458323511)</sup> The Open Source Definition states that an open source license must not discriminate against persons, groups, or fields of endeavor. These two world-views of software creation and distribution oppose one another. Clear differences of opinion and approach, and a lot of gray area individuals, teams, and companies must negotiate.

I’ve had a lot of time to reflect on the Lerna relicensing. Over time, more information and lived experience has helped shape a nuanced perspective on the topic across legal, moral, and feasible dimensions. My position is vulnerable, evolving, and sometimes I feel like a weathervane whipping in the changing winds. I can empathize with any position with adequate honesty. As time goes on, however, and I see the world needing more light, I cannot help but wonder if the Lerna event should be more inspiration than cautionary tale.

You won't see me use the word “neutral” again. I deeply understand its merits, but cannot ignore its cowardice. The world needs more licenses like the Hippocratic License or the Functional Source License. The moral certainty they provide is what we need, even at the cost of implementation ambiguity. They accurately portray the software landscape as complex and unequal—yet are working to right it. They come closer to justice than any libertarian ideal open source does. I believe we must equally work within our roles. We can educate and advocate for full acknowledgement that evolving software licensing carries risk worth navigating, even if that takes more mental energy and follow-through. I’ve since become plenty comfortable accepting risk using ambiguous licenses. The world is complicated and we must live within it.

And even with these thoughts, I also have a duty to explain the environment today: large companies blanket-ban the use of projects containing certain open source licenses such as the Unlicense and the WTFPL. Even more economically-focused licenses, like the SSPL or BUSL. Not out of avarice, indifference, or malignant intent, but rather, lack of established legal clarity and risk-aversion. There simply isn’t enough case law out there. Automated license compliance tooling can dissuade or prohibit teams and individuals from using your software. Would-be users *and contributors* are locked out of engaging with your software, not because of misaligned ideals, but rather some simple if-then checks. It’s worth noting, then, that depending on your designed value exchange as a maintainer and licenser, this may be a bug or a feature! Since businesses rely on licensing jurisprudence, weigh the likely outcomes with your ethics. Do you focus on blocking the corporation or empowering the humans making a living there? How complicit is an employee in the actions of their employer? I can slam dunk that argument in most cases, but others give me pause.

Let me emphasize: this isn’t a rejection of ethical principles; it’s a clear-eyed look at where we stand today. Tech capitalism thrives off the labor of open source maintainers. It's a bleak perspective with evidence to back it up. One could see these newer licenses as a response to, a protest of, the imbalanced and exploitative nature of open source consumption. And they’d be right to be loud about it. Right to attract attention. Historical and recent acts of protest draw media attention to causes of women’s suffrage, the Vietnam War, racial justice, and the climate crisis. (FIG 4.9) Do they amplify the message or distract from it?

![FIG 4.9: Climate activists generated a lot of attention by targeting famous artwork. This may seem tangential to their aims of curbing reliance on fossil fuels, but the message is amplified by the means. Photo from Just Stop Oil/Reuters via https://www.npr.org/2022/10/26/1131377513/museum-protests-famous-artworks-history](/images/8658984b-9571-442e-a49d-364a10bce7bd.png)  
FIG 4.9: Climate activists generated a lot of attention by targeting famous artwork. This may seem tangential to their aims of curbing reliance on fossil fuels, but the message is amplified by the means. Photo from Just Stop Oil/Reuters via https://www.npr.org/2022/10/26/1131377513/museum-protests-famous-artworks-history

In a recent streak of protests, artwork was attacked to juxtapose hypocrisy or highlight looming worldwide crises.<sup>[182](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715460471802)</sup> When protesting, we shouldn’t conform to the medium of the oppressor. But there are practical limits within some systems. Do we award any credit for only attacking artwork under glass? Here we can observe calculated protest, a balance of intent and impact. How different is it from the open source protest I've described earlier? In some ways it’s similar to the pursuit of just, humane, and equitable software licensing. In some ways it’s not. I try to listen, continually learn, and to paint a broad picture of it all here as I’ve seen it play out within open source communities.

So after criticizing the methods of others, I should suggest my own. What would modulated protest look like? I posit that you can push for change while still doing right by your users. Microsoft acquired GitHub not long after the Lerna relicensing event took place, renewing calls for both companies to drop ICE. As far as I know—they haven’t. I have nuanced perspectives on GitHub the product and company. It’s undoubtedly been a force for good in many projects and communities—and has made public, positive, reflective changes over the years—while also having organizational, legal, cultural, and business conflicts that don’t always make them the paragon of free and open source stewardship. To be fair, no company is perfect here and it’s naïve to think otherwise. I hope I’ve struck that balance in the pages of this book. We can be participants in an ecosystem while advocating for its improvement. I still use GitHub every day, optimistically, with eyes wide open, and will continue to do so. The Software Freedom Conservancy acknowledges this tight-rope walk. They demand change, for the very reasons Lerna did, as well as unresolved licensing and ethical questions related to the AI-powered, publicly trained Copilot feature.<sup>[183](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715460581247)</sup> They encourage others to raise their voices, and empower them along a spectrum of engagement that includes migration, boycott, and declaration of GitHub use under protest.<sup>[184](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715460595655)</sup> These are all more pro-community and don’t cause collateral damage to unwitting users. And of course, petitions for “redress of grievance” to your elected representatives is enshrined in another important file.

### Where to Learn More

That was a lot. Licensing is a prism that reveals a surprising number of serious topics. I hope I didn’t discourage you from supporting existing projects or launching your own open source efforts. The connections we can build are simply too strong to ignore. I have no doubt you’ll help further the conversation if you choose.

For new work you release yourself—all my previous advice holds. For new work you wish to open source while on-the-clock at an employer, consult your OSPO, lawyer, or Legal team before starting an endeavor. Read GitHub’s *The Legal Side of Open Source*<sup>[185](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715460640287)</sup> as a gateway into so many more subjects. I’ve also started diving into Amanda Brock’s edited book, *Open Source Law, Policy & Practice.*<sup>[186](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715460669024)</sup>

Let your license help communicate the value exchanges you expect users and contributors to engage in. If you don’t want a weapons manufacturer or a cloud-based competitor using your software, that’s entirely up to you. But know these licenses don’t satisfy the strictest definitions of open source licensing. Only you can determine if that’s alright. Your license is but one part of a complete communications and governance plan that should cover all of the public-facing work your project creates. The license can set up the legal skeleton, but what you do within it is the beating heart that will define your project to the community.

## CHANGELOG

The third fundamental file is the CHANGELOG. It documents how the project evolves over time. Change can come in many forms, from a README bulleted list to blog posts with migration guides, automated code alterations, and video walkthroughs. The change management of your project is another intentionally designed value exchange, and one of the most critical. Once someone starts using your code, they become in part dependent on it. This is a risk to them and a responsibility for you. Responsibly managing and communicating change is the least you can do.

Most projects stick to the convention of defining a release-worthy milestone via a semver-compliant Git tag. When people are evaluating or using your software, they will look to the stability of release as a differentiator. How often does your API change? Do you provide step-by-step guidance when it does? How effectively you communicate version-to-version changes can save them hours and hours of time over the lifespan of their engagement. In the thick of a dependency updates ticket, or when skimming a Dependabot summary, engineers will be making a beeline to your CHANGELOG file or releases page to determine if they are impacted.

### git commit\-ment

How you disclose what’s changed is up to you, but make it brief and more relevant to end-users than contributors, if you have to choose. Why? Because contributors are more comfortable and motivated to look deeper into a project’s Git commit history. When time is tight, optimize for the other developer. Future you and future me will thank you. A year from now, you will be a stranger to this code too.

A lot of tooling and techniques seek to document change at the git commit level. Yes, atomic commits<sup>[187](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715484488349)</sup> are fantastic to review or revert, but require a lot of mental energy to craft. The result is adoption of specifications like the conventional commit syntax.<sup>[188](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715484519225)</sup> Tooling can automatically pick up these commits and do things like update a CHANGELOG, increment your documented semver, even git tag your codebase. This is powerful stuff, but easy to mess up and easier still for your contributors. You don’t want to nitpick an external contributor’s process—they are already going out of their way to help you. You need to meet them where they are. Often, development looks like this:

> feat: WIP date refactor
> does this work?
> more WIP
> forgot a file
> fix lint in CI

Accept and sidestep these problems by advocating for basic Git hygiene:

* **Branch by default.** Create a safe, shareable space for each new body of work. You can work on as many of them as needed, independent of one another, and use tooling like GitHub pull requests to test and review them carefully.
    
* **Keep all change small.** Limit the scope of work to a single complete feature or fix. This is what we mean by making atomic changes. See something unrelated in need of sprucing up? Resist the urge to sprinkle it in. You want potential reviewers to have a straightforward review, both in coherence and in brevity. Sometimes small change is impossible—the work loses clarity if broken up more. And with those large sizes come big commit lists tempting you to rewrite. There is a time and place to revise Git history, but I’d argue they aren’t normal days in the office.
    
* **Set the mood.** Use brief, second-person imperative commands, where the subject, *you*, is implied. (Like that last sentence.) Even if you don’t end up using tooling to read these commits, writing them this way focuses the effort again toward the impact of the change. This can help when reviewing code or history.
    
* **Relax.** For as much as it matters, it also doesn’t. Fretting over perfect history, rebasing, submodules, worktrees, it’s enough to overwhelm. Approach the depth of the tool as ready, if at all.
    

A compromise approach to the rigidity of a prescribed commit structure is to squash-and-merge all commits upon merge.<sup>[189](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715484697971)</sup> This gives you as a maintainer control over the final commit message content, while allowing for commit-level leeway during feature development. See the Resources section for more Git recommendations.

### Releases and Publication

Sites like GitHub and GitLab package up sets of change as a “release.” These platforms allow you to associate some long-form markdown text to a Git tag. If I cannot find a CHANGELOG file, I look for releases. Releases also can contain project artifacts like binaries or archive files for end users to directly interact with.

If you intend for your project to be available on the public npm registry for users to download, you need to publish the artifacts too.<sup>[190](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715484796505)</sup> Keep your Git repository, CHANGELOG, releases, and available registry packages in synchronicity whenever possible. Published code omitted from a repository is lazy at best and suspicious at worst—sometimes evidence of ill intent like malware. Unreleased code in a repository is less accessible to others, diminishing its reach.

Remember that in most circumstances, people encountering your project’s release documentation or artifacts will either be 1) in a hurry to upgrade with as little effort as possible, or 2) looking to get up and running as quickly as possible. In both cases, clear, concise accounting of changes creates a healthy exchange of expectations.

## CODE\_OF\_CONDUCT

Adding a CODE\_OF\_CONDUCT file to your repository or website makes clear to everyone engaged with your project what the rules are. It defines what is and isn’t acceptable behavior within what media, who is covered by the policy, enforcement guidelines, how to report problems, and what happens after a concern is raised. The preamble of the popular Contributor Covenant code of conduct is representative of the intent and the stakes<sup>[191](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1716872723010)</sup>:

> *We as members, contributors, and leaders pledge to make participation in our community a harassment-free experience for everyone, regardless of age, body size, visible or invisible disability, ethnicity, sex characteristics, gender identity and expression, level of experience, education, socio-economic status, nationality, personal appearance, race, caste, color, religion, or sexual identity and orientation.*
>
> *We pledge to act and interact in ways that contribute to an open, welcoming, diverse, inclusive, and healthy community.*

GitHub makes adding a code of conduct a wizard-like process,<sup>[192](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715484968831)</sup> allowing users to choose between popular codes of conduct and add contact info for reports. Having a code of conduct on file results in its display on the repository home page, new issue page, discussion page, and elsewhere. It factors directly into the repository’s “community standards” insight metric. This makes the process about as simple as it can get. But what happens next matters more.

### Beyond a Code of Conduct is Governance

A code of conduct makes expectations public and clear for all parties, but it’s the first step in a holistic effort to create an inclusive experience. With a code of conduct in place, it’s vital that maintainers are trained and prepared to enforce it. Adopting a governance plan beyond the initial reporting mechanism creates the follow-through that yields real safety.

For example, the Node.js project contains a two-thousand-word moderation policy<sup>[193](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715485258693)</sup> that outlines who the code of conduct applies to (everyone), emphasizes the opportunity for all parties to assume self-corrective positive intent, and guides maintainers and users through what should happen when a code of conduct violation is reported. It includes four means to request moderation, some near-anonymous or out of band from where the abuse is happening. The policy also details escalation of moderation and how to make changes to the policy itself. Important also is what to do in the event of a moderation dispute. This fidelity was the result of hard-learned lessons, incrementally applied to become a more inclusive, clear, introspective, and objective process. Projects that invest in this work are communicating that people matter more than code, and that should be applauded.

### Everyone Benefits from a Code of Conduct

*Why bother with a code of conduct?* In all my encounters, it is only men that ask that question. They are telling on themselves. They state that you don’t need a code of conduct for other places: the corner pub, college classroom, job site, or grocery store. And yet life would probably be better with one, and is! Even a cursory search brings us to employee handbooks, collegiate codes of conduct, and trespass laws . Shoutout to the University of Minnesota code of conduct,<sup>[194](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715485432538)</sup> which defines 13 different enforcement steps, and outlines hearing and appeals processes. The revision history dates back to 1970!

Luckily, we as a *profession* are catching up to basic rules of decency and inclusion. That means many have come before us and taken a stand. People like Sage Sharp, who demanded more from the Linux kernel community.<sup>[195](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715485497136)</sup> A community that briefly enshrined an inadequate “code of conflict.”<sup>[196](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715485532357)</sup> Sage, and others, have seen the rampant sexism, inequality, abuse, and favoritism of die-hard hacker culture, and rejected it for something better. That isn’t controversial—it’s civilization knocking on the doorstep. Fortunately, you can use this as a filter. If someone cannot handle basic decency, you know what to do now. History is full of important contributions made by unsavory persons. We don’t need to glorify their contributions despite their failings. We, and those curmudgeons, must demand more of our collective selves. Tech and open source are speedrunning the same cycle at play across broader society.

As these changes play out, “cultural” pushback from an old-guard of personalities and their followers surfaces within discussion forums, comment threads, and even during board elections for the Open Source Initiative standards body. Progress is apparently an existential threat to them. They tantrum and complain of censorship, lashing out at would-be allies and contributors, if only they saw it that way. The vitriol is sign that ever-increasing inclusion is working. There is no doubt much more work to be done, but improvements arrive across the industry, in big and small ways. As Nathan Schneider put it: “If the early architects of open source feel threatened by a new generation demanding more, that is probably a sign of progress.”<sup>[197](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715485748545)</sup>

An in-person industry event, and surely a thing as simple as some message boards around a code repository, can get this right. Jen Simmons, in considering a code of conduct to a conference, uses the analogy of fire code and building safety. Within a discussion on the blog *CSS-Tricks*, she wrote<sup>[198](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1719056764414)</sup>:

> *Many of these conferences are held in hotels. The hotel itself has a plan about what to do if there’s a fire in the building. There are laws, in fact, about the hotel and fire safety. The fire marshal visits periodically to make sure those laws are being obeyed. What is considered safe is figured out ahead of time. When and how to evacuate the building is figured out ahead of time. What equipment is needed (detectors, sprinklers, standpipes) is figured out ahead of time. It’s not figured out during a fire. It’s not dependent on who’s there, or why a fire was started. It’s decided long before, when there is no problem in sight, so a problem does happen, people have a clue about what to do in the moment.*

These policies are designed and distributed *before* something goes wrong. As Simmons says, it would be unthinkable to devise an evacuation gameplan during an emergency. It’s why we practice fire drills. What we do now to prepare for difficulty makes facing those situations easier, because we have a shared understanding, a written record, and muscle memory to spur our actions.

I almost omitted a code of conduct as a fundamental, but not for lack of importance. Rather, most projects start with a non-existent or closed community. Maybe a population of one. Given everything else going through your mind when open sourcing your fledgling project, moderating a community might feel overwhelming. But it costs you nothing to adopt an inclusive mindset, and a lot of help is out there. Sameera Kapila says within *Inclusive Design Communities*<sup>[199](/read/endnotes#h5EYfv5qDd2WmIvO-endnote-1715485180375)</sup> that “if everyone takes even one or two of these small steps toward inclusivity, I believe we’ll see change.”

## Start Simple

Maybe you start with a small set of files you want to get off your local machine. Maybe you want to share code with your network. As Brad Frost says in a long-pinned social media post: “Work hard. Don’t be an asshole. Share what you know.” That’s succinct! But often we need more guardrails. Create clear expectations with these four fundamental files, README, LICENSE, CHANGELOG, and CODE\_OF\_CONDUCT—you won’t regret it. One day, you might just find yourself in the company of friends and strangers. These folks are allies when respected and welcomed. They’ll tell you in word and deed what else the project needs. Listen. Next chapter will explore how to do just that.

[Chapter 5: Community Investment ➡️](/read/community_investment)