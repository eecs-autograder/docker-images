# Update EECS 280 AG Docker Image

1. Make changes to the `Dockerfile`.
2. Ensure you've downloaded a local copy of packages not in version control. e.g. Java - find the correct version [here](https://www.oracle.com/java/technologies/javase/javase8u211-later-archive-downloads.html). (You may need to create an Oracle account to download it.)
3. Make sure you've got a DockerHub account and you're logged in.
4. The `.tar.gz` files in this repo are [too large to upload to autograder.io](https://eecs-autograder.github.io/autograder.io/topics/custom_sandbox_images.html#tips-and-tricks) Instead, build an image locally and tag it. Publish to DockerHub. For example:
```console
docker build -t jamesjuett/eecs280-ag:1 .
docker push jamesjuett/eecs280-ag:1
```
5. Then, create a separate `Dockerfile` that contains only the following:
```dockerfile
FROM jamesjuett/eecs280-ag:1
```
6. Use that `Dockerfile` to [rebuild the image via the course configuration](https://eecs-autograder.github.io/autograder.io/topics/custom_sandbox_images.html) for the current term on autograder.io. (Make sure not to commit that `Dockerfile` to this repository, though.)