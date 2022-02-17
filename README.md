# checkout-qemu-buildx
This is a collection of tasks which I repeat in basically all my workflows, so
I decided to group them all into a single "composite action".

This will:

- Checkout the repository
- Set up QEMU
- Configure Docker Buildx
- Login to DockerHub

## Usage

```yaml
- name: Checkout repository and set up Docker
  uses: JonasAlfredsson/checkout-qemu-buildx@v1.0.0
  with:
    should_login: ${{ github.event_name != 'pull_request' }}
    username: ${{ secrets.DOCKERHUB_USERNAME }}
    password: ${{ secrets.DOCKERHUB_TOKEN }}
```

## Versioning

This repository will begin at version `v1.0.0`, and at this point in time the
sub-actions have these versions:

- `actions/checkout@v2.4.0`
- `docker/setup-qemu-action@v1.2.0`
- `docker/setup-buildx-action@v1.6.0`
- `docker/login-action@v1.12.0`

Each time one of these change I will increase the same `major`/`minor`/`patch`
here. So if one dependency increase its `patch` version I will increase this
repository's `patch` version. If one of these jumps a `major` so will this,
which means that you can be pretty confident that noting suddenly breaks when
pinning to a version here.
