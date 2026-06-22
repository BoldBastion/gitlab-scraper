[Gitlab Scraper](https://apify.com/klondikeking/gitlab-scraper?fpr=data)

Extract comprehensive project, user, and group data from GitLab with enterprise-grade reliability. Perfect for DevOps intelligence, competitive analysis, open source research, and marketplace monitoring.

## What This Actor Does

GitLab Scraper extracts detailed metadata from GitLab projects, including stars, forks, issues, merge requests, README content, topics, and contributor information. Unlike basic scrapers, it uses GitLab's official REST API for maximum reliability and data completeness.

### Key Features

- **Project Search**: Find projects by keywords across all of GitLab
- **User Profile Scraping**: Extract all projects from specific users
- **Group Intelligence**: Scrape complete project listings from groups/organizations
- **Deep Metadata**: Stars, forks, issues, merge requests, topics, and more
- **README Extraction**: Optionally fetch README content for analysis
- **Pagination Support**: Handle large result sets automatically
- **Rate Limit Resilience**: Built-in retry logic and respectful API usage

## Use Cases

### 1. DevOps Intelligence

Monitor popular container images, CI/CD configurations, and DevOps tooling trends. Track which projects are gaining traction in the developer community and identify emerging technologies before they become mainstream.

### 2. Competitive Analysis

Analyze competitor open source strategies by tracking their GitLab presence. Monitor their most popular projects, development velocity, and community engagement metrics.

### 3. Open Source Research

Academic researchers and analysts can study open source trends, technology adoption patterns, and collaborative development practices across the GitLab ecosystem.

### 4. Talent Sourcing

Identify active developers and high-quality projects for recruitment purposes. Filter by programming language, activity level, and community engagement.

### 5. Marketplace Monitoring

Track plugin and extension ecosystems hosted on GitLab. Monitor version updates, community feedback, and adoption metrics.

## Input Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| `searchQueries` | string[] | No | Search terms to find projects (e.g., "machine learning", "react") |
| `projectPaths` | string[] | No | Specific project paths like "gitlab-org/gitlab" |
| `userNames` | string[] | No | GitLab usernames to extract projects from |
| `groupPaths` | string[] | No | GitLab groups to extract all projects from |
| `maxResults` | integer | Yes | Maximum projects to extract (1-1000) |
| `includeDetails` | boolean | No | Fetch README content and merge request counts |
| `proxyConfiguration` | object | No | Proxy settings (uses Apify Proxy by default) |

### Example Input

```
{
  "searchQueries": ["machine learning", "docker"],
  "userNames": ["gitlab-org"],
  "maxResults": 50,
  "includeDetails": true
}
```

## Output Schema

Each extracted project includes:

```
{
  "id": 12345,
  "name": "example-project",
  "path": "example-project",
  "pathWithNamespace": "user/example-project",
  "description": "A sample project description",
  "webUrl": "https://gitlab.com/user/example-project",
  "starsCount": 150,
  "forksCount": 45,
  "openIssuesCount": 12,
  "mergeRequestsCount": 3,
  "defaultBranch": "main",
  "visibility": "public",
  "archived": false,
  "createdAt": "2023-01-15T10:30:00Z",
  "lastActivityAt": "2024-01-20T14:22:00Z",
  "language": "Python",
  "topics": ["machine-learning", "data-science"],
  "tagList": ["v1.0", "stable"],
  "readmeContent": "# Example Project\\n\\nThis is the README...",
  "owner": {
    "id": 67890,
    "username": "user",
    "name": "User Name",
    "webUrl": "https://gitlab.com/user"
  },
  "containerRegistryEnabled": true,
  "issuesEnabled": true,
  "mergeRequestsEnabled": true,
  "wikiEnabled": true
}
```

## Pricing

This Actor uses **Pay Per Event** pricing:

- **$0.001 per project extracted**

Example costs:

- 100 projects = $0.10
- 1,000 projects = $1.00
- 10,000 projects = $10.00

No monthly fees, no minimums. Pay only for what you use.

## Rate Limits & Performance

- GitLab API rate limits: 10 requests/second for unauthenticated requests
- This Actor respects rate limits with automatic backoff
- Average extraction speed: ~30-60 projects/minute with details enabled
- Recommended maxResults: 50-100 for initial testing

## FAQ

**Q: Can I scrape private repositories?**
A: No, this Actor only extracts publicly available data from GitLab.

**Q: What happens if GitLab API is down?**
A: The Actor has built-in retry logic (3 attempts) and will gracefully handle temporary API failures.

**Q: Can I extract historical data?**
A: The Actor extracts current state data. For historical trends, run the Actor periodically and compare results.

## Limitations

- Public projects only (private repos require authentication not supported)
- GitLab.com only (self-hosted GitLab instances not supported)
- README extraction requires the project to have a README.md file
- Merge request counts may be limited by GitLab API pagination

## Support

Open an issue on this Actor's Apify page for questions, feature requests, or bug reports.

---

*Built for developers who need reliable GitLab intelligence at scale.*