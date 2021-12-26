### AWS Elastic Container Registry

Online registry for public and private container images.


### pulling and running container with Docker

`docker pull public.ecr.aws/h0w1j9u3/grinch-aoc:latest`


`docker run -it public.ecr.aws/h0w1j9u3/grinch-aoc:latest`


(printenv can be a good enumeration tech while inside container)

---

You can us `jq` to 'pretty print' contents of a `.json` image file 

`cat manifest.json | jq`

