# play-k6


#### Hello world
> When using the `k6` docker image, you can't just give the script name since
 the script file will not be available to the container as it runs. Instead
 you must tell k6 to read `stdin` by passing the file name as `-`. Then you
 pipe the actual file into the container with `<` or equivalent. This will
 cause the file to be redirected into the container and be read by k6.

`docker run --rm -i grafana/k6 run - <./script/hello.js`

![helloworld](https://github.com/hahasoft/play-k6/assets/40051294/956fe804-7e34-4bf0-92ed-2e816747ee65)

---

#### Running a 5-second, 10-VU load test
`docker run --rm -i grafana/k6 run --vus 2 --duration 5s - <./script/hello.js`

#### Each time you run the script, you can set the options in your JavaScript file:
`docker run --rm -i grafana/k6 run - <./script/hello_opts.js`

![hello_opts](https://github.com/hahasoft/play-k6/assets/40051294/32ee451a-58d0-4a44-8689-878a7e72da3b)

---

#### Ramp VUs up and down in stages
`docker run --rm -i grafana/k6 run - <./script/rampup.js`

![rampup](https://github.com/hahasoft/play-k6/assets/40051294/9e67303e-1e92-4524-b6ae-3c006cfe52f6)

---

#### Ex. http
```
docker run --rm -i grafana/k6 run - <./script/http/httpget.js
docker run --rm -i grafana/k6 run - <./script/http/httppost.js
docker run --rm -i grafana/k6 run - <./script/http/custom_metrics.js
docker run --rm -i grafana/k6 run - <./script/http/check.js
```
---

#### grafana dashboard
```
docker compose up
docker compose run k6 run rampup.js
```

![docker_ps](https://github.com/hahasoft/play-k6/assets/40051294/b2b043e2-d910-4a57-90b1-fe78c873d33f)

![docker_compose](https://github.com/hahasoft/play-k6/assets/40051294/4097aa7a-8656-4532-851f-a7fe6bfc7465)

![db1](https://github.com/hahasoft/play-k6/assets/40051294/163334dd-a550-4c9b-b3c4-c1370fe33676)

---

# Reference
 - https://k6.io/
 - https://github.com/grafana/k6/
 - https://k6.io/docs/results-output/grafana-dashboards/
 - https://grafana.com/grafana/dashboards/?search=k6
 - https://grafana.com/dashboards/2587

---