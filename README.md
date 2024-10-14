Requesting a Cloud Shell.Succeeded. 
Connecting terminal...

Welcome to Azure Cloud Shell

Type "az" to use Azure CLI
Type "help" to learn about Cloud Shell

mbh5923 [ ~ ]$ python3 -m venv venv~
mbh5923 [ ~ ]$ python3 -m venv venv
mbh5923 [ ~ ]$ source venv/bin/activate
(venv) mbh5923 [ ~ ]$ pip install flask
Requirement already satisfied: flask in ./venv/lib/python3.9/site-packages (3.0.3)
Requirement already satisfied: itsdangerous>=2.1.2 in ./venv/lib/python3.9/site-packages (from flask) (2.2.0)
Requirement already satisfied: Jinja2>=3.1.2 in ./venv/lib/python3.9/site-packages (from flask) (3.1.4)
Requirement already satisfied: blinker>=1.6.2 in ./venv/lib/python3.9/site-packages (from flask) (1.8.2)
Requirement already satisfied: click>=8.1.3 in ./venv/lib/python3.9/site-packages (from flask) (8.1.7)
Requirement already satisfied: importlib-metadata>=3.6.0 in ./venv/lib/python3.9/site-packages (from flask) (8.5.0)
Requirement already satisfied: Werkzeug>=3.0.0 in ./venv/lib/python3.9/site-packages (from flask) (3.0.4)
Requirement already satisfied: zipp>=3.20 in ./venv/lib/python3.9/site-packages (from importlib-metadata>=3.6.0->flask) (3.20.2)
Requirement already satisfied: MarkupSafe>=2.0 in ./venv/lib/python3.9/site-packages (from Jinja2>=3.1.2->flask) (3.0.1)

[notice] A new release of pip is available: 23.0.1 -> 24.2
[notice] To update, run: pip install --upgrade pip
(venv) mbh5923 [ ~ ]$ mkdir ~/BestBikeApp
mkdir: cannot create directory ‘/home/mbh5923/BestBikeApp’: File exists
(venv) mbh5923 [ ~ ]$ cd ~/BestBikeApp
(venv) mbh5923 [ ~/BestBikeApp ]$ cat >>application.py <<EOL
> from flask import Flask
> app = Flask(__name__)
> @app.route("/")
> def hello():
> return "<html><body><h1>Hello Best Bike App!</h1></body></html>\n"
> EOL
(venv) mbh5923 [ ~/BestBikeApp ]$ pip freeze > requirements.txt
(venv) mbh5923 [ ~/BestBikeApp ]$ export FLASK_APP=application.py
(venv) mbh5923 [ ~/BestBikeApp ]$ flask run &
[1] 7487
(venv) mbh5923 [ ~/BestBikeApp ]$ Traceback (most recent call last):
  File "/home/mbh5923/venv/bin/flask", line 8, in <module>
    sys.exit(main())
  File "/home/mbh5923/venv/lib/python3.9/site-packages/flask/cli.py", line 1105, in main
    cli.main()
  File "/home/mbh5923/venv/lib/python3.9/site-packages/click/core.py", line 1078, in main
    rv = self.invoke(ctx)
  File "/home/mbh5923/venv/lib/python3.9/site-packages/click/core.py", line 1688, in invoke
    return _process_result(sub_ctx.command.invoke(sub_ctx))
  File "/home/mbh5923/venv/lib/python3.9/site-packages/click/core.py", line 1434, in invoke
    return ctx.invoke(self.callback, **ctx.params)
  File "/home/mbh5923/venv/lib/python3.9/site-packages/click/core.py", line 783, in invoke
    return __callback(*args, **kwargs)
  File "/home/mbh5923/venv/lib/python3.9/site-packages/click/decorators.py", line 92, in new_func
    return ctx.invoke(f, obj, *args, **kwargs)
  File "/home/mbh5923/venv/lib/python3.9/site-packages/click/core.py", line 783, in invoke
    return __callback(*args, **kwargs)
  File "/home/mbh5923/venv/lib/python3.9/site-packages/flask/cli.py", line 953, in run_command
    raise e from None
  File "/home/mbh5923/venv/lib/python3.9/site-packages/flask/cli.py", line 937, in run_command
    app: WSGIApplication = info.load_app()
  File "/home/mbh5923/venv/lib/python3.9/site-packages/flask/cli.py", line 335, in load_app
    app = locate_app(import_name, name)
  File "/home/mbh5923/venv/lib/python3.9/site-packages/flask/cli.py", line 245, in locate_app
    __import__(module_name)
  File "/home/mbh5923/BestBikeApp/application.py", line 5
    return "<html><body><h1>Hello Best Bike App!</h1></body></html>\n"
    ^
IndentationError: expected an indented block
(venv) mbh5923 [ ~/BestBikeApp ]$ cat >application.py <<EOL
from flask import Flask
app = Flask(__name__)

@app.route("/")
def hello():
    return "<html><body><h1>Hello Best Bike App!</h1></body></html>\n"

