Changing the default SSH port
---
Changing the default SSH port can add an extra layer of security through obscurity. To change the default SSH port on CentOS 8, follow these steps:

1. **Edit the SSH Configuration**:
   
   Open the SSH daemon configuration file using a text editor of your choice. I'll use `nano` here, but you can use `vi`, `vim`, or any other editor you're comfortable with.

   ```bash
   sudo nano /etc/ssh/sshd_config
   ```

   Find the line that starts with `Port` (which should have the default value `22`). Change it to your desired port number, e.g., `2222`:

   ```
   Port 2222
   ```

   Save and close the file.

2. **Adjust the Firewall Rules**:

   If you have `firewalld` enabled and running, you'll need to adjust the rules to allow connections on the new port:

   ```bash
   sudo firewall-cmd --permanent --add-port=2222/tcp
   sudo firewall-cmd --reload
   ```

   Remember to replace `2222` with whatever port number you've chosen.

3. **Restart SSH Daemon**:

   To apply the changes, restart the SSH service:

   ```bash
   sudo systemctl restart sshd
   ```

4. **Test the Configuration**:

   From a client machine or even the same machine, try connecting to the SSH server using the new port:

   ```bash
   ssh -p 2222 username@your_server_ip_or_hostname
   ```

   Make sure to replace `2222` with your new port number and `username` with a valid user on the server.

**Note**: Before ending your current SSH session (if you're connected remotely), ensure you can connect on the new port. This step is crucial to avoid locking yourself out if there's a configuration issue.

Lastly, remember that changing the port is just a basic security measure. It's more of a way to reduce the noise from automated bots but doesn't replace the need for strong passwords, public key authentication, and other security practices.


SSH Passwordless Login
---

Creating a passwordless login for SSH involves using public key authentication. The general idea is to generate a pair of keys (private and public) and then place the public key on the server. Once set up, you can log into the server without a password, using the private key for authentication.

Here's how to set up passwordless SSH login on CentOS:

### 1. Generate Key Pair:

If you haven't already, generate an SSH key pair on the **client** machine (the machine you'll be connecting from):

```bash
ssh-keygen
```

This command creates a private key (`~/.ssh/id_rsa`) and a public key (`~/.ssh/id_rsa.pub`). You can secure the private key with a passphrase if desired, but for a truly passwordless experience, just press `Enter` when prompted for a passphrase.

### 2. Copy the Public Key to the Server:

Use the `ssh-copy-id` utility to copy your public key to the server's `~/.ssh/authorized_keys` file:

```bash
ssh-copy-id username@server_address
```

Replace `username` with your user on the server and `server_address` with the server's IP or hostname.

This command will prompt you for the server password. Once provided, it'll append the public key to the `~/.ssh/authorized_keys` file on the server.

### 3. Test Passwordless Login:

From the client machine, attempt to SSH to the server:

```bash
ssh username@server_address
```

You should be able to log in without being prompted for a password.

### Additional Notes:

- Ensure that the `~/.ssh/` directory on the server has permissions set to `700` and the `~/.ssh/authorized_keys` file has permissions set to `600`. Incorrect permissions can prevent key-based authentication from working:

  ```bash
  chmod 700 ~/.ssh
  chmod 600 ~/.ssh/authorized_keys
  ```

- If you secured your private key with a passphrase (which adds a layer of security if someone gains access to your private key), you can use `ssh-agent` to avoid entering the passphrase each time you use the key.

- Always ensure you have another way to access the server when configuring SSH settings, to avoid locking yourself out in case of a misconfiguration.

Passwordless SSH login is convenient and can enhance security when combined with other measures like disabling root login or using SSH on a non-default port. However, it's crucial to protect your private key, as anyone with access to it (and its passphrase, if set) can access the server.