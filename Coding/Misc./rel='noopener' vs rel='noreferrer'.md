`rel="noopener"`: This attribute is used to prevent the newly opened page from having access to the window.opener property of the opening page. This property provides a reference to the window or tab that opened the current page. By adding `rel="noopener"`, you ensure that the opened page cannot manipulate or access the properties and methods of the opening page. This attribute helps protect against certain types of cross-site scripting (XSS) attacks.

`rel="noreferrer"`: This attribute, in addition to preventing access to the window.opener property, also prevents the Referer header from being sent to the newly opened page. The Referer header is typically sent by the browser and contains the URL of the page that referred the user to the current page. By using `rel="noreferrer"`, you prevent the newly opened page from knowing the URL of the page that the user came from. This can provide an additional layer of privacy and security.

## Summary
- `rel='noopener'` prevents the newly opened page from having access to the window object of the original page.
- `rel='noreferrer'` implicitly adds `rel='noopener'` behavior, additionally it prevents the `referer` header from being sent. 
- `target='_blank'` also implicitly adds `rel='noopener'` behavior.
