# Browser Tab Reuse

Intelligent browser tab management: reuse existing tabs instead of opening new ones.

## Usage

Before opening a URL, check if a tab with the same domain exists:

```bash
# Get all tabs
browser action=tabs

# If domain matches, focus existing tab
browser action=focus targetId=xxx

# Otherwise open new tab
browser action=open targetUrl=https://example.com
```

## Workflow

1. Use `browser action=tabs` to get current tab list
2. Extract domain from target URL
3. Compare with existing tabs' URLs
4. Match found → switch to that tab
5. No match → create new tab

## Example

User says "open Xiaohongshu":
1. Get all tabs
2. Check if xiaohongshu.com tab exists
3. Yes → focus that tab
4. No → create new tab

## Notes

- Only create new tab for cross-domain cases
- Same domain tabs are reused
- Supports fuzzy matching (baidu.com matches news.baidu.com)
