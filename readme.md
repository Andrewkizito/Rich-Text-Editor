# React Quill Editor

This is a simple React application that uses the `react-quill` library to render a rich text editor with image upload functionality. The editor allows you to format text, add headers, create lists, insert images, and more.

## Installation

To run this application locally, follow these steps:

1. Clone the repository: `git clone <repository-url>`
2. Navigate to the project directory: `cd react-quill-editor`
3. Install the dependencies: `npm install`

## Usage

Once the dependencies are installed, you can start the development server:

```bash
npm start
```

This will start the application on `http://localhost:3000` and open it in your default browser. You will see a form with a text editor and a submit button.

## Features

- Text formatting options such as bold, italic, underline, and blockquote.
- Headers: Choose from header levels 2, 3, and 4.
- Text color selection.
- Lists: Create ordered and bullet lists.
- Indentation: Increase or decrease the indentation level.
- Insert hyperlinks and images.
- Remove formatting option.
- Image upload functionality: Click the image button to select an image from your device and insert it into the editor.

## Implementation Details

The main component of the application is `Editor.js`. It utilizes the `react-quill` library to render the editor and handle user interactions. The component structure and key implementation details are as follows:

### Importing Dependencies

The required dependencies and styles are imported at the beginning of the file:

```jsx
import { useCallback, useMemo, useRef, useState } from "react";
import QuillEditor from "react-quill";
import "react-quill/dist/quill.snow.css";
import styles from "./styles.module.css";
```

### Component Function

The main component function is defined as `Editor`:

```jsx
const Editor = () => {
  // Editor state
  const [value, setValue] = useState("");

  // Editor ref
  const quill = useRef();

  // Handler to handle button clicked
  function handler() {
    console.log(value);
  }

  // Image handler function
  const imageHandler = useCallback(() => {
    // Image handling logic
  }, []);

  // Quill modules configuration
  const modules = useMemo(
    () => ({
      // Toolbar configuration
      toolbar: {
        container: [
          // Specify toolbar options
        ],
        handlers: {
          image: imageHandler,
        },
      },
      clipboard: {
        matchVisual: true,
      },
    }),
    [imageHandler]
  );

  // Quill formats configuration
  const formats = [
    // Specify formats
  ];

  return (
    // JSX code for rendering the editor
  );
};

export default Editor;
```

### State and Ref

The component state is managed using the `useState` hook. The `value` state stores the current content of the editor. The `setValue` function is used to update the state.

The `quill` ref is used to reference the Quill editor instance.

### Image Handler

The `imageHandler` function is defined using the `useCallback` hook. This function handles the image upload functionality. It creates an input element, sets the necessary attributes, triggers a click event to open the file picker, and handles the selected image file. It then reads the file as a data URL and inserts the image into the editor at the current cursor position.

### Quill Modules and Formats

The `modules` configuration object is defined using the `useMemo` hook. It specifies the toolbar options and their configuration. The `image` button has a custom handler assigned to it, which is the `imageHandler