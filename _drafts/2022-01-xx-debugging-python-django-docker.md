---
layout: post
title: "Debugging"
---

using Postbird

using pprint() with docker 

find the docker container id with `docker ps` then run `docker logs container-id -f` to see realtime output of the logs including any vars in pprint() statements.