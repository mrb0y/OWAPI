## OW API

This server is a simple way to get read-only information about players and heroes in Overwatch.  
**A live version runs on https://owapi.net.**  
 
## API Docs

OWAPI has a very simple RESTful API to get information.  
As the API is read-only, the only method required is `GET`.  

See the [doc](/api.md) for more information. 


### Running an instance

OWAPI has a few requirements:

 - A Python version >3.5
 - Probably a Linux-based server; I don't know about the viability of running it on Windows.
 
**Installation steps:**

 1. **Clone the repository.**
 
     `git clone https://github.com/SunDwarf/OWAPI.git`
     
 2. **Create a new virtual environment.**
 
     `python3.5 -m venv ./venv`
     
 3. **Setup a Redis server.**
 
     Redis should be running on the default port - 6379. You can override this in config.yml; however.  
     Redis is used for caching lots of data so that there's not a 10 second delay on EVERY request as the data is fetched and scraped; it is essential. 
     
     For Debian/Ubuntu, you can install one with:
     `sudo apt install redis-server`
     
     You can enable it with:
     `sudo systemctl enable redis-server && sudo systemctl start redis-server`.
     
 4. **Install the requirements.**

     For debian-based systems:
        `sudo apt install libxslt-dev python3-dev build-essential`

     `source ./venv/activate && pip install -r requirements.txt`
     
 5. **Start the OWAPI server.**
 
     `PYTHONPATH=. asphalt run config.yml`
          
     Note: If you want the full speedups from Kyoukai you must run with uvloop enabled:
     `PYTHONPATH=. asphalt run -l uvloop config.yml`