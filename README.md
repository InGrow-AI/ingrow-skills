# InGrow skills

The open skill layer for GTM. 25 skills that turn Claude Code, Cursor, Codex or any agent into a growth team: finding accounts, reading buying signals, reaching the right people and researching competitors.

Every skill runs on [InGrow](https://tryingrow.com), one API for live data from LinkedIn, X, Facebook, TikTok, YouTube, Glassdoor, job boards, Amazon, G2, Trustpilot, Apollo, website traffic, tech stacks and SEC filings. Each step names the exact InGrow tool and its price, so your agent knows what a run costs before it starts.

## Set up

1. Create an API key in the [InGrow dashboard](https://app.tryingrow.com). You start with a $1 free credit.
2. Connect your agent. Either add InGrow as an MCP server with the command and token from the dashboard, or give your agent the link to [llms.txt](https://tryingrow.com/llms.txt) and your key.
3. Add the skills.

Claude Code, for one project:

```bash
git clone https://github.com/InGrow-AI/ingrow-skills.git
mkdir -p .claude/skills && cp -R ingrow-skills/skills/* .claude/skills/
```

Claude Code, for every project:

```bash
mkdir -p ~/.claude/skills && cp -R ingrow-skills/skills/* ~/.claude/skills/
```

Other agents: each skill is a plain Markdown file. Paste `SKILL.md` into the agent's instructions, or point the agent at the file.

## How a skill is written

Each skill lives in `skills/<name>/SKILL.md` with a `name` and a `description` in its front matter, so agents load it only when the task matches. The body says what to ask the user, which InGrow tools to call in which order, what to return, what it costs, and the guardrails.

Tool names match the InGrow MCP tools. Over REST, call the path shown next to each tool with your key in the `x-api-key` header.

## Skills

### Find accounts

| Skill | What it does | InGrow tools |
| --- | --- | --- |
| [ICP matching](skills/icp-matching/SKILL.md) | Build a list of companies that match an ideal customer profile (industry, size, location, keywords), then check each one's headcount trend and tech stack before it goes on the list. | `apolloSearchOrganizations`, `techStackDetectTechnologies`, `linkedinGetCompanyInsights` |
| [Score fit times a fresh signal](skills/score-fit-times-signal/SKILL.md) | Rank a list of accounts by multiplying how well each fits the ICP by how fresh its strongest buying signal is (funding, hiring for the team you sell to, headcount growth). | `linkedinGetCompanyInsights`, `linkedinSearchJobs`, `secSearchFormD` |
| [Qualify accounts by website traffic](skills/website-traffic-qualification/SKILL.md) | Pull monthly website visits, traffic sources and top countries for a list of domains and keep the ones above a size or growth threshold. | `webTrafficGetWebsiteTraffic` |
| [Target by tech stack](skills/tech-stack-targeting/SKILL.md) | Find which companies in a list run a competitor's tool or a tool that pairs with the user's product, using live website detection. | `techStackAnalyzeWebsite`, `techStackDetectTechnologies` |
| [Amazon seller prospecting](skills/amazon-seller-prospecting/SKILL.md) | Find brands and sellers that are growing on Amazon in a category, with their ratings and product counts, to prospect for ecommerce services or software. | `amazonGetBestSellers`, `amazonGetProduct`, `amazonGetSeller`, `amazonGetSellerProducts` |

### Buying signals

| Skill | What it does | InGrow tools |
| --- | --- | --- |
| [Companies that just raised](skills/companies-that-just-raised/SKILL.md) | Find private companies that filed a Form D (a fundraise) recently in chosen industries, then check headcount growth and website traffic to confirm momentum. | `secSearchFormD`, `linkedinGetCompanyInsights`, `webTrafficGetWebsiteTraffic` |
| [Teams being built](skills/teams-being-built/SKILL.md) | Find companies hiring several people in the function the user sells to, a sign that a new team and budget exist. | `linkedinSearchJobs`, `jobsSearchJobs`, `linkedinGetCompanyInsights` |
| [Leadership change alerts](skills/leadership-change-alerts/SKILL.md) | Find public companies that just appointed or lost an executive, using 8-K item 5.02 filings, and identify the new leader. | `secSearchFilings`, `secExtractFilingItem`, `linkedinGetProfile` |
| [Public company priorities](skills/public-company-priorities/SKILL.md) | Read a public company's latest 10-K or 10-Q risk factors and management discussion to pull out its stated priorities and problems. | `secSearchFilings`, `secExtractFilingItem` |

### People and contacts

| Skill | What it does | InGrow tools |
| --- | --- | --- |
| [Decision-makers at an account](skills/decision-makers-at-account/SKILL.md) | Find the people who own a buying decision at a target company by title and seniority, confirm their current role on LinkedIn, and rank who to contact first. | `apolloSearchPeople`, `linkedinGetProfile` |
| [Find work emails](skills/find-work-emails/SKILL.md) | Find verified work emails for a list of LinkedIn profiles, with a cost check before running. | `contactsGetEmail` |
| [People engaging with competitors](skills/competitor-post-engagers/SKILL.md) | Collect the people who reacted to and commented on a competitor's recent LinkedIn posts, then keep the ones who match the buyer profile. | `linkedinGetCompanyPosts`, `linkedinGetCompanyPostComments`, `linkedinGetPostReactions`, `linkedinGetProfile` |
| [Influencer audiences](skills/influencer-audiences/SKILL.md) | Find the LinkedIn creators your buyers follow on a topic, then collect the buyers who engage with their posts. | `linkedinSearchPosts`, `linkedinGetProfilePosts`, `linkedinGetProfilePostComments`, `linkedinGetProfile` |
| [X conversation mining](skills/x-conversation-mining/SKILL.md) | Search X for people describing a problem the user solves, then qualify the accounts by bio and follower count. | `twitterSearch`, `twitterGetUser`, `twitterGetTweetReplies` |

### Engage before you pitch

| Skill | What it does | InGrow tools |
| --- | --- | --- |
| [Write only once the channel is open](skills/write-once-the-channel-is-open/SKILL.md) | Check which prospects have an open LinkedIn profile (messageable without a connection) and route them to a direct message, and the rest to a connection request first. | `linkedinGetOpenProfileStatus` |
| [Warm up, then ask](skills/warm-up-then-ask/SKILL.md) | Read a prospect's recent posts and the posts they react to, then plan two or three genuine touches before the ask. | `linkedinGetProfilePosts`, `linkedinGetProfileReactions` |
| [Comment first](skills/comment-first/SKILL.md) | Find this week's posts from a list of prospects and draft a thoughtful comment for each, ranked by how much engagement the post is getting. | `linkedinGetProfilePosts`, `linkedinGetPost` |
| [Comments worth replying to](skills/comments-worth-replying-to/SKILL.md) | Go through the comments on the user's own recent LinkedIn posts and surface the commenters who match the buyer profile, with a suggested reply. | `linkedinGetProfilePosts`, `linkedinGetProfilePostComments`, `linkedinGetProfile` |

### Account and market research

| Skill | What it does | InGrow tools |
| --- | --- | --- |
| [Account research brief](skills/account-research-brief/SKILL.md) | Produce a one-page brief on a company before a call: headcount and growth, recent LinkedIn posts, open roles, website traffic, tech stack and review ratings. | `linkedinGetCompanyInsights`, `linkedinGetCompanyPosts`, `linkedinSearchJobs`, `webTrafficGetWebsiteTraffic`, `techStackDetectTechnologies`, `reviewsGetG2Product` |
| [Team pains from Glassdoor](skills/glassdoor-team-pains/SKILL.md) | Read a company's Glassdoor reviews filtered to the team the user sells to and pull out recurring complaints about tools, process and workload. | `glassdoorSearchCompanies`, `glassdoorGetCompanyOverview`, `glassdoorGetCompanyReviews` |
| [Hiring cost benchmark](skills/hiring-cost-benchmark/SKILL.md) | Estimate what a company is paying to hire the roles it has open, using salary data for those titles and locations. | `jobsGetCompanySalary`, `jobsGetEstimatedSalary` |
| [YouTube and podcast prospecting](skills/youtube-podcast-prospecting/SKILL.md) | Find YouTube channels and podcasts in a niche, with subscriber counts and recent topics, for sponsorships, guest spots or partnerships. | `youtubeSearch`, `youtubeGetChannel`, `youtubeSearchChannel` |

### Competitive intelligence

| Skill | What it does | InGrow tools |
| --- | --- | --- |
| [Competitor ad watch](skills/competitor-ad-watch/SKILL.md) | Pull a competitor's live ads from the Meta Ad Library and summarize their offers, hooks and how long each ad has run. | `facebookSearchAdvertisers`, `facebookGetAdvertiserAds` |
| [TikTok ad angles](skills/tiktok-ad-angles/SKILL.md) | Pull the top performing TikTok ads in an industry or for a keyword and break down their hooks, formats and calls to action. | `tiktokGetTopAds`, `tiktokGetAdDetails` |
| [Review battlecard](skills/review-battlecard/SKILL.md) | Build a battlecard against a competitor from its G2 page and its lowest-rated G2 and Trustpilot reviews. | `reviewsGetG2Product`, `reviewsGetG2ProductReviews`, `reviewsGetTrustpilotReviews` |

## Contributing

Add a skill or improve one. See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

[MIT](LICENSE)
