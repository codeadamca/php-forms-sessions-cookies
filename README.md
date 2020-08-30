# php-forms-sessions-cookies

A basic example using PHP to create a basic login form. 

In this example we will create a simple login process that will include four steps:

1. The first page will be an HTML form with a email and password textbox.
2. If the password is correct, the second page will save the email address to a session.
3. The thirs page will include a welcome message and display the email address from the session.
4. The final page will remove all session data and redirect the visitor to the first page. 

## Step 1: The Login Page

Create a new HTML file called `step-1.html`. This file will not require any PHP so it can be given an HTML extension. Add the standard HTML tags to the file and place the following HTML form in the `body`:

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

## Step 2: Check Login Credentials

Create a new file called `step-2.php`. Add the standard HTML tags. Above the `doctype` tag add some PHP to check the email and password:

```php
<?php

session_start();

if( $_POST['email'] == 'jane.doe@email.com' and $_POST['password'] == 'password' )
{

    $_SESSION['login'] = true;
    $_SESSION['email'] = $_POST['email'];

}

?>
```

In the `body` add one message for a successful login and a second message for an error:

```php
<?php if( isset( $_SESSION['login'] ) ): ?>

  <h2>Success!</h2>
  <p>You have been logged in!</p>
  <a href="step-3.php">Continue to Step 3</a>

<?php else: ?>

  <h2>Error!</h2>
  <p>Incorrect email and/or password!</p>
  <a href="step-1.html">Try Again</a>

<?php endif; ?>
```


