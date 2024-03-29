# `$htp` 

The `$htp` function is a custom JavaScript function designed to handle AJAX (Asynchronous JavaScript and XML) requests for dynamic content loading. It simplifies the process of fetching data from a server and updating specified HTML elements with the response content.

#### Syntax

```javascript
$htp.call(element,dynamic_options,options);
```

- `element`: The DOM element on which the `$htp` function is called. This element should have attributes specifying the details of the AJAX request, such as the URL (`htp-get`) and additional query parameters (`htp-query`).

#### Example Usage

```html
<div
     htp-get="/content.html"
     htp-query='{"key":1,"id":"20"}'>
     Click me to fetch data
</div>
```
```js
<script>
 document.querySelector("div").addEventListener("click",function(){
 $htp.call(this);
});
</script>
```

#### Example Usage (POST Request)

```html
<div class="post"
      htp-post="/submit.php"
      htp-query='{"key":1,"id":"20"}'>
</div>
```

## `$htp.call()`

```javascript
// Call the $htp function with dynamic options
$htp.call(document.querySelector(".element"), { dynamic: "value" });

// Another example with additional static options
$htp.call(document.querySelector(".element"), { dynamic: "value" }, {
    "htp-get": "/hello.html",
   //  or... options
});
```

#### Explanation:

- The `$htp.call()` function is used to initiate an AJAX request.
- In the first example, only dynamic options are provided. The dynamic options object `{ dynamic: "value" }` contains data that can be interpolated into the AJAX request. This data could be used for various purposes, such as constructing the request URL or providing query parameters.
- In the second example, both dynamic and static options are provided. The dynamic options `{ dynamic: "value" }` remain the same, while static options are provided as a separate object. Static options include properties like `"htp-get"`, which specifies the URL for the AJAX request.
- By providing both dynamic and static options, you can customize the AJAX request based on both fixed and variable parameters.
- The `document.querySelector(".element")` selects the HTML element on which the AJAX request will be triggered. This element must have appropriate `htp-get` or `htp-post` attributes defined to specify the type and details of the request.
- When the `$htp.call()` function is executed, it triggers an AJAX request based on the provided options.

## `$htp Events` 

$htp triggers events during various stages of the HTTP request lifecycle. These events can be useful for tracking the progress of AJAX requests and performing actions based on the state of the request. Below are the events along with their descriptions:

---

#### 1. `htp-load`

- **Description:** This event is triggered when an AJAX request initiated by $htp starts loading data from the server.
- **Usage:** Use this event to display a loading indicator or perform other actions indicating that data is being fetched.
- **Example:**
  ```javascript
  document.querySelector(".element").addEventListener("htp-load", function() {
      console.log("Loading...");
  });
  ```

#### 2. `htp-loaded`

- **Description:** This event is triggered when the AJAX request initiated by $htp successfully retrieves data from the server and the content is ready to be processed.
- **Usage:** Use this event to hide the loading indicator and display the fetched content.
- **Example:**
  ```javascript
  document.querySelector(".element").addEventListener("htp-loaded", function() {
      console.log("Content loaded...");
  });
  ```

#### 3. `htp-fail`

