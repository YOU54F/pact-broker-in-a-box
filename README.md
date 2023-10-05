# pact-broker-in-a-box

a pact broker with a bundled ruby runtime, for use in CI suites and systems without docker - its not for sharing or persisting data

You _probably_ don't want to rely on this, and you _definitely_, don't want to run it in production.

So don't

Otherwise, if you just want a Pact Broker ASAP rocky. you got it!

Download script requires `curl`, 

The ruby standalone requires `glibc`, so Alpine users need `apk add gcompat libc6-compat`

You _might_ be able to get away without bash, I'm pretty sure I made the wrapper scripts posix compliant, but if not, install `bash`.

If using `wait-for` - you need `wget` & `netcat`

If you don't have `killall` check out this [link](https://www.thegeekdiary.com/pkill-command-not-found/) for linux specific commands to get it

```sh
export TRAVELING_RUBY_INSTALL_PATH=${HOME}/.pact
export PATH=${HOME}/.pact:${PATH}
curl -fsSL https://raw.githubusercontent.com/YOU54F/traveling-ruby/traveling-pact/cli.sh | sh
pact-broker-app.sh &
wget -qO- https://raw.githubusercontent.com/eficode/wait-for/v2.2.3/wait-for | sh -s -- 0.0.0.0:9292 -t 20 -- echo broker is up
killall ruby || true
```


netcat might be under `netcat-traditional` or `netcat-openbsd` depending on your distro.

Source script:- https://github.com/YOU54F/traveling-ruby/blob/traveling-pact/cli.sh
Srouce release:- https://github.com/YOU54F/traveling-ruby/releases/tag/rel-20230803-pact
