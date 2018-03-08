# eComCharge Gateway and WLS setup

In order to setup project, you have to:

```
> docker-compose build
> docker-compose run gateway bash
> RACK_ENV=test rake db:create
> RACK_ENV=test rake db:schema_load
# press ctrl-D to quit
> docker-compose run wls bash
> rake db:create
> rake db:schema:load
# press ctrl-D to quit
# setup solr
> docker-compose exec solr solr create_core -c test
> docker-compose exec solr solr create_core -c development
```

Now you can run anything inside projects like this:

```
docker-compose run gateway bash
> rspec
> cucumber
```

Inside wls, update solr config to connect to host: solr, port: 8983
