---
layout: post
category: Jenkins
tags: [Jenkins]
description:
revdate:  2019-04-21  09:06 +0900
---
# Jenkins のmasterとslave




## JenkinsのMasterとslave

## Master

* jenkinsおじさん自身のこと

## Slave

* 特定のジョブを実行させたいマシン


### Slave が追加できない（[SSH] No Known Hosts file was found at /var/jenkins_home/.ssh/known_hosts.）

```
SSHLauncher{host='192.168.11.XX', port=22, credentialsId='XX', jvmOptions='', javaPath='', prefixStartSlaveCmd='', suffixStartSlaveCmd='', launchTimeoutSeconds=210, maxNumRetries=10, retryWaitTime=15, sshHostKeyVerificationStrategy=hudson.plugins.sshslaves.verifiers.KnownHostsFileKeyVerificationStrategy, tcpNoDelay=true, trackCredentials=true}
[04/21/19 10:45:35] [SSH] Opening SSH connection to 192.168.11.XX:22.
/var/jenkins_home/.ssh/known_hosts [SSH] No Known Hosts file was found at /var/jenkins_home/.ssh/known_hosts. Please ensure one is created at this path and that Jenkins can read it.
Key exchange was not finished, connection is closed.
java.io.IOException: There was a problem while connecting to 192.168.11.XX:22
	at com.trilead.ssh2.Connection.connect(Connection.java:758)
	at hudson.plugins.sshslaves.SSHLauncher.openConnection(SSHLauncher.java:1175)
	at hudson.plugins.sshslaves.SSHLauncher$2.call(SSHLauncher.java:846)
	at hudson.plugins.sshslaves.SSHLauncher$2.call(SSHLauncher.java:833)
	at java.util.concurrent.FutureTask.run(FutureTask.java:266)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1149)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:624)
	at java.lang.Thread.run(Thread.java:748)
Caused by: java.io.IOException: Key exchange was not finished, connection is closed.
	at com.trilead.ssh2.transport.KexManager.getOrWaitForConnectionInfo(KexManager.java:95)
	at com.trilead.ssh2.transport.TransportManager.getConnectionInfo(TransportManager.java:237)
	at com.trilead.ssh2.Connection.connect(Connection.java:710)
	... 7 more
Caused by: java.io.IOException: The server hostkey was not accepted by the verifier callback
	at com.trilead.ssh2.transport.KexManager.handleMessage(KexManager.java:548)
	at com.trilead.ssh2.transport.TransportManager.receiveLoop(TransportManager.java:790)
	at com.trilead.ssh2.transport.TransportManager$1.run(TransportManager.java:502)
	... 1 more
[04/21/19 10:45:35] Launch failed - cleaning up connection
[04/21/19 10:45:35] [SSH] Connection closed.
```

### 対処

Host Key Verification Strategyの設定値を変更する。
「Known hosts file Verification strategy」
　　　　　　　　　　↓
「Manually trusted key Verification Strategy」