[[ETHICAL-HACKING]]

**Clickjacking** attacks trick web users into performing an action they did not intend, typically by rendering an invisible page element on top of the action the user thinks they are performing.
The invisible element contains a link which then delegates the user in the website the hacker wants them to be.

To ensure that your site doesn’t get used in a clickjacking attack, you need to make sure it cannot be wrapped in an iframe by a malicious site. This can be done by giving the browser instructions directly via **HTTP headers**, or in older browser by using client-side JavaScript (**frame-killing**).


###### X-Frame-Options

The `X-Frame-Options` [HTTP header](https://www.hacksplaining.com/glossary/http) can be used to indicate whether or not a browser should be allowed to render a page in a `<frame>`, `<iframe>` or `<object>` tag. It was designed specifically to help protect against clickjacking.

There are three permitted values for the header:

DENY

The page cannot be displayed in a frame, regardless of the site attempting to do so.

SAMEORIGIN

The page can only be displayed in a frame on the same origin as the page itself.

ALLOW-FROM *uri*

The page can only be displayed in a frame on the specified origins.

###### Frame-Killing

In older browsers, the most common way to protect users against clickjacking was to include a frame-killing JavaScript snippet in pages to prevent them being included in foreign iframes:

```html
<style>
  /* Hide page by default */
  html { display : none; }
</style>

<script>
  if (self == top) {
    // Everything checks out, show the page.
    document.documentElement.style.display = 'block';
  } else {
    // Break out of the frame.
    top.location = self.location;
  }
</script>
```

**An example frame-killing script:** when the page loads, this code will check that the domain of the page matches the domain of the browser window, which will _not_ be true when the page is embedded in an iframe.

Most sites don’t need to be embedded in iframes, so a frame-killing script is easy to implement. If embedding _is_ required in your application, consider adding a whitelist of domains, so you have control over where your content is embedded.

Frame-killing offers a large degree of protection against clickjacking, but it can be error-prone. Be sure to set appropriate HTTP headers as the first recourse in protecting your site.


```javascript

response.setHeader("X-Frame-Options", "DENY");
response.setHeader("Content-Security-Policy", "frame-ancestors 'none'");
```
//framekilling in Node.