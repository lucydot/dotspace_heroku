
The web app can be found [here](https://boiling-peak-32563.herokuapp.com/voila/render/dotspace.ipynb) and is accessible through the shortened URL [bit.ly/GrainGenerator](https://bit.ly/GrainGenerator).

I've included the steps for creating a simple web app like GrainGenerator below. This uses a combination of:
- [Jupyter Notebooks](https://jupyter.org/)
- [ipywidgets](https://ipywidgets.readthedocs.io/en/latest/) (simple widget library)
- [Voila](https://github.com/QuantStack/voila) (to convert the notebook into a standalone web app)
- [Heroku](https://www.heroku.com/) (to deploy the web app)

This wiki was created after attending a GUI workshop at RSE conference 2019 led by [Diego Alonso Alvarez](https://www.imperial.ac.uk/people/d.alonso-alvarez), where the combination of `Jupyter`+`ipywidgets`+`Voila` was suggested. 

GrainGenerator uses Python, but this workflow should be compatible with any Jupyter kernel (C++, Julia etc).

**1. Notebook with widgets**

Use Jupyter Notebooks and ipywidgets to generate/read in and interact with data (create sliders, input text boxes etc) locally. I recommend using the [ipywidgets](https://ipywidgets.readthedocs.io/en/latest/) documentation. You can see the GrainGenerator code example [here](https://github.com/lucydot/dotspace_heroku/blob/master/dotspace.ipynb).

**2. Convert notebook to local web app**

Use voila to convert the notebook into a simple standalone web application. For testing locally you can follow the installation and usage instructions [here](https://voila.readthedocs.io/en/latest/using.html).

**3. Deploy using Heroku**

Deploy using Heroku so that others can access your web app (I prefer Heroku over Binder as it loads more quickly, and does not have an intermediate loading page). Sign up for a free Heroku account. There are deployment steps for voila [here](https://voila.readthedocs.io/en/latest/deploy.html) and there is a tutorial [here](https://github.com/martinRenou/voila-heroku) but CAUTION the `Procfile` as outlined did not work for me; my `Procfile` contains

> web: jupyter extension enable voila.server_extension --sys-prefix && jupyter server --ServerApp.default_url=/voila --ip=0.0.0.0 --ServerApp.open_browser=False --port=$PORT --ServerApp.token='' --ServerApp.default_url=/voila/render/path/to/notebook.ipynb

as outlined early in [this discussion](https://github.com/QuantStack/voila/issues/184). Your `requirements.txt` should contain `voila` and `jupyter extension`.






