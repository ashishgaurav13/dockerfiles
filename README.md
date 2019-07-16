This repo has my public docker files.

#### Notes

* For GPU work, install nvidia-docker for your Linux distribution
* It may be convenient for you to use `dockerx`. Place it in your bin?
* Run `dockerx -check` to see defaults and what's installed.
* Create a config like in `configs/rl.txt` and use it as `dockerx -c CONFIG CMD`.
    * If `CMD` is one word and present in `CONFIG`, then equivalent command is run.
    * Else, all of `CMD` is run with the container name in `CONFIG`.
    * Make sure that `CONFIG` has only two sections, just like in `configs/rl.txt`.
    * First section is the name of the docker container.

### [ashishgaurav13/rl](https://cloud.docker.com/repository/docker/ashishgaurav13/rl)

* Ubuntu 18.04
* CUDA10.0/CUDNN7
* Tensorflow, Pytorch, Keras
* OpenAI Gym
* OpenGL Support

To use OpenGL, first add to access control list in host
```
$ xhost local:root
```

Then

```
$ docker run -t -e DISPLAY --net=host ashishgaurav13/rl glxgears
```