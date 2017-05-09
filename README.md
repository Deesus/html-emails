# HTML Emails

### General:

#### Compatibility Issues:
- HTML/CSS standards are inconsistently supported across email clients.
- Clients will strip certain elements from your emails -- e.g.`<head>` tags and a myriad of CSS attributes.
- All email clients strip away all JavaScript from emails (this is for security reasons).
- Factors that affect HTML email UI are multivariable:
	1. the device (iPhone 6, iPhone 4, desktop, etc.)
	2. the email client (Gmail, Outlook, Thunderbird, Gmail app for Android, etc.)
	3. if accessing the email via web browser, then the specific browser (Firefox, Chrome, Edge, IE, etc.)
	3. the specific version of said client (Outlook 2016, Outlook 2013)
	4. the OS that the email is being accessed from (Windows 7, Windows 10, MacOS)
	
	Therefore, an email on Gmail app for iPhone 6 has idiosyncrasies indiscernible on another combination.

#### Development Strategy:
- Because email CSS support is poor, you cannot rely on advanced, and in many cases, even basic CSS attributes.
- Use HTML tables, not divs (divs are not reliable).
- Even if a particular CSS property is not supported by all clients, you still may want to use it nonetheless. Perhaps you'd want to create the best-looking UI for your target email clients (which support that specific CSS property) and create fallback UI for the less-important email clients (those that don't support specific property).

### Debugging:
- Generated emails have an `.eml` file extension. Rename the `.eml` file to `.mht` (which is a web page archive format). Now you can open the email/file in Firefox and use DevTools to inspect the content.
	- If will not be able to access DevTools if you are converting your emails to base64 encoding (e.g. for multipart emails); you will need to temporarily comment out the server-side logic does this extraneous encoding.
- You can test `.eml` files on different browsers and use DevTools another way: 
	1. Set up a desktop email client (e.g. Thunderbird) and connect to a browser-based account (e.g. Gmail). 
	2. Place the `.eml` file in your inbox. In Thunderbird, you would drag the file to the inbox.
	3. Open the browser you want to test the `.eml` file and log in to your account. You should see your `.eml` email in your inbox (in your browser)----if not, refresh your inbox.
	4. You now open that email and open up DevTools to inspect and debug.
	
- Use an email testing service. They allow you to test every combination of email/device/OS/client. These services charge monthly subscription fees, but will save you a lot of hassle, headache, time, and money. 

### Outlook/MS Mail/IE Gotchas:

- `width` and `height` attributes are not supported by MS email clients.

- Gmail on IE doesn't accept padding on `<table>` elements; use padding on `<td>` instead.

- Outlook doesn't support float; in order to 'float' items, use the `align` *element* attribute. For example:
```html
<tr>
  <td align="right"> 
    <table class="component" width="65px" cellpadding="0" cellspacing="0">
	  ....
    </table>
  </td>
</tr>
```
In the above code, we have a component `<table>` contained inside the `<td>` and subsequently, the container aligns/floats its contents to the right.

### Blue links and underlining for dates, telephone #s, and addresses:
- Mobile devices/clients detect address, phone, and date text and automatically highlight them as clickable links. This often overrides the carefully branded colors or causes readability issues.
- To prevent this from happening on mobile clients (especially on iOs), wrap the text inside an anchor tag `<a href="#">` and add override the font `color` and `text-decoration`:
```html
 <a href="#" style="color: #999 !important; text-decoration: none;">123 Gandhi Rd, Bangalore</a>
```

### Misc.

- CSS shorthand values seem to work fine in most cases (e.g. `color: #fff` or `border: 1px solid red`).