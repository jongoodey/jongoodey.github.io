Built a Chrome extension that speeds up webpage analysis with AI a bit.

Here's what it does: takes a screenshot of an entire webpage (including the bits below the fold), then automatically uploads it to Claude or ChatGPT. That's it really.

You click the extension, choose full page or just the visible bit, it scrolls through capturing everything, stitches it together, then opens your AI of choice with the image already uploaded. Takes about 30 seconds instead of the usual faff of taking multiple screenshots and uploading manually.

The bit I'm finding most useful - it stores all your screenshots so you can quickly flip between different sites. Been using it to jump between Search Console and Analytics screenshots to get the full picture without having multiple tabs open. Just scroll through your captures and compare data side by side.

Works on those annoying sites like LinkedIn that normally block automated scrolling. Got retry logic for when uploads fail, which they do sometimes.

Been using it for quick content audits and competitor analysis. Rather than copying text or taking notes, I just capture the whole page and ask Claude to pull out what I need.

Nothing revolutionary, just saves a bit of time if you're regularly throwing webpages at AI for analysis.

[Video to show how it works](https://www.linkedin.com/posts/marketing-intelligence_i-have-just-built-a-chrome-extension-that-activity-7354446458449735681-lUOw)

What tedious tasks are you still doing manually that could probably be automated?

---
# **What the Extension Actually Does**

**Core Function:**
Takes full-page screenshots of websites (including content below the fold) and automatically uploads them to Claude or ChatGPT for analysis.

**How it works:**
1. You click the extension icon on any webpage
2. Choose "Full Page" or "Visible Area" capture
3. For full page: it automatically scrolls down the page in segments, taking screenshots of each section
4. Stitches all the segments together into one complete image
5. Click "Analyze with Claude" or "Analyze with ChatGPT" 
6. Opens the AI service in a new tab and uploads the screenshot automatically
7. You can add your own prompt/questions about the image

**Technical details:**
- Handles very long pages (thousands of pixels tall)
- Works on complex sites like LinkedIn that usually prevent programmatic scrolling
- Shows real-time progress indicators during capture
- Has retry logic for failed uploads
- Captures multiple segments with overlapping regions to ensure no content is missed

**End result:**
Instead of manually taking screenshots, cropping, uploading to AI services, you get the entire webpage analyzed by AI in about 30 seconds with minimal clicks.

That's it. It's basically automated screenshot + AI upload for web analysis.