- **Description:** This event is triggered when the AJAX request initiated by $htp fails to retrieve data from the server.
- **Usage:** Use this event to handle errors gracefully, such as displaying an error message to the user.
- **Example:**
  ```javascript
  document.querySelector(".element").addEventListener("htp-fail", function() {
      console.error("Failed to load content.");
  });


## `dynamically Events`

The provided CSS code dynamically adjusts the appearance of elements based on the presence of certain attributes (htp-on, htp-fail, htp-done) to reflect the state of an AJAX request managed by $htp. Here's a breakdown of what each part does:

1. **Display Loading Indicator during Loading**:
   ```css
   .target[htp-on] {
       /* Style for when loading */
   }
   ```
   - This rule applies styles to elements with the class `.target` when the `htp-on` attribute is present, indicating that an AJAX request is in progress.

2. **Hide Dynamic Content and Error Message by Default**:
   ```css
   .target[htp-on] .dynamic,
   .target[htp-fail] .dynamic {
       display: none;
   }
   .page-error {
       display: none;
   }
   ```
   - This rule hides elements with the class `.dynamic` when either the `htp-on` or `htp-fail` attributes are present, as well as hiding the `.page-error` element by default.

3. **Display Error Message if Loading Fails**:
   ```css
   .target[htp-fail] .page-error {
       display: block;
   }
   ```
   - This rule displays the error message element (`.page-error`) when the `htp-fail` attribute is present, indicating that the AJAX request has failed.

4. **Hide Loading Indicator when Loading is Done or Fails**:
   ```css
   .target[htp-done] .loading, 
   .target[htp-fail] .loading {
       display: none;
   }
   ```
   - This rule hides the loading indicator element (`.loading`) when either the `htp-done` or `htp-fail` attributes are present, indicating that the AJAX request has either successfully completed or failed.

Overall, these CSS rules provide a way to dynamically adjust the appearance of elements based on the state of an AJAX request, ensuring a better user experience by showing loading indicators and error messages appropriately.


## `htp-options`

The `htp-options` attribute provides a comprehensive set of options for configuring AJAX requests made using the `$htp` function in JavaScript. These options allow developers to customize various aspects of the HTTP request, including request method, headers, success callback, error handling, and more.

#### List of `htp-options`

1. **htp-method**: Specifies the HTTP method for the request (`GET`, `POST`, etc.).
2. **htp-t**: Specifies the target element where fetched content will be inserted.
3. **htp-query**: Specifies query parameters for the request.
4. **htp-headers**: Specifies custom headers for the request.
5. **htp-s**: Specifies the success callback function to handle the HTTP request's successful response.
6. **htp-swap**: Specifies the property to update with the fetched content (e.g., `innerHTML`, `append`).
7. **htp-swap-s**: Specifies the method for inserting fetched content (`after`, `before`, etc.).
8. **htp-status**: Defines the expected status code for successful responses.
9. **htp-sync**: Controls the synchronization behavior of HTTP requests triggered by `htp-call`.
10. **htp-ldr**: Specifies a loading indicator or error message while the request is in progress or in case of failure.

#### Example Usage

```html
<div 
  htp-get="/api/data"
  htp-method="GET"
  htp-t=".target"
  htp-query='{"category": "books", "page": 1}'
  htp-headers='{"Authorization": "Bearer YOUR_TOKEN"}'
  htp-s="handleSuccess"
  htp-swap="append"
  htp-swap-s="after"
  htp-status="200"
  htp-sync="true"
  htp-ldr=".loading-indicator"
></div>
```

#### Explanation

- The `htp-get` attribute specifies the URL for the AJAX request.
- The `htp-method` attribute sets the HTTP method to `GET`.
- The `htp-t` attribute designates the target element for inserting fetched content.
- The `htp-query` attribute defines query parameters for the request.
- The `htp-headers` attribute includes custom headers in the request.
- The `htp-s` attribute assigns a success callback function to handle successful responses.
- The `htp-swap` attribute determines how the fetched content is updated (`append` in this case).
- The `htp-swap-s` attribute specifies the method for inserting the fetched content (`after`).
- The `htp-status` attribute sets the expected status code for successful responses.
- The `htp-sync` attribute controls the synchronization behavior of subsequent requests (`true` for synchronous behavior).
- The `htp-ldr` attribute specifies a loading indicator or error message.

#### Best Practices

- Use meaningful values for each option to ensure clarity and maintainability of code.
- Test different combinations of options to verify proper functionality in various scenarios.
- Handle errors gracefully by providing appropriate error messages or fallback content.


### `htp-get` and `htp-post`

The `htp-get` and `htp-post` attributes are used in HTML elements to specify the URL for AJAX requests and the HTTP method to be used (GET or POST). These attributes are commonly used in conjunction with JavaScript functions such as `$htp.call()` to initiate AJAX requests and retrieve data from or send data to a server.

#### `htp-get` Attribute

The `htp-get` attribute is used to specify the URL for making HTTP GET requests. When an element with `htp-get` is activated (e.g., clicked), the JavaScript function associated with it (e.g., `$htp.call()`) will initiate a GET request to the specified URL.

##### Example Usage:

```html
<div htp-get="/api/data">Click me to fetch data</div>
```
```js
document.querySelector("div").addEventListener("click",function(){
 $htp.call(this);
});
```

#### `htp-post` Attribute

The `htp-post` attribute is used to specify the URL for making HTTP POST requests. Similarly to `htp-get`, when an element with `htp-post` is activated, it triggers a JavaScript function to initiate a POST request to the specified URL.

##### Example Usage:

```html
<div  htp-post="/api/data"
htp-query='{"key":1,"id":"20"}'
>Click me to fetch data</div>
```
```js
document.querySelector("div").addEventListener("click",function(){
 $htp.call(this);
});
```

#### Usage Notes:

- Use `htp-get` for requests where you want to retrieve data from the server.
- Use `htp-post` for requests where you want to send data to the server, typically used with form submissions.
- These attributes are often used in combination with JavaScript functions to handle the AJAX requests and responses, such as `$htp.call()`.


##  `htp-query`

The `htp-query` attribute in an AJAX request specifies the query parameters to be sent along with the request. These parameters are typically used to customize the server's response based on the client's requirements. The `htp-query` attribute value should be a valid JSON object representing the query parameters.

#### Syntax:

```html
<div
    htp-get="/api/data"
    htp-query='{"param1": "value1", "param2": "value2"}'
