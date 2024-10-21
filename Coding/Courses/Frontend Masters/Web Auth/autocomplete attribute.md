The _autocomplete_ attribute is mainly to help password managers and browsers to automatically fill in inputs.
```html
<!-- register form -->
<input type='password' autocomplete='new-password' />
<!-- login form -->
<input type='password' autocomplete='current-password' />
<!-- if email is used as id -->
<input type='email' autocomplete='username' />

<input type='text' autocomplete='given-name'/>
<input type='text' autocomplete='family-name' />
```