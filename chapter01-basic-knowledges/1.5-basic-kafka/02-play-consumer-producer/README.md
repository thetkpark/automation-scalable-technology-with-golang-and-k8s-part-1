Play Consumer-Producer
===

Kafkacat URL
https://github.com/edenhill/kafkacat

1. Start all k8s object if not created
$ kubectl apply -f .

2. Check if kafka and zookeeper pods is running
$ kubectl get po -n basic-kafka
NAME                    READY   STATUS    RESTARTS   AGE
client-util             1/1     Running   0          5m28s
kfk1-86886b6b84-75p7p   1/1     Running   2          5m29s
kfk2-5b69dfcdb4-wk9lt   1/1     Running   2          5m29s
kfk3-6d4c8874c6-47dxp   1/1     Running   2          5m29s
zk1-76cc547698-8865g    1/1     Running   0          5m29s
zk2-7bb59d6788-5dfxx    1/1     Running   0          5m29s
zk3-566db54d6b-xqjzh    1/1     Running   0          5m29s

3. Exec into client-util pod
$ kubectl exec -it client-util -n basic-kafka -- bash
root@client-util:/#

4. Start Producer using kafkacat, and send some messages
$ kafkacat -P -b "kfk1,kfk2,kfk3" -t "mytopic"
> -P -> run command as producer (kafkacat as producer)
> -b -> Connect to these broker
> -t -> name of topic

$ message1
$ message1
$ message3

5. Open another tab in terminal, and exec into client-util
$ kubectl exec -it client-util -n basic-kafka -- bash
root@client-util:/#

6. Start Consumer in the open terminal
$ kafkacat -C -b "kfk1,kfk2,kfk3" -t "mytopic"
> -C -> run command as consumer

```
Output:
% Reached end of topic mytopic [20] at offset 0
% Reached end of topic mytopic [11] at offset 0
% Reached end of topic mytopic [8] at offset 0
% Reached end of topic mytopic [22] at offset 2
% Reached end of topic mytopic [35] at offset 1
message1
% Reached end of topic mytopic [26] at offset 0
```
> [<number>] is the partition number
> offset 0 -> no message going in to this partition
> offset <number> -> there is <number> in this partition

7. Exit Consumer by (Ctrl + c)

8. Exit client-util 
$ exit

