# Run PredictionIO Engine on Heroku

## Similar Product Template (v0.3.2)
For details, please refer to http://docs.prediction.io/templates/similarproduct/quickstart/

## Getting started
Download PredictionIO engine template (http://templates.prediction.io/) depending on your machine learning needs. 
Tapster uses Similar Product Template. 

This repo contains some additional setups required to run the engine on Heroku.
```
git clone https://github.com/chanlee514/pio-engine && cd pio-engine/
heroku create <your-engine-name> --buildpack=https://github.com/chanlee514/pio-heroku
```

NOTE: Using the pio-heroku buildpack requires increase in Heroku slug size (300MB limit) due to Spark dependency.

Modify conf/pio-env.sh to match your eventserver's postgres database. 
Change PIO_STORAGE_SOURCES_PGSQL_URL to match Heroku's JDBC_DATABASE_URL. You can get this by running
```
heroku run bash 
echo $JDBC_DATABASE_URL
```

## Notes
Another approach that does not require increase in slug size is to locally build PredictionIO, push to git, and use it as a git submodule. This will require using git LFS for jar files.
