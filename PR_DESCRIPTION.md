# Objective

Images nested inside markdown links (e.g. `[![alt](img.png)](url)`) were not
clickable — clicking the image did nothing. This made linked images in rendered
markdown unusable.

## Solution

When rendering an image inside a link context (detected via
`builder.link_depth > 0`), wrap it in a clickable `div` with `cursor_pointer`
and an `on_click` handler that opens the link's destination URL.

## Testing

Manually verified in the markdown preview: clicking a linked image now opens the
link. Tested with both linked and non-linked images to ensure no regression.
Non-linked images are unaffected — the check is a simple boolean read with no
allocations.

## Self-Review Checklist:

- [ ] I've reviewed my own diff for quality, security, and reliability
- [ ] Unsafe blocks (if any) have justifying comments
- [ ] The content adheres to Zed's UI standards
- [ ] Tests cover the new/changed behavior
- [ ] Performance impact has been considered and is acceptable

---

Release Notes:

- Fixed images nested inside markdown links are now clickable
