# Binding of Isaac Knowledge Graph Setup Instructions

## Intro
Once unzipped there are three submodules: 

- `fyp_backend` - Django back end for website
- `fyp_frontend` - Angular front end for website
- `xml_to_csv` - XML reader that generates CSV files for importing into a Neo4j database

Each of the Python submodules have a `requirements.txt` file which can be used to install the required libraries for the project via the following command
```bash
pip install -r requirements.txt
```
The project was developed in Python 3.8, but it is likely to still work in any newer version as well.
The node modules required by the Angular project have all been included in the zipped folder and so [WHAT ACTUALLY NEEDS DOING????]
All the setup commands have been given for a Unix system as that is what was used during development, however it has been tested on a Windows machine, but the commands given here will need adjusting accordingly.

## XML reader
To use the XML reader ensure the XML file from the [Special:Statistics](https://bindingofisaacrebirth.fandom.com/wiki/Special:Statistics) page is saved into the root of the `xml_to_csv` project as `data.xml`. The data file used for development is included already.  
To run the script navigate into the inner `xml_to_csv` folder where the `read_xml.py` file resides and run the file. This can be done in 2 ways:
```bash
python3 read_xml.py
```
or
```bash
sudo chmod +x read_xml.py 
./read_xml.py
```
This will generate new versions of the CSV files already found in the same folder.

## Website
To get the web servers up run the following sets of commands in different terminals:
### Backend
```bash
cd fyp_backend/DjangoAPI
python3 manage.py runserver
```

```bash
cd fyp_frontend/fyp
npm install -g @angular/cli
npm update
ng serve
```

Then navigate to `localhost:4200/graph` in a browser and the website should load, this may take a while, especially on the first attempt.