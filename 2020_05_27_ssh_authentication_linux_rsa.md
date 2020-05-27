# How to connect to server with rsa key

## Create the key on local machine

This step has to be done only once. First check if you already have one.
```bash
ls -l ~/.ssh/id_*.pub
```

If not present, generate
```bash
ssh-keygen -t rsa -b 4096
```

## Register the key to the server

Run the command to register your machine on the server
```bash
ssh-copy-id remote_username@server_ip_address
```