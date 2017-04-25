# HTML Emails

### General:

- Even if a particular CSS property is not supported by all clients, you still may want to use it nonetheless. Therein, you'd make good-looking UI for clients that support that CSS and fallback for those that don't.

### Debugging:
- Generated emails have an `.eml` file extension. Rename the `.eml` file to `.mht` (which is a web page archive format). Now you can open the email/file in Firefox and use Dev Tools to inspect the content.


### Outlook/MS Mail/IE Gotchas:

- GMail on IE doesn't accept padding on `<table>` elements; use padding on `<td>` instead.

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
In the above code, we have a component (`<table>`) contained inside the `<td>` and subsequently, the container aligns/floats its contents to the right.

### Blue links and underlining for dates, telephone #s, and addresses:
- Mobile devices/clients detect address, phone, and date text and automatically highlight them as clickable links. This often overrides the carefully branded colors or causes readability issues.
- To prevent this from happening on mobile clients (especially on iOs), wrap the text inside an anchor tag (`<a href="#">`) and add override the font color and underlining:
```html
 <a href="#" class="footer-text" style="color: #999999 !important; text-decoration: none;">123 Gandhi Road, Bangalore</a>
```
