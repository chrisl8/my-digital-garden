---
{"dg-publish":true,"permalink":"/knowledge-base/windows-remote-desktop-error-0x708/","dgPassFrontmatter":true}
---

![attachments/Pasted image 20230315205954.png](/img/user/attachments/Pasted%20image%2020230315205954.png)

**Remote Desktop Connection**
```
Your computer could not connect to another console session on the remote computer because you already have a console session in progress.

Error code: 0x708
```

This means that the computer name you tried to reach is not working. Typically this can be fixed by attempting to make a remote connection to the IP Address of the device instead of the device hostname.

I know the error makes zero sense, but the solution for me is always to use the IP Address.

#KnowledgeBase 