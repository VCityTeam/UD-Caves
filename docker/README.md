# Docker usage

Build the image from the repository root:

```bash
docker build -t ud-caves -f docker/Dockerfile .
```

The pinned Blender wheel for Linux is x86-64. On an ARM host, cross-build and
run the image with `--platform linux/amd64`.

Display the generator options:

```bash
docker run --rm ud-caves cave.py --help
docker run --rm ud-caves tunnel.py --help
```

Write generated files into a host directory:

```bash
mkdir -p output
docker run --rm -v "$(pwd)/output:/output" ud-caves \
  cave.py --subdivision 2 --grid_size_x 3 --grid_size_y 2 --outputdir /output

docker run --rm -v "$(pwd)/output:/output" ud-caves \
  tunnel.py --subdivision 2 --outputdir /output
```

To inspect the image interactively:

```bash
docker run --rm -it --entrypoint sh ud-caves
```
