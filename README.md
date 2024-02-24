# Using Forms, Sessions, and Cookies with PHP

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

Create a new file called `step-2.php`. 

Notice that the action in `step-1.html` is set to `step-2.php`. This page will be loaded when the HTML form in the first has been submitted. When a PHP file receives form data it is available by referenceing a special PHP array called `$_POST` or `$_GET`.

Open your new file and add the standard HTML tags. Above the `doctype` tag add the following PHP whcih will check to see if the provided email and password is correct:

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

If the email address and password are correct, this code will save the member's email address and a logged in status of `true` to a session.

> [!Note]
> A session allows a server side langauge to temporarily store data about a website visitor. It's similar to a cookie except the data resides on the sever and cookie data resides on the client computer. 

To use a session in PHP our code simply needs to initiate a session by executing the `session_start()` function. After the session has been initialized, session data can be created or referenced by using the `$_SESSION` array. 

> [More information on using PHP sessions](https://www.php.net/manual/en/function.session-start.php)

In the `body` add a message for a successful login and a second message for an error:

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

> [!Note]
> If you are testing this file make sure you upload both files to your server and start by loading `step-1.html`. The second file will not work properly without receiving the form data from the first file. 

## Step 3: Display Member Information

Create a new file called `step-3.php`. Open your new file and add the standard HTML tags. Above the `doctype` tage add the following code:

```php
<?php

session_start();

?>
```

This file will display the logged in member's email address by referencing the data in the session. Add the standard HTML tags and add this PHP in the `body`:

```php
<p>You are logged in as <?php echo $_SESSION['email']; ?>.</p>
<a href="step-4.php">Logout</a>
```

## Step 4: Logout

Create a new file named `step-4.php`. This file will simply use the `session_destroy()` function to remove all session data. 

Above the `doctype` tag add the following PHP code:

```php
<?php

session_start();
session_destroy();

?>
```

Within the `body` tag add a message informing visitors they have been logged out and a link back to `step-1.html`:

```html
<p>You have been logged out!</p>
<a href="step-1.html">Start Again</a>
```

Upload all four files to your server and test by loading `step-1.html`. 

## Cookies

For a challenge, adjust the four files above to use cookies instead of sessions. All of the code can remain the same except the code that creates or references session data. 

> [More information on using PHP cookies](https://www.php.net/manual/en/function.setcookie.php)

> Full tutorial URL:  
> https://codeadam.ca/learning/php-forms-session-cookies.html

***

## Repo Resources

* [Visual Studio Code](https://code.visualstudio.com/)
* [Filezilla](https://filezilla-project.org/)
* [PHP](https://php.net)

<a href="https://codeadam.ca">
<img src="https://codeadam.ca/images/code-block.png" width="100">
</a>
