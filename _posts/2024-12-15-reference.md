---
title:  "Post Reference"
excerpt: "포스트 작성을 위한 참고자료"
categories:
    - Markdown

last_modified_at: 2024-12-15T16:20:02-05:00
---

## Post 참고 자료

- [x] Finish my changes
- [ ] Push my commits to GitHub

```css
-ms-word-wrap: break-word;
word-wrap: break-word;
```

```ruby
str = ARGV.first
if str
  str = str.b[/\A_(.*)_\z/, 1]
  if str and Gem::Version.correct?(str)
    version = str
    ARGV.shift
  end
end
```