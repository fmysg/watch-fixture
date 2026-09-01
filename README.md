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
