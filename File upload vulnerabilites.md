[[ETHICAL-HACKING]]

**File uploads represent an easy way for an attacker to inject malicious code into your application.**
**Sophisticated hackers typically exploit a combination of vulnerabilities when attacking your site – uploading malicious code to a server is step one in the hacker playbook.** The next step is finding a way to execute the malicious code.

Even [big companies](https://threatpost.com/ebay-fixes-file-upload-and-patch-disclosure-bugs/111898) fall foul to this vulnerability, particularly if they are running complex, legacy code bases.



Any input coming from a user ought to be treated with suspicion until it has been guaranteed to be safe. This is particularly true of uploaded files, because your application will typically treat them as a big blob of data at first, allowing an attacker to smuggle any kind of malicious code they desire onto your system.
Consider using [cloud-based storage](http://aws.amazon.com/s3/) or a [content management system ](https://www.hacksplaining.com/glossary/content-management-systems)(CMS) to store uploaded files. Alternatively, if you are sure of your ability to scale your backend, you could write uploaded files to your database. Both of these approaches prevent accidental execution of an executable file.

1. ###### Ensure Upload Files Cannot Be Executed
However you end up storing your uploaded files, if they are written to disk, ensure they are written in such a way that the operating system knows not to treat them as executable code. Your web server process should have read and write permissions on the directories used to store uploaded content, but should _not_ be able to execute any files there. If you are using a Unix-based operating system, make sure uploaded files are written without the “executable” flag in the file permissions.
2. ###### Rename Files on Upload 
 Implement a method of indirection when serving the uploaded content back in the browser, so the content is not referenced by its name from the original upload.
3. ###### Validate File Formats and Extensions
4. ###### Validate the Content-Type Header
5. ###### Use a Virus Scanner
6. ###### Check File Sizes
A cheap and easy way to perform a [denial-of-service](https://www.hacksplaining.com/glossary/denial-of-service-attacks) attack is to upload a very large file, in the hope that the server runs out of space. Make sure you put a maximum size on the size of the files you accept.
7. ###### Caution towards Compressed Files


