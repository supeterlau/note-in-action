Run PostgreSQL server:

    docker run --name postgres-dev -v $HOME/Database/docker-pg/data:/var/lib/postgresql/data -e POSTGRES_PASSWORD=(long_password) -e POSTGRES_USER=(db_user) -e POSTGRES_DB=(db_name) -p 127.0.0.1:5432:5432 -d postgres:alpine

Run PostgreSQL client:

    docker run -it --rm --link postgres-dev:postgres postgres:alpine psql -h postgres -U (db_user) -d (db_name) -P "footer=off"

    docker start postgres-dev

    docker logs postgres-dev

Run Redis server:

    docker run --name redis-dev -v $HOME/Database/docker-redis/data:/data -p 127.0.0.1:6379:6379 -d redis:alpine redis-server --appendonly yes

Run Redis client:

    docker run --rm -it --link redis-dev:redis redis:alpine redis-cli -h redis -n 9

Run MongoDB server:
Run MongoDB client:

docker system prune
https://docs.docker.com/engine/reference/commandline/system_prune/
https://docs.docker.com/engine/reference/commandline/image_prune/
https://docs.docker.com/engine/reference/commandline/container_prune/
