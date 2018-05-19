# OpenAI Gym DockerFile based on TF1.6
## It also contains Jupyter Notebook with Python3

# References:

https://stackoverflow.com/questions/40195740/how-to-run-openai-gym-render-over-a-server

CUDA driver w/ OpenGL may conflict w/ xvfb.
Installing CUDA w/ --no-opengl-files option might helpful.


## Ver 0.1:
https://hub.docker.com/r/skynspace/py3-gym-tf1.6/

```
docker run -it -p 8888:8888 -p 6006:6006 -v $PWD:/mnt/notebooks/ skynspace/py3-gym-tf1.6:0.1
nvidia-docker run -it -p 8888:8888 -p 6006:6006 -v $PWD:/mnt/notebooks/ skynspace/py3-gym-tf1.6gpu:0.1
```

## Ver 0.2:
Added two more libraries.

- gym[atari] 
- scikit-image

In progress.
'''
docker 
'''
