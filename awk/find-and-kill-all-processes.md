# Find and Kill All Processes

When I found CPU usage is higher than usual, I used to do two things:

1. Use `ps` & `grep` to filter possible processes

```shell
ps aux | grep ruby
```

2. Kill the processes

```shell
kill PROCESS_ID
```

However, if there are lots of processes to kill, it would be great if you merge these two steps and one more powerful tool `awk`:

```shell
kill $(ps aux | grep 'guard' | awk '{print $2}')
```

Nice and easy.
