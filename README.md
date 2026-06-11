# Learning Docker

## Local reusable docker container to run php composer commands from a shell function

A shell function that mounts whatever directory you're currently in. Add this to your ~/.bashrc or ~/.zshrc:

```
composer() {
    docker run --rm -v $(pwd):/app --user $(id -u):$(id -g) composer:2 "$@"
}
```

- $(id -u):$(id -g) resolves to your actual user/group IDs at runtime, so Docker writes files as you — no root ownership issues, no custom dockerfile needed.
