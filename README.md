# Template for CodeRefinery workshop webpages

This repository is a template to set up webpages for CodeRefinery workshops.


### Schedule planning

**Host:** Manage zoom meeting, breakout rooms, timekeeping and breaks,
zoom chat, general attendee communication.  **Hackmd:** watches
hackmd, answers questions, organizes it, brings questions up in main
lecture.  **Expert helpers:** Reserve instructors who can help with
difficult problems, especially configuration problems at the very
beginning of each day.  **Helper:** breakout room helper, listed at
end (not per day) since they are usually expected to be a helper every
day. **(name)** in parentheses: "I offer to do it
but I am happy if someone replaces me here."

Overlapping roles are allowed when you think it's reasonable!


<table>
<tr>
  <th>Day</th>
         <th>Topics+Instructors</th>
         <th>Host</th>
         <th>Hackmd</th>
         <th>Experts helpers</th>
</tr>
<tr>
  <th>18.may (M)</th>
         <td>intro: <br>
		     reproducible-research: <br>
		     social-coding: <br>
	     </td>
         <td></td><!--host-->
         <td></td><!--hackmd-->
         <td></td><!--expert helpers-->
</tr>
<tr>
  <th>19.may (T)</th>
         <td>documentation: <br>
		     jupyter: <br>
	     </td>
         <td></td><!--host-->
         <td></td><!--hackmd-->
         <td></td><!--expert helpers-->
</tr>
<tr>
  <th>20.may (W)</th>
         <td>testing: <br>
		     modular code development: <br>
		     outro: <br>
	     </td>
         <td></td><!--host-->
         <td></td><!--hackmd-->
         <td></td><!--expert helpers-->
</tr>
</table>

Helpers: name, name.  (note: for privacy, helpers do not need to be
tracked here and can be recorded elsewhere)


## How to use this template

To use it, follow these instructions:
- Click the green "Use this template" button.
- Select owner of the new repository and repository name. The name should be
  "year-month-date-place", e.g. "2019-10-16-stockholm".
- Click "Create repository from template"
- You will now be redirected to the new repository.

Adjust these files:
- `title.md`
- `left-column.md`
- `right-column.md`


### Changing the status of the registration button

Registration is not yet open:
```html
<a class="btn btn-info disabled" href="#" data-mode="1" target="_blank">Registration will open soon</a>
```

Registration is open (adjust the `href`):
```html
<a class="btn btn-success" href="#" data-mode="1" target="_blank">Register here</a>
```

Registration is closed:
```html
<a class="btn btn-danger disabled" href="#" data-mode="1" target="_blank">Registration is closed</a>
```
