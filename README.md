PulseBlog — A single-file, client-side blog publishing web app

Summary
PulseBlog is a self-contained HTML file (index.html) that lets users publish blog posts in a Medium-like experience. It includes a Markdown-friendly editor with a live preview, a posts feed with like and delete actions, tag-based filtering, search, and local persistence via localStorage. Everything runs in the browser with no dependencies.

Key features
- Single-file deployment: All HTML, CSS, and JavaScript are in one file.
- Post composer: Title, content (Markdown supported), and tags.
- Live preview: Real-time Markdown preview beside the editor.
- Markdown conversion: Lightweight, safe Markdown to HTML renderer with headers, bold, italic, code, links, and basic lists.
- Feed with interactions:
  - Publish posts (persisted in localStorage)
  - Like posts (per-post like counter)
  - Read more / Show less toggle for long posts
  - Delete posts
- Tag filtering: Clickable tags to filter posts by tag.
- Search: Full-text search across titles, content, and tags.
- Local persistence: All posts are saved in localStorage and survive refreshes.
- Theme toggle: Light/Dark theme supported with persistence.
- Responsive layout: Two-column layout that stacks on small screens.

Setup and deployment
- Save as index.html
- Open directly in a modern browser (Chrome, Firefox, Edge, Safari)
- Optionally deploy to GitHub Pages:
  - Create a public repository
  - Commit index.html (and any assets) to main or gh-pages
  - In the repository settings, enable GitHub Pages from the main branch (root) or a /docs folder
  - Access your site at https://<username>.github.io/<repo>/

Usage
1) Publish a post
- Enter a title, write content in Markdown, add tags (comma-separated), and click Publish Post.
- Your post is saved to localStorage and appears in the feed immediately.
2) Preview
- Type in the editor; a live preview area shows the rendered Markdown to HTML.
3) Interact with posts
- Like: Click the Like button to increment the count.
- Read more / Show less: If content is long, toggle to expand or collapse the full content.
- Delete: Remove a post from the feed.
4) Filter and search
- Click any tag in a post to filter the feed to that tag.
- Use the search field to filter posts by text in title, content, or tags.
5) Theme
- Click Theme to toggle between light and dark themes. The choice persists in localStorage.

Technical details
- HTML structure
  - header.site-header: Brand and quick actions
  - main.container: Two-column layout
    - section.card.composer: Post composer (title input, content textarea, tags input, live preview, publish button)
    - section.card.feed: Feed with search, tag cloud, and posts list
  - footer: Simple footer
- CSS
  - Uses CSS variables for light/dark themes
  - Card-based UI with rounded corners, soft shadows, and responsive layout
  - Live preview area mirrors the editor content
- JavaScript (in-page)
  - Data model: Post object with id, title, content (markdown), tags, author, createdAt, likes, expanded
  - Persistence: LocalStorage under key pulse_blog_posts_v1
  - Markdown rendering: Lightweight mdToHtml function with header, bold, italic, code, links, and unordered lists
  - Rendering: renderPosts and renderTagCloud functions to build the feed and tag cloud
  - Event handling: Delegated events for publish, like, read more, delete, tag filter, and search
  - Utilities: timeAgo, parseTags, excerptFromMarkdown

Deployment info
- Recommended hosting: GitHub Pages (free, easy to deploy)
- Steps to deploy:
  - Push index.html to a GitHub repository
  - Enable GitHub Pages in repository settings (choose main branch or gh-pages)
  - Access the site at the generated Pages URL

License
- MIT License

Generated date
- 2025-11-05

Notes
- This app is designed to be a fast, self-contained demo. It stores data locally in the browser, so it won’t sync across devices. You can extend it by adding user accounts, multi-user editing, or syncing to a backend service if needed.