>
    <!-- AJAX Content -->
</div>
```
#### Example:

```html
<div
    htp-get="/api/data"
    htp-query='{"page": 1, "limit": 10, "sort": "asc"}'
    htp-swap="innerHTML"
    htp-t=".data-container"
>
    <!-- Placeholder for AJAX Content -->
</div>
```

#### Explanation:

- In this example, a `<div>` element is configured to make a GET request to `/api/data` with query parameters `page`, `limit`, and `sort`.
- The `htp-query` attribute value is a JSON object with key-value pairs specifying the query parameters.
- The fetched content will replace the innerHTML of the element with the class `data-container` once the request is successful.

#### Notes:

- Ensure that the query parameters are properly encoded, especially if they contain special characters or spaces.
- Check the server-side documentation to understand how query parameters are expected to be formatted and processed.
- Use query parameters to filter, paginate, or customize the server's response based on the client's requirements.
- 
## Dynamic Values

In HTML, dynamic values can be injected into attributes using placeholders. These placeholders are then replaced with actual values using JavaScript before initiating AJAX requests. Here's an example demonstrating the usage of dynamic values:

```html
<div
  class="content"
  htp-get="/api/data"
  htp-query='{"key":1,"id":"$id","user_name":"$name","total":"$total_number()"}'
>
  <!-- Dynamic Values -->
  <!-- $id: 12, $name: "barinty", $total_number(): 80 -->
</div>
<script>
  var id = 12;
  var name = "barinty";
  function total_number() {
    return 50 + 30;
  }
  $htp.call(document.querySelector(".content"), {
    id: id,
    /.............../ 
  });
</script>
```

#### Explanation:

- In the `htp-query` attribute, placeholders like `$id`, `$name`, and `$total_number()` are used to represent dynamic values.
- JavaScript variables (`id` and `name`) and a function (`total_number()`) are defined to provide actual values for these placeholders.
- The `$htp.call()` function is invoked with the target element (`.content`) and an object containing the values for dynamic placeholders (`id` and `name`).
- Before making the AJAX request, the placeholders in `htp-query` are replaced with their corresponding values.

This approach allows for flexible and dynamic generation of AJAX requests with varying parameters based on the context or user input.


##  `htp-t` target-element

The `htp-t` attribute is employed to specify the target element where fetched content will be inserted after a successful AJAX request. Below are examples illustrating different usage scenarios of `htp-t`.

#### Example 1: Using Class Selector

```html
<div htp-get="/list.html" htp-t=".target"></div>
<div class="target">
  <!-- Placeholder for AJAX Content -->
</div>
```

- In this example, an AJAX request is made to fetch data from the URL specified in `htp-get`.
- After a successful response, the fetched content will replace the content inside the element with the class `target`.

#### Example 2: Using ID Selector

```html
<div htp-get="/list.html" htp-t="#data"></div>
<div id="data">
    <h>hello world</h>
    <div htp-data="">
        <!-- Placeholder for AJAX Content -->
    </div>
</div>
```

- Here, an AJAX request is initiated to retrieve data from the URL specified in `htp-get`.
- Upon receiving a successful response, the fetched content will replace the content inside the element with the ID `data`.

#### Example 3: Using Tag Name and ID Selector

```html
<div htp-get="/list.html" htp-t="#data2"></div>
<p id="data2" htp-data="">
    <!-- Placeholder for AJAX Content -->
