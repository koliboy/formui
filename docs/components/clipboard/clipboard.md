### Component: Clipboard

This component provides examples of how to use the clipboard functionality with different target elements.

**Note Regarding Clipboard Feature:**

Please note that clipboard functionality is only available in secure contexts (HTTPS) and may vary in support across different browsers. Ensure your website is served over HTTPS to utilize this feature reliably. Always provide alternative methods for users if clipboard operations are not supported in their browser environment.



1. **Simple Usage**
   ```html
   <button class="button clip-b" clip-b-d="Copy Text"></button>
   <!-- This button copies the text "Copy Text" when clicked. -->
   ```

2. **Target Element Usage**
   - Example with input element:
     ```html
     <input class="input" value="Copy Text">
     <button class="button clip-b" clip-b-t=".input"></button>
     <!-- This button copies the value of the input element with the class "input" when clicked. -->
     ```

   - Example with div element:
     ```html
     <div class="brave">HELLO 👋</div>
     <button class="button clip-b" clip-b-t=".brave" clip-b-v="textContent"></button>
     <!-- This button copies the text content of the div element with the class "brave" when clicked. -->
     ```

   - Supported values for `clip-b-v` attribute:
     - `textContent`
     - `value`
     - `innerHTML`

3. **Each Target Element with Index**
   - Example with code elements:

```html
     <pre type="html"><code>
        <h1>code 1</h1>
     </code></pre>
     <button class="button clip-b" clip-b-t="code" clip-b-e="index" clip-b-v="innerHTML"></button>
     <!-- This button copies the inner HTML of the code element corresponding to its index when clicked. -->
   
     <pre type="html"><code>
        <h1>code 2</h1>
     </code></pre>
     <button class="button clip-b" clip-b-t="code" clip-b-e="index" clip-b-v="innerHTML"></button>
     <!-- This button copies the inner HTML of the next code element corresponding to its index when clicked. -->
   
<pre type="html"><code>
        <h1>code 3</h1>
     </code></pre>
     <button class="button clip-b" clip-b-t="code" clip-b-e="index" clip-b-v="innerHTML"></button>
     <!-- This button copies the inner HTML of the next code element corresponding to its index when clicked. -->
```

   - The `clip-b-e="index"` attribute ensures that each button follows the index of its corresponding code element.

#### Note
- Ensure that the necessary class names and attributes are correctly set on the target elements for the clipboard functionality to work as expected.
- Test the functionality thoroughly across different browsers to ensure compatibility.

## **`clip-b` Class**

The `clip-b` class is a fundamental component of the clipboard functionality within HTML documents. It enables the creation of buttons that, when clicked, facilitate the copying of specified text content to the clipboard. This class acts as a marker for identifying elements that trigger clipboard operations.

### Syntax:
```html
<button class="button clip-b"></button>
```

### Attributes:
- `class="clip-b"`: Assigns the clipboard behavior to the HTML element. When combined with other attributes and event listeners, it facilitates the copying of text content to the clipboard.

### Usage:
- **Simple Clipboard Button**: Incorporating the `clip-b` class into a button element instantly provides clipboard functionality. For instance:
  ```html
  <button class="button clip-b" clip-b-d="Copy Text"></button>
  ```
  This button, when clicked, will copy the text "Copy Text" to the clipboard.

- **Customized Clipboard Behavior**: The `clip-b` class can be augmented with additional attributes to specify the text content to be copied and the target element(s) from which the text will be copied. For example:
  ```html
  <button class="button clip-b" clip-b-t=".target-element" clip-b-v="textContent"></button>
  ```
  This button will copy the text content of the element with the class `target-element` when clicked.

## **`clip-b-d` Attribute**

The `clip-b-d` attribute is utilized in conjunction with the `clip-b` class to specify the data to be copied to the clipboard when the associated button is clicked. This attribute allows developers to define the content directly within the HTML markup, simplifying the implementation of basic clipboard functionality without the need for additional scripting.

### Syntax:
```html
<button class="button clip-b" clip-b-d="data"></button>
```

### Attributes:
- `clip-b-d`: Assigns the data to be copied to the clipboard when the button is clicked.
  - **data**: The text content or data to be copied. This can be a string, variable, or any other valid data type that can be converted to text.

### Usage:
- **Simple Text Copying**: Incorporating the `clip-b-d` attribute into a button element allows for quick and straightforward copying of specified text. For instance:
  ```html
  <button class="button clip-b" clip-b-d="Copy Text"></button>
  ```
  This button will copy the text "Copy Text" to the clipboard when clicked.

