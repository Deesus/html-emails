# HTML Emails

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

