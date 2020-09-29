# php-forms-sessions-cookies

A basic example using PHP to create a basic login form. 

In this example we will create a simple login process that will include four steps:

1. The first page will be an HTML form with a email and password textbox.
2. If the password is correct, the second page will save the email address to a session.
3. The thirs page will include a welcome message and display the email address from the session.
4. The final page will remove all session data and redirect the visitor to the first page. 

## Step 1: The Login Page

Create a new HTML file called step-1.html. This file will not require any PHP so it can be given am HTML extension. Add the standard HTML tags to the file and the following HTML form:

```html
<form method="post" action="step-2.php">
  Username:
  <input type="text" name="email">
  <br>
  Password:
  <input type="password" name="password">
  <br>
  <input type="submit" value="Login">
</form>
```