</p>
```

- This example demonstrates using both tag name and ID selector in `htp-t`.
- After a successful AJAX response, the fetched content will replace the content inside the `<p>` element with the ID `data2`.

#### Usage Notes:

- `htp-t` accepts CSS selectors, IDs, or tag names to specify the target element.
- Ensure that the target element exists in the document for the content insertion to occur correctly.
- It's essential to have proper placeholder content within the target elements to ensure a seamless transition when the AJAX content is loaded.
- Test the behavior of content insertion with different target elements to confirm the expected functionality.

These examples showcase how `htp-t` can be utilized to define the location where fetched content should be inserted in the HTML document following an AJAX request.

##  `htp-status`

The `htp-status` attribute in an AJAX request specifies the expected HTTP status code for a successful response. It allows you to define the specific status code that indicates a successful response from the server. If the response status code matches the one specified in `htp-status`, the success handler (specified using `htp-s`) will be executed.

#### Syntax:

```html
<div
    htp-get="/api/data"
    htp-status="200"
    htp-s="handleSuccess"
>
    <!-- AJAX Content -->
</div>
```

#### Attributes:

- **htp-get** or **htp-post**: Specifies the URL to which the AJAX request will be sent.
- **htp-status**: Specifies the expected HTTP status code for a successful response.
- **htp-s** (optional): Specifies the function to be called upon a successful response.

#### Example:

```html
<div
    htp-get="/api/data"
    htp-status="200"
    htp-s="handleSuccess"
>
    <!-- AJAX Content -->
</div>
<script>
    function handleSuccess(response,status) {
        console.log("Request successful!");
        console.log("Response:", response);
    }
</script>
```

#### Explanation:

- In this example, a `<div>` element is configured to make a GET request to `/api/data`.
- The `htp-status` attribute is set to `200`, indicating that a successful response should have an HTTP status code of `200`.
- If the response from the server has a status code of `200`, the `handleSuccess` function will be called, processing the response data.

#### Notes:

- Use `htp-status` to define the specific HTTP status code that indicates a successful response from the server.
- Ensure that the specified status code aligns with the server's response behavior.
- You can handle different status codes separately by specifying multiple `<div>` elements with different `htp-status` values and corresponding success handlers (`htp-s`).
- 
##  `htp-headers`

The `htp-headers` attribute in an AJAX request specifies additional HTTP headers to be included in the request sent to the server. These headers can provide various types of information, such as authentication tokens, content types, or custom headers required by the server to process the request properly.

#### Syntax:

```html
<div
    htp-get="/api/data"
    htp-headers='{"HeaderName": "HeaderValue", "Authorization": "Bearer TOKEN"}'
>
    <!-- AJAX Content -->
</div>
```

#### Attributes:

- **htp-get** or **htp-post**: Specifies the URL to which the AJAX request will be sent.
- **htp-headers**: Specifies a JSON object containing key-value pairs of HTTP headers to be included in the request.
- **htp-swap** (optional): Specifies how the fetched content should be inserted into the HTML document (e.g., innerHTML, append).
- **htp-data** (optional): Placeholder for the fetched content.
- Other optional attributes like `htp-query`, `htp-t`, `htp-s`, etc., may also be included based on the specific requirements.

#### Example:

```html
<div
    htp-get="/api/data"
    htp-headers='{"Authorization": "Bearer YOUR_TOKEN", "Content-Type": "application/json"}'
    htp-swap="append"
    htp-t=".target-element"
>
    <!-- Placeholder for AJAX Content -->
</div>
```

#### Explanation:

- In this example, a `<div>` element is configured to make a GET request to `/api/data`.
- The `htp-headers` attribute includes two headers: `Authorization` with the value `Bearer YOUR_TOKEN` and `Content-Type` with the value `application/json`.
- The fetched content will be appended to the element with the class `target-element` once the request is successful.





##  `htp-data`

The `htp-data` attribute is used to indicate the location where fetched content will be inserted after a successful AJAX request. Here are examples illustrating different ways to use `htp-data`.

#### Example 1: Inserting Content Inside a `<div>` Element

```html
<div htp-get="/api/fetch-data">
    <!-- dynamic content -->
</div>
```

- In this example, an AJAX request is made to fetch data from the URL specified in `htp-get`.
- Upon a successful response, the fetched content will replace the existing content inside the `<div>` element.

#### Example 2: Inserting Content Inside a `<div>` Element with Other Elements

```html
<div htp-get="/api/fetch-data">
    <div>other Elements</div>
    <div htp-data="">
        <!-- dynamic content -->
    </div>
