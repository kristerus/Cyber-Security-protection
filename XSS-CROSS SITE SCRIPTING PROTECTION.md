[[ETHICAL-HACKING]]
**Cross-site scripting** (XSS) is one of the most common methods hackers use to attack websites. XSS vulnerabilities permit a malicious user to execute arbitrary chunks of JavaScript when other users visit your site.

**XSS is the most common publicly reported security vulnerability, and part of every hacker’s toolkit.

To protect the website, we must escape any characters, with the HTML entity encoding as below:
" &#34

/# &#35

& &#38

' &#39

( &#40

) &#41

/ &#47

; &#59

< &#60
>&#62

#### Most modern browsers escape the input by default
A method worth giving a shot is implementing a content-security policy, mainly using this meta tag:
```xml
<meta http-equiv="Content-Security-Policy" content="script-src 'self' https://apis.google.com">
```


##### You need to make sure to avoid inline JavaScript execution!!
In ReactJS all the code in curly braces will be immediately escaped, and it can also be bound with `dangerouslySetInnerHTML` property, which is named to remind you of the security risk. Any code as below is considered dangerous:
```react
render() {
  return <div dangerouslySetInnerHTML={ __html: dynamicContent } />
}
```

A common practice, is to also make HTTP-Cookies only modified and stored in the browser and not accessible by outter JS commands.
