# HTML Emails

### General:

#### Compatibility Issues:
- HTML/CSS standards are inconsistently supported across email clients.
- All email clients strip away all JavaScript from emails (this is for security reasons).
- Even if a particular CSS property is not supported by all clients, you still may want to use it nonetheless. You would, therefore, make the best-looking UI for email clients that support that CSS and fallback for those that don't.

#### Development Strategy:
- Because email CSS support is poor, you cannot rely on advanced, and in many cases, even basic CSS attributes.
- Use HTML tables, not divs (divs are not reliable).

### Debugging:
- Generated emails have an `.eml` file extension. Rename the `.eml` file to `.mht` (which is a web page archive format). Now you can open the email/file in Firefox and use Dev Tools to inspect the content.


### Outlook/MS Mail/IE Gotchas:

- `width` and `height` attributes are not supported by MS email clients.

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
In the above code, we have a component `<table>` contained inside the `<td>` and subsequently, the container aligns/floats its contents to the right.

### Blue links and underlining for dates, telephone #s, and addresses:
- Mobile devices/clients detect address, phone, and date text and automatically highlight them as clickable links. This often overrides the carefully branded colors or causes readability issues.
- To prevent this from happening on mobile clients (especially on iOs), wrap the text inside an anchor tag `<a href="#">` and add override the font `color` and `text-decoration`:
```html
 <a href="#" style="color: #999 !important; text-decoration: none;">123 Gandhi Rd, Bangalore</a>
```