</div>
```

- Here, an AJAX request is initiated to retrieve data from the URL specified in `htp-get`.
- After a successful response, the fetched content will replace the content inside the `<div>` element with the `htp-data` attribute.

#### Example 3: Inserting Content Inside a `<p>` Element

```html
<div htp-get="/api/fetch-data" htp-t="p"></div>

<p>
    <!-- dynamic content -->
</p>
```
`or`
```html
<div htp-get="/api/fetch-data" htp-t="p"></div>

<p htp-data="">
    <!-- dynamic content -->
</p>
```

`or`
```html
<div htp-get="/api/fetch-data" htp-t="p"></div>

<p>
<div htp-data="">
 <!-- dynamic content -->
</div>
   
</p>
```

- This example demonstrates inserting content inside a `<p>` element.
- Upon receiving a successful AJAX response, the fetched content will replace the existing content inside the `<p>` element.

#### Usage Notes:

- `htp-data` can be placed inside various HTML elements such as `<div>`, `<p>`, `<span>`, etc., to specify the location where fetched content should be inserted.
- Ensure that the target element with `htp-data` exists in the document for the content insertion to occur as intended.
- The fetched content will replace the existing content inside the element with the `htp-data` attribute.
- Test the behavior of content insertion with different target elements to confirm the expected functionality.

These examples demonstrate how `htp-data` can be used to specify the location where fetched content should be inserted in the HTML document after an AJAX request.

## `htp-swap`

The `htp-swap` attribute in the `$htp` library specifies the property to be updated with the fetched content after a successful AJAX request. It determines how the fetched data will be integrated into the target element. Here's a breakdown of its usage:

#### Available Options:

1. **innerHTML**:
   - Replaces the entire content inside the target element with the fetched data.

2. **append**:
   - Appends the fetched data to the existing content inside the target element.

3. **after**:
   - Inserts the fetched data immediately after the target element.

4. **before**:
   - Inserts the fetched data immediately before the target element.

#### Example Usage:

```html
<!-- Replaces the entire content inside the target element -->
<div htp-get="/api/fetch-data" htp-swap="innerHTML"></div>

<!-- Appends the fetched data to the existing content inside the target element -->
<div htp-get="/api/fetch-data" htp-swap="append"></div>

<!-- Inserts the fetched data immediately after the target element -->
<div htp-get="/api/fetch-data" htp-swap="after"></div>

<!-- Inserts the fetched data immediately before the target element -->
<div htp-get="/api/fetch-data" htp-swap="before"></div>
```

1. **prepend**:
   - Inserts the fetched data at the beginning of the existing content inside the target element.

2. **textContent**:
   - Sets the text content of the target element to the fetched data. This option is useful when you want to replace only the text content without affecting the HTML structure.

#### Example Usage:

```html
<!-- Inserts the fetched data at the beginning of the existing content -->
<div htp-get="/api/fetch-data" htp-swap="prepend"></div>

<!-- Sets the text content of the target element to the fetched data -->
<div htp-get="/api/fetch-data" htp-swap="textContent"></div>
```


#### Usage Notes:

- Choose the appropriate `htp-swap` option based on how you want the fetched data to integrate with the existing content.
- Ensure that the target element exists in the document for the content insertion to occur correctly.
- Test the behavior of content integration with different `htp-swap` options to confirm the expected functionality.

This explanation outlines the usage of `htp-swap` in the `$htp` library, allowing you to control how fetched data is integrated into the target element after an AJAX request.

## `htp-swap-s`

In this example, let's say you have an external HTML file called `example.html` containing some HTML content and scripts. You want to fetch this content and insert it into your current HTML document before a specific target element, while also adjusting the scripts behavior.

#### External HTML File (`example.html`):

```html
<h1>Heading....</h1>
<script>
    // JavaScript code
</script>
<script src="/some.js"></script>
```

#### Integration into Current HTML Document:

```html
<div htp-get="/example.html" htp-swap-s="before"> 
    <!-- This will fetch the content of 'example.html' and insert it before the current element -->
    <script>
        // JavaScript code
    </script>
    <script src="/some.js"></script>
    <!-- data before fetch scripts -->
    <div htp-data>
        <!-- Placeholder for dynamic content -->
        <!-- <h1>Heading....</h1> -->
    </div>
