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
