This repo has my public docker files.

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

#### Notes

* For GPU work, install nvidia-docker for your Linux distribution
* Also alias `dockergl="nvidia-docker run -ti --rm -e DISPLAY --net=host"`