</div>
```

#### Explanation:

- The `htp-get` attribute fetches the content of `example.html`.
- The `htp-swap-s="before"` attribute specifies that the fetched content should be inserted immediately before the current `<div>` element.
- Inside the fetched content, any `<script>` tags or external script references will be executed or loaded respectively.
- The `<div htp-data>` tag indicates where the fetched HTML content will be placed.
- Any dynamic content from the fetched HTML, such as the `<h1>Heading....</h1>`, will be inserted into the document within the `<div htp-data>` tag.

This example demonstrates how to fetch content from an external HTML file and adjust script behavior during insertion using the `htp-swap-s` attribute, providing flexibility in managing dynamic content integration in your web application.

##  `htp-s`

In this example, we'll demonstrate how to use the `htp-s` attribute to specify a callback function to handle the success of an AJAX request.

#### HTML Markup:

```html
<div htp-get="/api/fetch-data" htp-s="calling">
    <div htp-data>
        <!-- Placeholder for fetched data -->
    </div>
</div>
```

#### JavaScript Callback Function:

```javascript
<script>
    // Define the callback function to handle the success of the AJAX request
    function calling(element, status) {
        // `element` parameter represents the element that triggered the AJAX request
        // `status` parameter represents the status of the AJAX request

        // Your logic here to handle the success status
        console.log("AJAX request successful!");
        console.log("Element: ", element);
        console.log("Status: ", status);
    }
</script>
```

#### Explanation:

- The `<div>` element contains the `htp-get` attribute, specifying the URL `/api/fetch-data` from which data will be fetched via an AJAX request.
- The `htp-s="calling"` attribute specifies the name of the JavaScript function `calling` to be executed upon successful completion of the AJAX request.
- Inside the `<div>` element, there's a `<div htp-data>` element which serves as a placeholder for the fetched data.
- The JavaScript function `calling` takes two parameters: `element` (representing the triggering element) and `status` (representing the status of the AJAX request).
- Within the `calling` function, you can define logic to handle the successful completion of the AJAX request, such as updating the UI with the fetched data or performing additional operations based on the status.

This example demonstrates how to use the `htp-s` attribute to define a callback function that executes upon successful completion of an AJAX request triggered by the `$htp` library.


##  `htp-sync`

In this example, we'll demonstrate how to use the `htp-sync` attribute to control the synchronization behavior of HTTP requests triggered by `$htp`.

#### HTML Markup:

```html
<div class="load-more-cnt" htp-get="/load-more.php" htp-query='{"key":1,"id":"$id"}' htp-sync="true" htp-swap="append">
    <div class="cnt" htp-data="">
        <p data="1">first paragraph</p>
        <p data="2">second paragraph</p>
    </div>
    <button>load more</button>
</div>
```

#### JavaScript:

```javascript
<script>
    // Event listener for the "load more" button
    var button = document.querySelector("button");
    button.addEventListener("click", function() {
        // Get the last paragraph's data attribute value
        var id = Array.from(document.querySelectorAll('p')).slice(-1)[0].getAttribute("data");

        // Trigger the AJAX request with the updated id value
        $htp.call(document.querySelector(".load-more-cnt"), {id: id});
    });
</script>
```

#### Explanation:

- The `<div>` element with the class `load-more-cnt` contains the attributes `htp-get`, `htp-query`, `htp-sync`, and `htp-swap`. 
- The `htp-get` attribute specifies the URL `/load-more.php` from which data will be fetched via an AJAX request.
- The `htp-query` attribute provides the query parameters for the AJAX request, including a dynamic parameter `$id`.
- The `htp-sync="true"` attribute indicates that subsequent HTTP requests triggered by `$htp` should wait for the current request to complete before executing. This ensures that requests are processed in order.
- The `htp-swap="append"` attribute specifies that the fetched data will be appended to the existing content within the `.cnt` element.
- Inside the `<div>` element, there's a `<button>` element labeled "load more", which users can click to trigger the AJAX request for more data.
- When the button is clicked, an event listener calls a JavaScript function. This function retrieves the value of the `data` attribute from the last `<p>` element and triggers the `$htp` call with the updated id value, effectively loading more data.
  
This example demonstrates how to use the `htp-sync` attribute to ensure that AJAX requests triggered by `$htp` are synchronized, preventing concurrent execution and ensuring that requests are processed in the expected order.


##  `Loading Dynamically`

In this example, we'll demonstrate how to dynamically load content from an external URL using `$htp`. We'll also handle loading indicators and error messages.

#### CSS Styling:

```css
<style>
    /* Display loading indicator when htp-on attribute is present */
    .target[htp-on] {
        /* Style for when loading */
    }

    /* Hide dynamic content and error message by default */
    .target[htp-on] .dynamic,
    .target[htp-fail] .dynamic {
        display: none;
    }

    .page-error {
        display: none;
    }

    /* Display error message if loading fails */
    .target[htp-fail] .page-error {
        display: block;
    }

    /* Hide loading indicator when loading is done or fails */
    .target[htp-done] .loading, 
    .target[htp-fail] .loading {
        display: none;
    }
