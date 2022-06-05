[[ETHICAL-HACKING]]

### The concept of OPEN REDIRECT
An open redirect is where your application redirects the user to a URL supplied from an unstrustworthy source, without checking the validity of the URL. 
Users are tricked in frequenting a malicious link or website of the phishers choice.
The trust the users have in your website or product is damaged and thereby, the number of visitors drops.
Can happen when clicking a normal link or after the redirection after authentication if the website URL is not checked.

To prevent:
###### Disallow Offsite Redirects
Make sure all redirect URLs are **relative paths** – i.e. they start with a single `/` character. (Note that URLs starting with `//` will be interpreted by the browser as a protocol agnostic, absolute URL – so they should be rejected too.)
If you _do_ need to perform external redirects, consider whitelisting the individual sites that you permit redirects to.

#### Check the Referrer When Doing Redirects
Redirects to URLs passed in query parameters should only be triggered by pages on your site. Any other sites triggering a redirect should be treated with extreme suspicion.
#### As a second layer of defense, check that the Referer in the HTTP request matches your domain whenever you perform a redirect.

The code in NodeJS.
```javascript

function isRelative(url) {
  return url && url.match(/^\/[^\/\\]/);
}
```

#regex

Redirects can happen in client-side JavaScript, too! Validate any code that sets `window.location`, to ensure the URL is not taken from untrusted input.
###### Interstitial Pages
Some sites insert interstitial pages when the user is leaving the site – **“you are now leaving tinyrobotninjas.com, you will be automatically redirected in 5 seconds”.** This is a good defense against doppelganger domains – websites that have a very similar domain name, in order to trick the user into trusting them. If you implement an interstitial page that passes the URL in the query parameter, be sure to check the `Referer` header, or else they could be open to abuse.

###### Aggregator Sites
Aggregator sites often make use of redirects to do click-counting. URLs are chosen by the community, then when a user clicks on the link, the click-through count is incremented, and the user is redirected to their destination. If your site implements this type of functionality, redirects to external sites are part of doing business. Just be sure to check the `Referer` each time you do a redirect!





