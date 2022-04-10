# Display & Create Pages

Implemented via Vue.js 3.

This App is responsible for displaying pages and creating new ones.

## Display Pages:

The main screen displays data table of all the pages.
There are 3 fields: Pages, Template & Created At.

The Pages field is the url of the page. the Data is a hyperlink. When clicking on it,
a new tab will open and the page name will be part of the url with query param: mode=edit.
for example: ".../[page name]?mode=edit"

For now, The only Template type for pages is "blog".

## Create Pages:

On the top right, there is an "+" button. This will allow creating a new page.
Upon clicking the button, A popup will apear. The popup is a form. The fields are
url (page url), locale & Template.

Upon filling the fields and clicking "Create", the new page will be added
to the list of pages.

Right now, The list of pages are stored on local storage
only. In the future, The data will be sent to the backend.