- **Dynamic Content**: Developers can dynamically generate the content to be copied using server-side scripts or client-side JavaScript, allowing for flexible clipboard functionality. For example:
  ```html
  <button class="button clip-b" clip-b-d="<?php echo $dynamicText; ?>"></button>
  ```

### Additional Notes:
- **Static vs. Dynamic Content**: While the `clip-b-d` attribute allows for static text content to be specified directly within the HTML markup, it can also be used in conjunction with server-side scripting languages or client-side JavaScript to dynamically generate the data to be copied.
- **Security Considerations**: When using dynamic content with the `clip-b-d` attribute, developers should ensure that the data being copied does not contain sensitive information and is sanitized to prevent potential security risks, such as cross-site scripting (XSS) attacks.
- **Fallback Options**: For browsers that do not support the Clipboard API or JavaScript, it's advisable to provide alternative methods for users to copy content manually.

### Example:
```html
<!-- Simple clipboard button with specified text -->
<button class="button clip-b" clip-b-d="Click to Copy"></button>

<!-- Dynamic content generation using server-side scripting -->
<?php
    $dynamicText = "Dynamic Text Content";
?>
<button class="button clip-b" clip-b-d="<?php echo $dynamicText; ?>"></button>
```

In summary, the `clip-b-d` attribute facilitates the easy implementation of basic clipboard functionality by allowing developers to specify the data to be copied directly within the HTML markup. This attribute is versatile and can be used with both static and dynamically generated content to provide users with a seamless copying experience.

## **`clip-b-t` Attribute**

The `clip-b-t` attribute is an essential attribute associated with the clipboard component (`clip-b`). It specifies the target element(s) from which text content will be copied when the clipboard button is clicked. This attribute plays a crucial role in determining the source of the text data to be copied to the clipboard.

### Syntax:
```html
<button class="button clip-b" clip-b-t="targetSelector"></button>
```

### Attributes:
- `clip-b-t`: This attribute specifies the target element or elements from which text content will be copied.
  - **targetSelector**: A CSS selector that identifies the target element(s) from which text content will be copied.

### Usage:
- **Single Target Element**: You can specify a single target element using its CSS selector. For example:
  ```html
  <button class="button clip-b" clip-b-t=".input"></button>
  ```
  This will copy the text content from the input field with the class `input` when the button is clicked.

- **Multiple Target Elements**: If you have multiple elements from which you want to copy text content, you can specify them using a common CSS selector. For example:
  ```html
  <button class="button clip-b" clip-b-t="p"></button>
  ```
  This will copy text content from all `<p>` elements on the page.

### Additional Notes:
- The target element specified using `clip-b-t` should contain the text content you wish to copy to the clipboard.
- It's important to ensure that the specified target element(s) exist in the DOM when the clipboard button is clicked.
- You can combine the `clip-b-t` attribute with other attributes like `clip-b-v` to further customize the data that will be copied to the clipboard.

### Example:
```html
<!-- Copy text from a specific paragraph -->
<p id="paragraph1">This is the text to be copied.</p>
<button class="button clip-b" clip-b-t="#paragraph1"></button>


<p>This is paragraph 2.</p>
<button class="button clip-b" clip-b-t="p"></button>
```

In summary, the `clip-b-t` attribute allows you to specify the target element(s) whose text content will be copied to the clipboard when the associated clipboard button is clicked. It provides flexibility in selecting the desired source of text data for copying.


## **`clip-b-v` Attribute**

The `clip-b-v` attribute is an essential part of the clipboard functionality provided by the `clip-b` class. It allows developers to specify the content that will be copied to the clipboard when the associated button is clicked. This attribute provides flexibility in selecting the portion of content from the target element(s) to be included in the clipboard operation.

### Syntax:
```html
<button class="button clip-b" clip-b-v="value"></button>
```

### Attributes:
- `clip-b-v`: Defines the value or property of the target element(s) whose content will be copied to the clipboard.
  - **value**: Specifies the specific property or attribute of the target element(s) to be copied. It can be any valid JavaScript property or attribute containing text content.

### Usage:
- **Copying Text Content**: The most common usage of the `clip-b-v` attribute is to copy the text content of the target element(s). For example:
  ```html
  <button class="button clip-b" clip-b-t=".target-element" clip-b-v="textContent"></button>
  ```
  This button will copy the text content of the element(s) with the class `target-element` to the clipboard when clicked.

