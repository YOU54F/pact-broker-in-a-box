# pact-broker-in-a-box

a pact broker, for use in CI suites and systems without docker - its not for sharing or persisting data

You _probably_ don't want to rely on this, and you _definitely_, don't want to run it in production.

Use it in your Github actions like this

```yml
    steps:
      - uses: you54f/pact-broker-in-a-box@main
```

Once the step is complete, you will have a running pact broker on http://localhost:9292

1. Installs Scoop for netcat / wget / 7zip
2. Installs ruby
3. Installs pact broker
    1. Uses sqlite built from source on windows
4. Starts pact broker
5. Uses wait-for script which requires netcat / wget to wait for broker to start successfully
