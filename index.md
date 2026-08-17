---
layout: single
author_profile: true
classes: wide
permalink: /
---

<div class="resume-intro">
  <p class="resume-kicker">Senior Backend Engineer</p>
  <h1>Building the systems behind AI-powered products.</h1>
  <p class="resume-lede">I design and ship distributed backend systems, AI infrastructure, and high-throughput services. Over 7+ years at monday.com, Savvy Security, and Intel, I’ve worked across AI gateways, load balancing, retrieval pipelines, security integrations, and performance-critical developer tooling.</p>
</div>

## Things I’ve Built

### AI Gateway

Built and operate the shared **AI Gateway and SDK** used by development teams across monday.com products. It gives engineers one interface for working with multiple AI providers and models without managing provider credentials or subscriptions themselves. I add model support, handle production issues, support adopting teams, track usage and costs, and maintain Datadog dashboards for reliability, latency, and cost.

### Distributed AI Load Balancing

Designed a distributed load balancer spanning multiple providers, accounts, regions, and rate limits—for example, ten Azure accounts alongside three AWS accounts. For every model request, it finds the provider-account-region combinations that can serve the requested model and region, then selects an eligible target without exhausting a single account’s quota. Because the gateway runs across several regions and deployments, it uses consistent hashing on the session ID to keep a session routed to the same provider server.

### Workspace RAG & Embedding Pipelines

Built an account-level embedding pipeline that scans monday.com boards and represents their structure, including column names, column types, and sections. Search uses those embeddings to match by **semantic meaning**, improving on the lexical search that was available before and making it easier to find the right boards without knowing their exact names or wording.

### Cross-Device Playbook Throttling

Built a Firestore-backed throttling system for Savvy’s Chrome extension and its in-browser security playbooks. Administrators could show contextual warnings or block a page—for example, reminding employees not to publish private company data—without repeatedly interrupting the same user. Throttling was configurable per website, supported expiration rules such as “once a week,” and synchronized across a user’s computers.

### Transaction-Safe Extension Coordination

Extended the throttling mechanism to coordinate expensive extension operations across users. When an administrator visited a supported web application, the extension could discover and report every user in that customer account. Firestore transactions provided an atomic shared state so multiple administrators could not overwrite one another or trigger duplicate discovery work and unnecessary requests to the customer’s application.

### Authentication Token Cache

Built a distributed **Redis token cache** mapping extension signing tokens to user and account data, avoiding repeated token decoding on every request across multiple backend deployments. The cache respected token expiration and invalidated entries as soon as tokens expired. Using Go’s `pprof` tooling to measure the result, I found that it reduced request CPU time by **about 30%** while also providing a smaller latency improvement.

### Resilient Extension Authentication

Designed a low-friction authentication flow for Savvy’s Chrome extension. The extension could open the login page and reuse a recent browser session to sign the user in automatically. It continuously checked token validity and recovered safely from expiration, extension restarts, and computers waking after hours asleep, while suppressing retries so users were not bombarded with repeated login attempts.

### CAD Automation Tooling

Designed tools and automations for Intel’s physical-design engineers, writing **Tcl integrations for Synopsys Fusion Compiler and Cadence tooling**. We adapted existing tools and created new workflows for evolving manufacturing methods and technologies, working directly with the physical-design team to investigate bugs and refine changing requirements.

### Layout Verification Workflows

As part of Intel’s CCAD team, automated verification that physical designs complied with manufacturing specifications. The workflows encoded production rules into repeatable checks so engineers did not need to perform the verification manually.

### Quarto Presentation Generator

I love creating technical presentations in Markdown, so I added AI to make better use of Quarto’s RevealJS features. The tool turns an article into a structured presentation, writes each slide with speaker notes, and outputs a renderable `.qmd` file. It supports OpenAI, Anthropic, and local Ollama models.

