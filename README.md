# Watch Monitor Fixture

This is a small static site for comparing Watch and Firecrawl Monitor.

## Publish with GitHub Pages

1. Create a new GitHub repository, for example `watch-monitor-fixture`.
2. Upload `index.html` to the repository root and commit it to `main`.
3. Open **Settings -> Pages**.
4. Select **Deploy from a branch**, branch `main`, folder `/ (root)`, then save.
5. Use the published URL as the monitor target, for example `https://USER.github.io/watch-monitor-fixture/`.

GitHub Pages may take several minutes to publish a commit. Verify the new content in an incognito window before triggering a monitor Check.

## Suggested Watch jobs

- Full page: omit `selector`.
- Headline: `.headline`.
- All story titles: `.story .title`.
- One story: `.story[data-story-id="story-1"] .title`.
- Scores: `.story .score`.
- Noise: `.noise`.
- Selector error: `.watch-test-not-found`.

## Repeatable manual changes

Change only one item per commit, then wait for the published page to update:

- Change `Monitor target headline A` to `Monitor target headline B`.
- Change one story title.
- Reorder or add/remove a `.story` article.
- Change only a score or comment count.
- Change only the `#noise` timestamp.
- Delete the `.headline` element to test a selector miss.
- Restore the previous content to test a rollback.

Keep the public URL stable. Do not add cache-busting query parameters to the monitor URL; record the commit SHA and publish time in the test log instead.

## Nimble Map URL discovery tests

The fixture contains three URL-discovery cases. All three test pages are intentionally absent from `sitemap.xml`:

- `fresh-html-20260921-a7f3.html` is a normal HTML link from the homepage. It tests page-link discovery with `sitemap=skip`.
- `js-only-20260921-c44e.html` is inserted by JavaScript after page load. It tests whether the mapper evaluates rendered links.
- `orphan-20260921-b91c.html` is not linked from any page. It tests whether a mapper returns URLs from a source other than the current page graph.

Use `domain_filter=domain` so the external `example.com` control link is excluded. For cache-sensitive tests, replace the path token (`20260921-a7f3`, etc.) with a new value on every run instead of adding only a query string. After pushing a commit, wait at least 10-15 minutes for GitHub Pages and its CDN to publish the change, then verify the homepage and each new page directly before calling Map.