- **Customized Content Selection**: Developers can specify different properties or attributes of the target element(s) to be copied based on their requirements. For instance:
  ```html
  <button class="button clip-b" clip-b-t=".input-field" clip-b-v="value"></button>
  ```
  This button will copy the `value` attribute of the input field(s) with the class `input-field` to the clipboard.

### Additional Notes:
- **Property Flexibility**: The `clip-b-v` attribute provides flexibility in selecting the specific property or attribute of the target element(s) to be included in the clipboard operation. Developers can choose attributes such as `textContent`, `value`, `innerHTML`, etc.
- **Dynamic Content Selection**: Developers can dynamically generate the content to be copied by selecting different properties or attributes of the target element(s) based on changing conditions or user interactions.
- **Target Element Dependency**: The behavior of the `clip-b-v` attribute is dependent on the presence of the `clip-b-t` attribute, which specifies the target element(s) from which the content will be copied.

### Example:
```html
<!-- Copying text content from a paragraph -->
<p class="paragraph">Paragraph Content</p>
<button class="button clip-b" clip-b-t=".paragraph" clip-b-v="textContent"></button>

<!-- Copying inner HTML content from a div -->
<div class="content">Text Content to Copy</div>
<button class="button clip-b" clip-b-t=".content" clip-b-v="innerHTML"></button>
```

In summary, the `clip-b-v` attribute enhances the clipboard functionality by allowing developers to specify the value or property of the target element(s) to be copied to the clipboard. This attribute enables customization and flexibility in selecting the content for the clipboard operation, catering to various use cases and requirements.


## **`clip-b-e` Attribute**

The `clip-b-e` attribute is an integral part of the clipboard functionality facilitated by the `clip-b` class. It specifies the method by which target elements are selected and their content is extracted for copying to the clipboard when the associated button is clicked. This attribute offers developers the flexibility to define the selection process based on specific requirements.

### Syntax:
```html
<button class="button clip-b" clip-b-e="method"></button>
```

### Attributes:
- `clip-b-e`: Specifies the method for selecting target elements and extracting content for clipboard operations.
  - **method**: Indicates the selection method. Common values include `"index"` for selecting individual elements by their index, and custom methods defined by developers.

### Usage:
- **Selecting Target Element by Index**: The `clip-b-e="index"` method selects individual target elements based on their index within a collection. For example:
  ```html
  <button class="button clip-b" clip-b-t=".paragraph" clip-b-e="index" clip-b-v="textContent"></button>
  ```
  This button will copy the text content of each paragraph element with the class `paragraph` to the clipboard. Each button corresponds to a specific paragraph based on its index.

### Additional Notes:
- **Custom Selection Methods**: Developers can define custom methods tailored to their specific use cases. These methods can utilize JavaScript functions to select target elements and extract content dynamically.
- **Dynamic Selection Behavior**: The behavior of the `clip-b-e` attribute can be dynamic, allowing developers to change the selection method based on user interactions or other conditions.
- **Dependence on Target Element Selection**: The effectiveness of the `clip-b-e` attribute depends on the accuracy of the target elements specified using the `clip-b-t` attribute.

### Example:
```html
<!-- Selecting target element by index -->
<p class="paragraph">Paragraph 1</p>
<button class="button clip-b" clip-b-t=".paragraph" clip-b-e="index" clip-b-v="textContent"></button>
<p class="paragraph">Paragraph 2</p>
<button class="button clip-b" clip-b-t=".paragraph" clip-b-e="index" clip-b-v="textContent"></button>
```

In summary, the `clip-b-e` attribute allows developers to define how target elements are selected and content is extracted for clipboard operations. By providing various selection methods, developers can create tailored clipboard functionality to suit different use cases and user interactions.

The `clip-b-e` attribute defines the method for selecting target elements and extracting content for clipboard operations. It is important to understand how it functions correctly to avoid unintended behavior in clipboard functionality.

Let's break down the examples provided:

1. **This is wrong:**
   ```html
   <input value="Paragraph First">
   <button class="button clip-b" clip-b-t="input"></button>
   <p class="paragraph">Paragraph 1</p>
   <button class="button clip-b" clip-b-t=".paragraph" clip-b-e="index" clip-b-v="textContent"></button>
   <p class="paragraph">Paragraph 2</p>
   <button class="button clip-b" clip-b-t=".paragraph" clip-b-e="index" clip-b-v="textContent"></button>
   ```
   In this example, the input field is separate from the paragraph elements, and the clipboard button targets the input instead of the paragraphs. This may not produce the desired clipboard behavior, as the input is not associated with the paragraph content.

