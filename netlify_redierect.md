# redierct netlify 


after you have seccessfully deployed your server on the `EC2` you might have noticed that the url is not secure (http not https).

so if you try to make a request to an api that requires https you will get an error. (mixed content error)

+ to fix this issue were going to use something called redierct. which is a configuration that will redirect all http request to https. 


## for react app

+ Step 1:

create a file called `_redirects` in the public folder of your react app.

+ Step 2:

add the following to the file

```
/api/* http://ip:port/api/:splat 200

```

ex:

`/api/* http://44.211.65.244:8001/api/:splat 200`

now every request that starts with `/api` will be redirected to the server ip address and port.


example of a request:

```
axios.get('/api/users')

```


+ step 3: 

deploy your app to netlify and you should be good to go.



## for nextjs app


+ step 1:

create a file called `netlify.toml` in the root of your nextjs app.

+ step 2:

add the following to the file

```
[[redirects]]
  from = "/api/*"
  to = "http://ip:port/api/:splat"
  status = 200
  force = true

```

ex:

```
[[redirects]]
  from = "/api/*"
  to = "http://44.211.65.244:8001/api/:splat"
  status = 200
  force = true

```

now every request that starts with `/api/` will be redirected to the server ip address and port.

