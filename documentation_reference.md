Avalon Documentation Guide

## Alerts

This site supports 4 different kinds of alerts:
* Tip
* Note
* Important
* Warning

To include an alert within a page, copy and paste one of the following pairs of tags, and place your content between the tags:

Tip:
{{ site.data.alerts.tip}}
Your content here.
{{ site.data.alerts.end}}

Note:
{{ site.data.alerts.note}}
Your content here.
{{ site.data.alerts.end}}

Important:
{{ site.data.alerts.important}}
Your content here.
{{ site.data.alerts.end}}

Warning:
{{ site.data.alerts.warning}}
Your content here.
{{ site.data.alerts.end}}

### Code Blocks and Alerts

To put a code block within an alert, surround the code block with <pre> tags, as seen in the following example:

{{site.data.alerts.note}}
Your content here
<pre>
Your code block here
Your code block here
</pre>
{{site.data.alerts.end}}

### Images and Alerts

Images can be included into alerts the same way they are included into a page, using the include tag seen in the following example:

{{site.data.alerts.important}}
Your content here:
{% include yourimage.html file="image/path.png" alt="alt text" %}
More content here.
{{site.data.alerts.end}}

### Formatted Text and Alerts

Text within alerts will not be formatted according to the kramdown markup used elsewhere in the site. To format text, use html tags instead:

{{site.data.alerts.important}}
This is an example of <em>bold</em>, whereas this is an example of <i>italics</i>.
{{site.data.alerts.end}}