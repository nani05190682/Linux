
1. Create a simple alias:

**Solution:**

To create an alias called "sales" that forwards emails to "sales@example.com", follow these steps:

1. Connect to your server via SSH.
2. Open the aliases file located at `/etc/aliases` using a text editor.
3. Add the following line to the file: `sales: sales@example.com`
4. Save and close the file.
5. Run the command `newaliases` to update the aliases database.

To test the alias, send an email to "sales@example.com" or "sales@yourdomain.com" and verify that it is delivered to the correct email address.

2. Create a catch-all alias:

**Solution:**

To create an alias called "info" that forwards emails to "info@example.com", follow these steps:

1. Connect to your server via SSH.
2. Open the aliases file located at `/etc/aliases` using a text editor.
3. Add the following line to the file: `info: info@example.com`
4. Save and close the file.
5. Run the command `newaliases` to update the aliases database.

To test the alias, send an email to a non-existing email address on your domain (e.g. "fake@example.com") and verify that it is delivered to the "info" alias.

3. Create a group alias:

**Solution:**

To create an alias called "support" that forwards emails to multiple email addresses, such as "helpdesk@example.com" and "techsupport@example.com", follow these steps:

1. Connect to your server via SSH.
2. Open the aliases file located at `/etc/aliases` using a text editor.
3. Add the following line to the file: `support: helpdesk@example.com, techsupport@example.com`
4. Save and close the file.
5. Run the command `newaliases` to update the aliases database.

To test the alias, send an email to the "support" alias and verify that it is delivered to all specified email addresses.

4. Create an alias with a filter:

**Solution:**

To create an alias called "spamfilter" that forwards emails to "junk@example.com" only if they contain the word "spam" in the subject line, follow these steps:

1. Connect to your server via SSH.
2. Open the aliases file located at `/etc/aliases` using a text editor.
3. Add the following line to the file: `spamfilter: /bin/grep -i -e "^subject:[ ]*.*spam.*" | /usr/bin/mail -s "Possible spam detected" junk@example.com`
4. Save and close the file.
5. Run the command `newaliases` to update the aliases database.

To test the filter, send an email with the word "spam" in the subject line to the "spamfilter" alias and verify that it is delivered to the "junk" email address.

5. Create an alias with a script:

**Solution:**

To create an alias called "notify" that runs a custom script whenever an email is sent to it, follow these steps:

1. Connect to your server via SSH.
2. Open the aliases file located at `/etc/aliases` using a text editor.
3. Add the following line to the file: `notify: |/path/to/script.sh`
4. Save and close the file.
5. Run the command `newaliases` to update the aliases database.

In this example, replace "/path/to/script.sh" with the actual path to your script file.

To test the alias, send an email to the "notify" alias and verify that your script is executed as expected.