[Explore the project →](https://github.com/snirye/quarto-presentation){: .project-link}

### wt-claude

I built this before worktree support became common in IDEs, so I could work on several features in parallel without organizing every checkout by hand. The CLI creates or resumes worktrees, keeps them in a predictable location, and opens an iTerm session with Claude Code in the right directory. It also supports repository discovery and reusable system prompts.

[Explore the project →](https://github.com/snirye/wt-claude){: .project-link}

### Pictionary AI

I built this when Ollama first appeared as a playful demo of what a free local vision model could do. Players draw while the model guesses in real time, earning points when it gets the word right. The game carefully queues drawing updates to stay responsive despite local-model latency.

[Explore the project →](https://github.com/snirye/PictionaryAI){: .project-link}

### Tcl Outline for VS Code

At Intel, our Tcl automation files often exceeded 2,000 lines and were difficult to navigate. I built this VS Code extension using regular expressions and brace matching to expose procedures and nested code in the Outline view. It now has **more than 2,000 users**.

<figure class="project-preview">
  <img src="{{ '/assets/projects/tcl-outline.jpg' | relative_url }}" alt="VS Code showing the Tcl Outline extension with nested symbols in the Outline panel" loading="lazy">
  <figcaption>Nested Tcl symbols in VS Code’s Outline view.</figcaption>
</figure>

[VS Code Marketplace →](https://marketplace.visualstudio.com/items?itemName=sniryehuda.tcl-vsc-outline){: .project-link} · [Source code](https://github.com/snirye/tcl_outline_vscode)

### Fake Tab · Chrome Extension

The idea came to me while sharing my screen in a meeting: it would be funny to hide harmless “Easter eggs” among the visible tabs. The Chrome extension creates inactive tabs with preset or custom titles and emoji favicons, while remembering recent titles locally.

<figure class="project-preview">
  <img src="{{ '/assets/projects/fake-tab.png' | relative_url }}" alt="Fake Tab Chrome extension open in Chrome, showing custom-title input and quick presets" loading="lazy">
  <figcaption>Create a custom tab or choose a quick preset before screen sharing.</figcaption>
</figure>

[Chrome Web Store →](https://chromewebstore.google.com/detail/fake-tab-embarrassing-tit/bfhjffpbcehlmjahbiccimljgokdkhpc){: .project-link} · [Source code](https://github.com/snirye/fake-tab)

### Seder Boker · Kids’ Morning Routine Dashboard

I built this Hebrew-language dashboard when summer vacation disrupted our children’s usual morning habits. We leave a device on the table, and the children mark tasks as they finish them while parents can adjust the routine. Everything stays on the device for privacy, and it became part of our real family routine.

<figure class="project-preview">
  <img src="{{ '/assets/projects/seder-boker.jpg' | relative_url }}" alt="Seder Boker’s Hebrew morning-routine dashboard, showing task cards and progress for two children" loading="lazy">
  <figcaption>A focused, child-friendly routine board with independent progress tracking.</figcaption>
</figure>

[Open the live app →](https://sederboker.co.il/){: .project-link}

### AirCondServer

I built this because I wanted to turn off the living-room air conditioner from bed. I hid an ESP controller and IR LED inside a lamp, aimed it at the unit, and reproduced the remote’s Gree protocol. A local browser dashboard controls power, mode, and temperature without a cloud account.

<figure class="project-preview">
  <img src="{{ '/assets/projects/aircond-server.jpg' | relative_url }}" alt="AirCondServer’s local air-conditioner dashboard with power, mode, and target-temperature controls" loading="lazy">
  <figcaption>Local Wi-Fi control for power, operating mode, and target temperature.</figcaption>
</figure>

[Explore the project →](https://github.com/snirye/AirCondServer){: .project-link}

## Education

### B.Eng. in Computer Engineering
{: .resume-role}

<span class="resume-company">Bar-Ilan University</span>
<span class="resume-meta">2022 · GPA 90</span>

## Technical toolkit

<div class="toolkit-list">
  <p><strong>Primary:</strong> Go, TypeScript, Node.js, Python, C++, SQL</p>
  <p><strong>AI:</strong> AI gateways, RAG, embeddings, OpenAI API, LangChain, Ollama</p>
  <p><strong>Systems:</strong> GCP, Docker, Linux, Firestore, NoSQL, REST, load balancing, caching</p>
  <p><strong>Additional:</strong> JavaScript, Zig, TCL, C, Bash, Assembly, Java</p>
</div>

## Contact

I’m always happy to talk about thoughtful engineering work and interesting systems problems.

[Email me](mailto:sniryehud@gmail.com){: .contact-link} · [GitHub](https://github.com/snirye) · [LinkedIn](https://www.linkedin.com/in/snir-yehuda-5996a0186/)