2. **But this is fine:**
   ```html
   <input class="paragraph" value="Paragraph First">
   <button class="button clip-b" clip-b-t=".paragraph"></button>
   <p class="paragraph">Paragraph 1</p>
   <button class="button clip-b" clip-b-t=".paragraph" clip-b-e="index" clip-b-v="textContent"></button>
   <p class="paragraph">Paragraph 2</p>
   <button class="button clip-b" clip-b-t=".paragraph" clip-b-e="index" clip-b-v="textContent"></button>
   ```
   In this corrected version, the input field is part of the paragraph elements, and the clipboard button targets the paragraph elements correctly, ensuring that the clipboard operation includes the intended content.

3. **This is wrong:**
   ```html
   <input class="paragraph" value="Paragraph First">
   <p class="paragraph">Paragraph 1</p>
   <p class="paragraph">Paragraph 2</p> 
   <button class="button clip-b" clip-b-t=".paragraph" clip-b-e="index" clip-b-v="textContent"></button>
   <button class="button clip-b" clip-b-t=".paragraph" clip-b-e="index" clip-b-v="textContent"></button>
   <button class="button clip-b" clip-b-t=".paragraph"></button>
   ```
   In this example, the clipboard buttons with `clip-b-e="index"` are targeting specific paragraph elements, but the last button without `clip-b-e` does not have a specific target. This may result in inconsistent behavior in the clipboard operation.

4. **But this is fine:**
   ```html
   <input class="paragraph" value="Paragraph First">
   <p class="paragraph">Paragraph 1</p>
   <p class="paragraph">Paragraph 2</p> 
   <button class="button clip-b" clip-b-t=".paragraph" clip-b-e="index" clip-b-v="value"></button>
   <button class="button clip-b" clip-b-t=".paragraph" clip-b-e="index" clip-b-v="textContent"></button>
   <button class="button clip-b" clip-b-t=".paragraph" clip-b-e="index" clip-b-v="textContent"></button>
   ```
   In this corrected version, all clipboard buttons target the paragraph elements correctly, and each button specifies the content to be copied to the clipboard using `clip-b-v`, ensuring consistent behavior across all buttons.

In summary, when using `clip-b-e`, ensure that each clipboard button has a clear and consistent target element, and specify the content to be copied accurately using `clip-b-v` to avoid unintended behavior in clipboard operations.


## **Clipboard Event Handling**

The following documentation provides an example of how to handle events related to clipboard operations triggered by the `clip-b` class. This example demonstrates how to listen for clipboard events such as successful copying, copying completion, and error handling.

### HTML Markup:
```html
<!-- Event -->
<h1>Copy paragraph</h1>
<p class="paragraph">Paragraph Content</p>

<button class="button clip-b" clip-b-t=".paragraph" clip-b-e="index" clip-b-v="textContent"></button>
```

### JavaScript Code:
```javascript
<script>
    // Selecting elements
    var change =  document.querySelector("h1");
    var btn = document.querySelector(".clip-b");
    
    // Event listener for successful clipboard copy
    btn.addEventListener("clip-success", function() {
        change.textContent = "Copied!";
    });
    
    // Event listener for completion of clipboard operation
    btn.addEventListener("clip-after", function() {
        change.textContent = "Copy paragraph";
    });
    
    // Event listener for clipboard operation error
    btn.addEventListener("clip-error", function() {
        console.log("Error copying text to clipboard");
    });
</script>
```

### Description:
- The HTML markup contains a heading (`<h1>`) and a paragraph (`<p>`) element with a class of `paragraph`, along with a button (`<button>`) that triggers clipboard functionality.
- In the JavaScript code:
  - The `document.querySelector` method is used to select the heading and button elements by their respective classes.
  - Event listeners are added to the button element to handle clipboard-related events:
    - `clip-success`: Fired when the clipboard operation is successful. It updates the heading text to indicate that the paragraph has been copied.
    - `clip-after`: Fired after the clipboard operation is completed, resetting the heading text to its initial state.
    - `clip-error`: Fired if an error occurs during the clipboard operation, logging an error message to the console.

This documentation provides a basic example of how to handle clipboard events in a web application using the `clip-b` class and corresponding event listeners. Developers can further customize event handling based on their specific requirements and user experience considerations.
