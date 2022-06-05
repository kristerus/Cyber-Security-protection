[[ETHICAL-HACKING]]

If an attacker can execute code in your servers, the website under your control is dead. Inserting malicious code, which then calls shell scripts to be executed is what is also known as command-execution, or shell-hacking.
To protect, try using as many APIs to solve your problems as possible, and **escape the characters which most likely will compromise your website in any case**.
Grouping them together, the main ones are these below:


;

&

|

`

What's more, try implementing a REGEX to check if the inputed value is "friendly".

Try to whitelist the commands whenever possible, so everything remains under your control. In NODE.JS the code would look like below:

The usual way of invoking shell commands in Node is using the [`child_process`](https://nodejs.org/api/child_process.html) module.
```javascript
child_process.execFile('/bin/ls', ['-l', input_path], function (err, result) {
  console.log(result)
});
```
```javascript
var ls = child_process.spawn('/bin/ls', ['-l', input_path])
```