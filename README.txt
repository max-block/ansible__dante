--> How to make a password hash? (different options)
$ ansible all -i localhost, -m debug -a "msg={{ 'mypassword' | password_hash('sha512', 'mysecretsalt') }}"
$ mkpasswd --method=sha-512
$ python -c "from passlib.hash import sha512_crypt; import getpass; print(sha512_crypt.using(rounds=5000).hash(getpass.getpass()))"

--> Install passlib to pipx.ansible
pipx inject ansible passlib

--> Test proxy
curl --proxy socks5://usr:pass@host:port https://httpbin.org/ip