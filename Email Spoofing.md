[[ETHICAL-HACKING]]


Emails are sent using the SMTP-> simple mail transfer protocol.
-> does not have an authentication mechanism.
->phishing: sending an email to trick the user to changing their password immediately, the form for which will also require the old password, which will be saved in the hacker's list of stolen passwords. The site then will redirect to the legitimate website, so the user will not suspect anything.

## How to protect ourselves?

-   **Implement the Sender Policy Framework (SPF):** publish a [DNS record](https://www.cloudflare.com/learning/dns/dns-records/) to explicitly state which servers are allowed to send email from your domain.
-   **Implement Domain Key Identified Mail (DKIM):** use a [digital signature](https://www.hacksplaining.com/glossary/digital_signatures) to prove that outgoing email was legitimately sent from your domain, and that it wasn’t modified in transit.

Implementing SPF and DKIM requires publishing new DNS records and making configuration changes to your technology stack - consult the documentation for your email sending service or software for details.

##### Transactional Email Services

Transaction emails are sent programmatically in response to actions on a website or application. If your site makes use of transactional email (during sign-ups or password resets, for example) you need to ensure you are sending authenticated mails.

 ##### Email Marketing Services

Email marketing services allow bulk-sending of emails to targeted mailing lists.

##### Mail Transfer Agentsg

If you organization hosts its own email servers, your system administrators will be making use of “Mail Transfer Agent” software. The most common MTAs are Microsoft Exchange (on Windows) and SendMail/Postfix (on Linux).