[Gitlab Scraper](https://apify.com/fatihtahta/gitlab-scraper?fpr=data)

## Overview

**Gitlab Scraper | Fast & Reliable | $2 / 1k** captures structured, public data from [gitlab.com](https://gitlab.com) including projects and user profiles. GitLab hosts millions of repositories, contributors, and discussions, making it a rich source for tracking technologies, communities, and product ecosystems. This actor automates collection with dependable runs so you can focus on analysis instead of manual browsing.

## Why Use This Actor

- **Market and competitive research:** Map projects, contributors, and activity around specific technologies or vendors.
- **Lead and outreach lists:** Identify active maintainers, organizations, and repositories relevant to your campaigns.
- **Product and trend monitoring:** Follow repositories by language, license, or topics to spot momentum and adoption patterns.
- **Directory building:** Assemble curated lists of projects or profiles with consistent metadata for enrichment or audits.
- **Time savings and reliability:** Schedule recurring runs and keep datasets fresh without manual exports or copy-paste work.

## Input Parameters

| Parameter | Type | Description | Default |
| --- | --- | --- | --- |
| `searchQueries` | array of strings | Keywords to search on GitLab. Each entry runs separately. | — |
| `searchUrls` | array of strings | Full GitLab search URLs (e.g., `https://gitlab.com/search?scope=projects&search=vscode`). The actor extracts the search term and scope automatically. | — |
| `searchMode` | string (`projects` | `users` | `projects_and_users`) | Choose which GitLab entities to fetch for each query. Select projects only, users only, or let the actor honor scopes from search URLs. | — |
| `projectLanguage` | string | Optional language filter for project searches (e.g., `typescript`). | — |
| `projectArchived` | boolean | Include archived repositories when enabled. | — |
| `projectMinStars` | integer | Minimum star count to include a project. | — |
| `projectMinForks` | integer | Minimum fork count to include a project. | — |
| `projectLicense` | string | License filter for projects (e.g., `apache-2.0`). | — |
| `projectTopics` | array of strings | Topics to require on projects (e.g., `security`, `cli`). | — |
| `projectOwner` | string | Owner namespace to target (e.g., `gitlab-org`). | — |
| `projectFilterTokens` | string | Additional GitLab search tokens to append to project queries (e.g., `stars:>50 archived:false`). | — |
| `maxResults` | integer | Maximum combined project and user records to save across all queries. | `50000` |

## Example Input

```
{
  "searchQueries": ["machine learning", "security research"],
  "searchMode": "projects_and_users",
  "projectLanguage": "typescript",
  "projectMinStars": 50,
  "projectLicense": "apache-2.0",
  "maxResults": 5000
}
```

## Example Output

Each dataset item is structured for straightforward analysis or enrichment.

```
{
  "type": "project",
  "name": "heritage_site_HackJaipur_hackathon",
  "nameWithNamespace": "Manjot Singh / heritage_site_HackJaipur_hackathon",
  "pathWithNamespace": "manjotsinghbagha/heritage_site_HackJaipur_hackathon",
  "webUrl": "https://gitlab.com/manjotsinghbagha/heritage_site_HackJaipur_hackathon",
  "description": "Hack-Jaipur hackathon project to build and e commerce site with the help Autho, Machine learning, 3D models,  Django, Python, Html, CSS, javascript",
  "avatarUrl": null,
  "topics": [],
  "starCount": 0,
  "forksCount": 0,
  "visibility": "public",
  "archived": null,
  "createdAt": "2025-12-18T19:18:04.039Z",
  "lastActivityAt": "2025-12-18T19:18:03.925Z",
  "namespace": {
    "name": "Manjot Singh",
    "fullPath": "manjotsinghbagha"
  }
}
```

- `type` — Indicates whether the item is a project or user entry.
- `name`, `nameWithNamespace`, `pathWithNamespace` — Project identifiers and paths for linking and indexing.
- `webUrl` — Direct link to the project page.
- `description`, `topics`, `visibility`, `archived` — High-level project details and status.
- `starCount`, `forksCount` — Popularity and community engagement signals.
- `createdAt`, `lastActivityAt` — Timestamps for project creation and latest activity.
- `namespace` — Owner or organization information.

## Notes & Limitations

- Use this actor responsibly and in accordance with GitLab’s terms of service and applicable laws.
- Public data can include personal information; ensure you have a lawful basis to store or process it.
- Start with modest result limits when exploring new filters, then scale once you confirm the scope.

## Support

Questions or custom needs? Open an issue on the **Issues** tab of the actor page in Apify Console and it will be resolved around the clock.

Happy Scraping,

- Fatih