EOL
[1]+  Exit 1                  flask run
(venv) mbh5923 [ ~/BestBikeApp ]$ export FLASK_APP=application.py
(venv) mbh5923 [ ~/BestBikeApp ]$ flask run &
[1] 7536
(venv) mbh5923 [ ~/BestBikeApp ]$  * Serving Flask app 'application.py'
 * Debug mode: off
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on http://127.0.0.1:5000
Press CTRL+C to quit
curl -kl http://localhost:5000/
127.0.0.1 - - [14/Oct/2024 19:56:32] "GET / HTTP/1.1" 200 -
<html><body><h1>Hello Best Bike App!</h1></body></html>
(venv) mbh5923 [ ~/BestBikeApp ]$ kill 7536
(venv) mbh5923 [ ~/BestBikeApp ]$ export APPNAME=$(az webapp list --query [0].name --output tsv)
/usr/lib64/az/lib/python3.9/site-packages/paramiko/pkey.py:100: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from this module in 48.0.0.
  "cipher": algorithms.TripleDES,
/usr/lib64/az/lib/python3.9/site-packages/paramiko/transport.py:259: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from this module in 48.0.0.
  "class": algorithms.TripleDES,
[1]+  Terminated              flask run
(venv) mbh5923 [ ~/BestBikeApp ]$ export APPRG=$(az webapp list --query [0].resourceGroup --output tsv)
/usr/lib64/az/lib/python3.9/site-packages/paramiko/pkey.py:100: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from this module in 48.0.0.
  "cipher": algorithms.TripleDES,
/usr/lib64/az/lib/python3.9/site-packages/paramiko/transport.py:259: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from this module in 48.0.0.
  "class": algorithms.TripleDES,
(venv) mbh5923 [ ~/BestBikeApp ]$ export APPPLAN=$(az appservice plan list --query [0].name --output tsv)
/usr/lib64/az/lib/python3.9/site-packages/paramiko/pkey.py:100: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from this module in 48.0.0.
  "cipher": algorithms.TripleDES,
/usr/lib64/az/lib/python3.9/site-packages/paramiko/transport.py:259: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from this module in 48.0.0.
  "class": algorithms.TripleDES,
(venv) mbh5923 [ ~/BestBikeApp ]$ export APPSKU=$(az appservice plan list --query [0].sku.name --output tsv)
/usr/lib64/az/lib/python3.9/site-packages/paramiko/pkey.py:100: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from this module in 48.0.0.
  "cipher": algorithms.TripleDES,
/usr/lib64/az/lib/python3.9/site-packages/paramiko/transport.py:259: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from this module in 48.0.0.
  "class": algorithms.TripleDES,
(venv) mbh5923 [ ~/BestBikeApp ]$ export APPLOCATION=$(az appservice plan list --query [0].location --output tsv)
/usr/lib64/az/lib/python3.9/site-packages/paramiko/pkey.py:100: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from this module in 48.0.0.
  "cipher": algorithms.TripleDES,
/usr/lib64/az/lib/python3.9/site-packages/paramiko/transport.py:259: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from this module in 48.0.0.
  "class": algorithms.TripleDES,
(venv) mbh5923 [ ~/BestBikeApp ]$ cd ~/BestBikeApp
az webapp up --name $APPNAME --resource-group $APPRG --plan $APPPLAN --sku $APPSKU --location "$APPLOCATION"
/usr/lib64/az/lib/python3.9/site-packages/paramiko/pkey.py:100: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from this module in 48.0.0.
  "cipher": algorithms.TripleDES,
/usr/lib64/az/lib/python3.9/site-packages/paramiko/transport.py:259: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from this module in 48.0.0.
  "class": algorithms.TripleDES,
The webapp 'CMPSC487WLab' doesn't exist
Creating AppServicePlan 'ASP-learn98d2b3d7b72a4890af1d22f74e-824b' or Updating if already exists
Readonly attribute name will be ignored in class <class 'azure.mgmt.web.v2023_01_01.models._models_py3.AppServicePlan'>
Creating webapp 'CMPSC487WLab' ...
Configuring default logging for the app, if not already enabled
Creating zip with contents of dir /home/mbh5923/BestBikeApp ...
Getting scm site credentials for zip deployment
Starting zip deployment. This operation can take a while to complete ...
Deployment endpoint responded with status code 202
Polling the status of async deployment. Start Time: 2024-10-14 20:03:06.556248+00:00 UTC
Status: Building the app... Time: 1(s)
Status: Build successful. Time: 19(s)
Status: Starting the site... Time: 34(s)
Status: Starting the site... Time: 49(s)
Status: Starting the site... Time: 66(s)
Status: Starting the site... Time: 82(s)
Status: Starting the site... Time: 97(s)
Status: Site started successfully. Time: 115(s)
You can launch the app at http://cmpsc487wlab-fxgvfbcebvbvfddn.eastus-01.azurewebsites.net
Setting 'az webapp up' default arguments for current directory. Manage defaults with 'az configure --scope local'
--resource-group/-g default: learn-98d2b3d7-b72a-4890-af1d-22f74efa8d85
--sku default: F1
--plan/-p default: ASP-learn98d2b3d7b72a4890af1d22f74e-824b
--location/-l default: eastus
--name/-n default: CMPSC487WLab
{
  "URL": "http://cmpsc487wlab-fxgvfbcebvbvfddn.eastus-01.azurewebsites.net",
  "appserviceplan": "ASP-learn98d2b3d7b72a4890af1d22f74e-824b",
  "location": "eastus",
  "name": "CMPSC487WLab",
  "os": "Linux",
  "resourcegroup": "learn-98d2b3d7-b72a-4890-af1d-22f74efa8d85",
  "runtime_version": "python|3.10",
  "runtime_version_detected": "-",
  "sku": "FREE",
  "src_path": "//home//mbh5923//BestBikeApp"
}
(venv) mbh5923 [ ~/BestBikeApp ]$ 