</style>
```

#### HTML Markup:

```html
<!-- Using htp-get directly -->
<div class="target" htp-get="/home.html">
    <div class="loading" loader="icon"></div>
    <div class="page-error" style="color: var(--error-color)">
        Page Can't Load. Please Try Again!!!
    </div>
    <div class="dynamic" htp-data="">
        <!-- Placeholder for dynamic content -->
    </div>
</div>

<!-- Using htp-t to specify target -->
<div htp-get="/home.html" htp-t=".target"></div>

<div class="target">
    <div class="loading" loader="icon"></div>
    <div class="page-error" style="color: var(--error-color)">
        Page Can't Load. Please Try Again!!!
    </div>
    <div class="dynamic" htp-data="">
        <!-- Placeholder for dynamic content -->
    </div>
</div>
```

#### Explanation:

- In the CSS styling, we define styles for loading indicators, error messages, and dynamic content display based on the presence of `htp-on`, `htp-fail`, and `htp-done` attributes.
- The `<div>` elements with the class `target` represent the containers for dynamically loaded content. 
- Inside each container, we have:
  - A loading indicator (`<div class="loading">`) displayed while content is being fetched.
  - A page error message (`<div class="page-error">`) shown if the content fails to load.
  - A dynamic content placeholder (`<div class="dynamic" htp-data="">`) where the fetched content will be inserted.
- We use the `htp-get` attribute to specify the URL from which to fetch content.
- For the second `<div>` element, we use the `htp-t` attribute to specify the target container where the fetched content will be inserted.

This example demonstrates how to use `$htp` to load content dynamically from an external URL while providing feedback to users through loading indicators and error messages.


## `htp-ldr` 

In this example, we'll demonstrate how to load content dynamically with a loader indicator while providing error handling.

#### CSS Styling:

```css
<style>
    /* Hide dynamic content by default */
    .dynamic-t {
        background: pink;
        display: none;
    }

    /* Show dynamic content when loading is done */
    .dynamic-t[htp-done] {
        display: block;
    }

    /* Hide loading indicator and error message when loading is done */
    .target[htp-done] .loading, 
    .target[htp-fail] .loading {
        display: none;
    }

    /* Show error message if loading fails */
    .target[htp-fail] .page-error {
        display: block;
    }
</style>
```

#### HTML Markup:

```html
<div 
    htp-get="/home.html"
    htp-t=".dynamic-t"
    htp-ldr=".target"
></div>

<div class="target">
    <div class="loading" loader="icon"></div>
    <div class="page-error" style="color: var(--error-color)">
        Page Can't Load. Please Try Again!!!
    </div>
</div>

<div class="dynamic-t">
    <div class="dynamic" htp-data="">
        <!-- Placeholder for dynamic content -->
    </div> 
</div>
```

#### Explanation:

- We have a loader indicator with the class `loading` inside the `.target` container.
- The `.dynamic-t` container is initially hidden (`display: none;`) to hide the dynamic content until it's loaded.
- When the dynamic content is loaded (`htp-done`), the `.dynamic-t` container is displayed (`display: block;`).
- If loading fails (`htp-fail`), the error message is displayed, and the loading indicator is hidden.


## `htp-type`

In this example, we'll demonstrate how to use progress indicators for download and upload operations.

#### Download Progress:

```html
<div class="target" htp-get="/home.html">
    <!-- Progress indicator for download -->
    <progress class="loading" value="0" max="100" htp-type="progress">0%</progress>
    
    <!-- Error message for failed download -->
    <div class="page-error" style="color: var(--error-color)">
        Page Can't Load. Please Try Again!!!
    </div>
    
    <!-- Placeholder for dynamic content -->
    <div class="dynamic" htp-data="">
        <!-- dynamic content -->
    </div>
