`docker` 容器的网络问题

- 在校园网环境下，`docker` 容器在 `pull` 阶段，往往存在网络延迟问题。
- 该问题无法通过 `proxy` 等手段解决，因为这本质上是 `IP` 层的 `MTU` 设置不当引起的。参考链接：[Docker pull progressively slow for large layers · Issue #40085 · moby/moby · GitHub](https://github.com/moby/moby/issues/40085)
- 推荐的做法是，利用部署在香港或者其他外部服务器拉取 `docker image`，然后通过 `scp` 传输到内部服务器，再执行下一步的 `docker run` 等操作。
