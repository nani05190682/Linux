Sure, here are the exercises with solutions in RHEL:

## Exercise 1: Adding Users

1. Add two users named `user1` and `user2` to the system.
2. Verify that the users have been added.

**Solution:**

```bash
1. sudo useradd user1
   sudo useradd user2
2. sudo cat /etc/passwd | grep user
```

## Exercise 2: Setting Passwords

1. Set the password for `user1` to `password1`.
2. Set the password for `user2` to `password2`.

**Solution:**

```bash
1. sudo passwd user1
   (enter password)
2. sudo passwd user2
   (enter password)
```

## Exercise 3: Switching Accounts

1. Login as `user1`.
2. Verify that you are logged in as `user1`.
3. Switch to `user2`.
4. Verify that you are logged in as `user2`.
5. Switch back to `user1`.
6. Verify that you are logged in as `user1`.

**Solution:**

```bash
1. su user1
   (enter password)
2. whoami
3. su user2
   (enter password)
4. whoami
5. su user1
   (enter password)
6. whoami
```

## Exercise 4: Logging in as Root

1. Logout from the current account.
2. Login as `root`.
3. Verify that you are logged in as `root`.

**Solution:**

```bash
1. exit
2. su root
   (enter password)
3. whoami
```

## Exercise 5: Logging Out

1. Logout from the current account.

**Solution:**

```bash
1. exit
```
