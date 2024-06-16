# aws-lambda-nodejs

Public images from AWS for lambda with nodejs are based on centos or fedora:

 - FROM public.ecr.aws/lambda/nodejs:20
 - FROM amazon/aws-lambda-nodejs:18

So, in this repository you will have a ready to use docker image with:

- ubuntu
- nodejs
- aws lambda runtime for real servers and local testing

## Official repository

https://github.com/jrichardsz/aws-lambda-nodejs

## Public Image

```
docker pull jrichardsz/aws-lambda-nodejs:ubuntu-22-node-20.13.0
```

## Build your own image

If you are concerned about the security, check all the files in this repository and build the image


```
docker build -t aws-lambda-nodejs:ubuntu-22-node-20.13.0 .
```

## Extend

To build another images based on this, if your code is in `/src` , your Dockerfile should look like this

```
FROM aws-lambda-nodejs:ubuntu-22-node-20.13.0

ARG LAMBDA_TASK_ROOT="/app"

# Copy your function code
COPY ./src/ ${LAMBDA_TASK_ROOT}/
RUN npm install 
```

- Build 

```
docker build -t acme:1.0.0 .
```

- And run it

```
docker run -it -p 8080:8080 acme:1.0.0
```

## Tests

To try your lambda code in your localhost execute this

```
curl -XPOST "http://localhost:8080/2015-03-31/functions/function/invocations" -d '{"payload":"hello world!"}' -v && echo
```

## Contributors

<table>
  <tbody>
    <td>
      <img src="https://avatars0.githubusercontent.com/u/3322836?s=460&v=4" width="100px;"/>
      <br />
      <label><a href="http://jrichardsz.github.io/">JRichardsz</a></label>
      <br />
    </td>    
  </tbody>
</table>