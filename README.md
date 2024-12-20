# Book Keeper

This project is a responsive web application built as part of the course "JavaScript Web Projects: 20 Projects to Build Your Portfolio" by Zero To Mastery. The application allows users to save, view, and manage bookmarks with ease.

## Table of contents

- [Book Keeper](#book-keeper)
  - [Table of contents](#table-of-contents)
  - [Overview](#overview)
    - [Screenshot](#screenshot)
    - [Links](#links)
    - [Features](#features)
    - [Built with](#built-with)
    - [What I learned](#what-i-learned)
    - [Useful resources](#useful-resources)
  - [Author](#author)
  - [Acknowledgments](#acknowledgments)

## Overview

The Book Keeper app provides an easy-to-use interface for managing bookmarks, making it a practical tool for organizing frequently visited websites.

This project includes the following features:
- A modal for adding bookmarks with fields for website name and URL.
- Validation to ensure correct input before saving.
- Display of all saved bookmarks, including their favicon.
- The ability to delete bookmarks dynamically.
- Persistent data storage using localStorage to retain bookmarks across sessions.

### Screenshot

![](./screenshot.png)

### Links

- Live Site URL: [DT Code](https://book-keeper.dtcode.se/)

### Features

- Add Bookmarks: Users can input a website name and URL to save bookmarks.
- Bookmark Validation: Ensures URLs are valid before saving.
- Favicon Integration: Displays a favicon for each saved website.
- Bookmark Management: Allows users to delete individual bookmarks.
- Persistent Data: Stores bookmarks using localStorage for data retention across sessions.
- Responsive Design: Adapts seamlessly to various screen sizes.

### Built with

- HTML5: For semantic structure.
- CSS3: For responsive styling and layout.
  - CSS Variables for consistent theming.
  - Flexbox for responsive layout management.
- JavaScript (ES6+): For interactivity and functionality.
  - DOM manipulation for dynamic updates.
  - Event handling for user interactions.
  - Validation using regular expressions.
  - localStorage for persistent data storage.

### What I learned

In this project, I learned:
- Enhancing user experience by creating a modal and managing interactive elements with JavaScript.
- Validating user input with regular expressions for robust and accurate URL handling.
- Effectively managing state and dynamic UI updates using arrays and localStorage.

Example code for validation and adding bookmarks:

```js
function validate(nameValue, urlValue) {
    const expression = /https?:\/\/(www\.)?[-a-zA-Z0-9@:%._\+~#=]{1,256}\.[a-zA-Z0-9()]{1,6}\b([-a-zA-Z0-9()@:%_\+.~#?&//=]*)/g;
    const regex = new RegExp(expression);
    if (!nameValue || !urlValue) {
        alert('Please submit values for both fields.');
        return false;
    }
    if (!urlValue.match(regex)) {
        alert('Please provide a valid web address.');
        return false;
    }
    return true;
}

function storeBookmark(e) {
    e.preventDefault();
    const nameValue = websiteNameEl.value;
    let urlValue = websiteUrlEl.value;
    if (!urlValue.includes('http://', 'https://')) {
        urlValue = `https://${urlValue}`;
    }
    if (!validate(nameValue, urlValue)) {
        return false;
    }
    const bookmark = { name: nameValue, url: urlValue };
    bookmarks.push(bookmark);
    localStorage.setItem('bookmarks', JSON.stringify(bookmarks));
    fetchBookmarks();
    bookmarkForm.reset();
    websiteNameEl.focus();
}
```

### Useful resources

- [MDN Web Docs: LocalStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage) - Helped with understanding and implementing persistent storage for bookmarks.
- [MDN Web Docs: RegExp](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions) - Assisted in creating a regular expression for validating URLs.
- [Font Awesome](https://fontawesome.com/) - Used for icons, including the modal close icon and delete buttons.

## Author

- GitHub - [@dantvi](https://github.com/dantvi)
- LinkedIn - [@danieltving](https://www.linkedin.com/in/danieltving/)

## Acknowledgments

Special thanks to Zero To Mastery for providing the guidance and course material for this project. This project was instrumental in honing skills related to DOM manipulation, localStorage, and interactive UI design.
