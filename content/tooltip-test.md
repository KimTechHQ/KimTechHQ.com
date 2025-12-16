---
title: "Tooltip Test"
date: 2025-12-10T12:00:00Z
draft: false
---

This page tests the `tooltip` shortcode. Hover over underlined words to see definitions.

<style>
.hb-tooltip {
  position: relative;
  display: inline;
  cursor: help;
  border-bottom: 1px dotted currentColor;
}

.hb-tooltip .hb-tooltip-text {
  position: absolute;
  left: 50%;
  transform: translateX(-50%) translateY(-6px);
  bottom: 100%;
  margin-bottom: 0.4rem;
  background: rgba(0, 0, 0, 0.88);
  color: #fff;
  padding: 0.4rem 0.6rem;
  border-radius: 0.35rem;
  font-size: 1.05rem;
  line-height: 1.2;
  white-space: nowrap;
  z-index: 99999;
  opacity: 0;
  visibility: hidden;
  transition: opacity 0.12s ease, visibility 0.12s ease;
  pointer-events: none;
  box-shadow: 0 6px 18px rgba(0, 0, 0, 0.25);
}

.hb-tooltip .hb-tooltip-text::after {
  content: '';
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  top: 100%;
  border: 6px solid transparent;
  border-top-color: rgba(0, 0, 0, 0.88);
}

.hb-tooltip:hover .hb-tooltip-text,
.hb-tooltip:focus-within .hb-tooltip-text {
  opacity: 1;
  visibility: visible;
}
</style>

Inline example:

<span class="hb-tooltip" tabindex="0">DNSSEC<span class="hb-tooltip-text">DNS Security Extensions that prevent spoofing.</span></span>

Markdown-processed inner content:

<span class="hb-tooltip" tabindex="0">**HTML**<span class="hb-tooltip-text">Hypertext Markup Language.</span></span>

Another example:

<span class="hb-tooltip" tabindex="0">Definition<span class="hb-tooltip-text">A short explanation about tooltips.</span></span>

Long content with punctuation:

<span class="hb-tooltip" tabindex="0">LongDef<span class="hb-tooltip-text">This definition contains "quotes" and a longer explanation so you can see wrapping behavior.</span></span>

End of test.
