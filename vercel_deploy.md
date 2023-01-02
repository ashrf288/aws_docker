  # redirect using vercel  



## vercel redirect

+ step 1:

create a file called `vercel.json` in the root of your nextjs app.

+ step 2:

add the following to the file

```json
{
  "rewrites": [
    {
      "source": "/api/:path*",
      "destination": "http://ip:port/api/:path*"
    }
  ]
}
```





