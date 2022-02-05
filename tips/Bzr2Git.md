# Bzr to Git

convert Bzr repository (on Launchpad) into Git.

[required]
- SSH key
- pip fastimport
- pip breezy

## Start SSH agent

```
ssh-keygen -t rsa
eval `ssh-agent`
```

upload your `~/.ssh/id_rsa.pub` to Launchpad.

## Login Launchpad

```
bzr whoami "YOURNAME <YOUR-EMAIL-ADDRESS@EXAMPLE.NET>
bzr lp-login YOURNAME -Ossl.cert_reqs=none
```

## Getting your bzr branch

```
bzr branch lp:~YOUR-BRANCH-URL
```

## Stop SSH agent

```
eval `ssh-agent -k`
```

## Install PIP plugins.

```
pip install fastimport
pip install breezy
pip show breezy -f | grep brz
```

add pip `Scripts` path for `brz` .

## Convert bzr branch into git

```
cd YOUR-BRANCH-DIR
git init
brz fast-export --plain . | git fast-import
```

## Done

```
git log
```

all your code are belong to you.