</div>
```

#### Upload Progress:

```html
<div class="target" htp-get="/post.py" htp-query='{"key":1,"id":"20"}'>
    <!-- Progress indicator for upload -->
    <progress class="loading" value="0" max="100" htp-type="progress-up">0%</progress>
    
    <!-- Error message for failed upload -->
    <div class="page-error" style="color: var(--error-color)">
        Page Can't Load. Please Try Again!!!
    </div>
    
    <!-- Placeholder for dynamic content -->
    <div class="dynamic" htp-data="">
        <!-- dynamic content -->
    </div>
</div>
```

#### Explanation:

- For both download and upload operations, we use a `progress` element to visualize the progress. 
- The `value` attribute of the `progress` element is updated dynamically to reflect the progress.
- For download progress, `htp-type="progress"` is used, and for upload progress, `htp-type="progress-up"` is used.
- The error message is displayed in case the operation fails, indicating that the page couldn't load.
- The `dynamic` class is used as a placeholder for the dynamic content that will be loaded after the operation is complete.


## `htp-type and htp-type-t`

In this example, we'll demonstrate how to use a progress indicator with custom styling for a download operation.

```html
<div class="target" htp-get="/home.html">
    <!-- Custom progress indicator with width-based style -->
    <div class="loading progress" htp-type="progress" htp-type-t="width" style="width: 0%;"></div>
    
    <!-- Error message for failed download -->
    <div class="page-error" style="color: var(--error-color)">
        Page Can't Load. Please Try Again!!!
    </div>
    
    <!-- Placeholder for dynamic content -->
    <div class="dynamic" htp-data="">
        <!-- dynamic content -->
    </div>   
</div>
```

#### Explanation:

- We use a `div` element with classes `loading` and `progress` to create a custom progress indicator.
- The `htp-type="progress"` attribute indicates that this element will function as a progress indicator.
- We specify `htp-type-t="width"` to control the progress indicator's style based on the width.
- Initially, the width is set to 0% (`style="width: 0%;"`), indicating that no progress has been made.
- In case of a failed download, the error message is displayed in the `page-error` section.
- The `dynamic` class serves as a placeholder for the dynamic content that will be loaded once the operation is complete.

# `Cross-Origin Note`

When using AJAX requests, it's essential to be aware of cross-origin restrictions imposed by web browsers. These restrictions are in place to enhance security and prevent malicious attacks.

#### Same-Origin Policy:

- By default, web browsers enforce the Same-Origin Policy, which prohibits scripts running under one origin from accessing resources from another origin.
- An origin consists of the combination of protocol (e.g., HTTP, HTTPS), domain (e.g., example.com), and port (if specified).
- For example, a script loaded from `https://example.com` cannot make AJAX requests to `http://api.example.com` due to different origins.

#### Cross-Origin Resource Sharing (CORS):

- To allow cross-origin requests, the server hosting the resource needs to include specific HTTP headers in its response.
- These headers, known as CORS headers, inform the browser that it's safe to allow the request from a different origin.
- Common CORS headers include `Access-Control-Allow-Origin`, `Access-Control-Allow-Methods`, `Access-Control-Allow-Headers`, etc.

#### Handling Cross-Origin Issues:

- If you encounter cross-origin issues while making AJAX requests, ensure that the server hosting the resource supports CORS.
- If you're in control of the server, configure it to include the necessary CORS headers to allow requests from your client's origin.
- If you're unable to modify the server's CORS configuration, you may need to use alternative methods like JSONP or server-side proxies to fetch the resource.
- Additionally, some APIs may require authentication or API keys, which need to be handled securely to avoid exposing sensitive information.

#### JSONP (JSON with Padding):

- JSONP is a technique used to bypass the Same-Origin Policy by dynamically adding a `<script>` tag to the document.
- It allows loading JSON data from a different origin by wrapping the JSON response in a JavaScript function call.
- JSONP requests are limited to `GET` requests and are not as secure as CORS, so use them cautiously and only with trusted sources.

#### Conclusion:

Understanding and addressing cross-origin issues is crucial for building robust and secure web applications. By ensuring proper CORS configuration and handling, you can facilitate seamless communication between your client-side JavaScript code and server-side resources while maintaining a high level of security.
