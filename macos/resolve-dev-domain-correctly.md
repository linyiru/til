# Resolve .dev domain correctly

Everytime I tried to visit websites with a `.dev` domain, I found the following error message:

```text
DNS_PROBE_FINISHED_NXDOMAIN
```

However when I use `dig` to figure out why I can't resolve `.dev` domain, everything goes well. 

```shell
$ dig pptr.dev

; <<>> DiG 9.10.6 <<>> pptr.dev
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 7638
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;pptr.dev.			IN	A

;; ANSWER SECTION:
pptr.dev.		3599	IN	A	185.199.108.153
pptr.dev.		3599	IN	A	185.199.109.153
pptr.dev.		3599	IN	A	185.199.110.153
pptr.dev.		3599	IN	A	185.199.111.153

;; Query time: 224 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Thu Dec 27 11:05:52 CST 2018
;; MSG SIZE  rcvd: 101
```

So I guess it's related to my local settings about DNS. The solution is here: remove `/etc/resolver/dev` and done.

The reason why there was a `etc/resolver/dev` file is I used to develop websites with a `.dev` **local** domain for testing for years. 

Now `.dev` gTLD domain is owned by Google, you should use `.test`, `.local` for local development.
