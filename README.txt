# create new
heroku create --stack cedar
git push heroku master
heroku addons:add shared-database
heroku apps:rename kotti
heroku scale web=1
heroku ps
heroku logs
heroku open
git remote add origin git@github.com:koansys/heroku-kotti.git
git push origin master

# update

- ./bin/pip install --upgrade kotti
- ./bin/pip install freeze > requirements.txt

# start from existing production

- git remote rename origin heroku
- git remote add origin git@github.com:koansys/heroku-kotti.git

# run locally

## with pgsql

It seems it needs psycopg2 locally

- pip install psycopg2

- PORT=5000 DATABASE_URL=postgresql://dbuser:ultrasecretsauce@localhost:5432/kotti foreman start -f Procfile

## with SQLite

- PORT=5000 DATABASE_URL=sqlite3:///Kotti.db foreman start -f Procfile ## persisted
- PORT=5000 DATABASE_URL=sqlite3:// foreman start -f Procfile ## in memory
