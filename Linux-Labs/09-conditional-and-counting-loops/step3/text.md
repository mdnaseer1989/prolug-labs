Now that we've used some loops, we've decided we are going to create a script that uses both of the loop types to create 100 files on both of our servers.

Create a script that loops over a list of servers, logs into them, and then creates 100 files called /tmp/file{{1..100}}.

<br>

### Solution
<details>
<summary>Solution</summary>

Create a script that connects over ssh to both servers and creates the neccessary files.

```plain
echo '
#!/bin/bash

for server in $(cat /root/servers.txt)
  do ssh $server "for i in $(seq 100); do touch /tmp/file$i; done"
done

' > /root/file_create.sh
```

If this works, you can see the files in both locations with this loop.

```plain
for server in controlplane node01; do ssh $server 'ls /tmp/file*'; done
```{{exec}}

Do you see the output you expected? Why or why not?

</details>