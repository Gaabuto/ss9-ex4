# Session 09 – Bài 4

```console
<a href="https://nginx.org/">nginx.org</a>.<br/>
To engage with the community please visit
<a href="https://community.nginx.org/">community.nginx.org</a>.<br/>
For enterprise grade support, professional services, additional
security features and capabilities please refer to
<a href="https://f5.com/nginx">f5.com/nginx</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
root@azvps-tm7f1n6r4:~# docker stop my-web && docker rm my-web
my-web
my-web
root@azvps-tm7f1n6r4:~# docker volume create easy-volume
easy-volume
root@azvps-tm7f1n6r4:~# docker volume ls
DRIVER    VOLUME NAME
local     easy-volume
root@azvps-tm7f1n6r4:~# docker run --rm -v easy-volume:/data alpine sh -c "echo 'Luu tru du lieu Docker' > /data/test.txt"
Unable to find image 'alpine:latest' locally
latest: Pulling from library/alpine
e2de96513ba9: Already exists
6d0606d1815c: Download complete
797dd00a0fc7: Download complete
Digest: sha256:294b683cb724975bec92580e1e685676bd4b50bda910ddb8c51d4cabeaec77e6
Status: Downloaded newer image for alpine:latest
root@azvps-tm7f1n6r4:~# docker run --rm -v easy-volume:/data alpine cat /data/test.txt
Luu tru du lieu Docker
root@azvps-tm7f1n6r4:~#
```
