## Venv

### Create venv
First make sure that the following command returns Python 3.12. 
```bash
python -V
```

To create a venv make sure you are in the root directory and run the following command (only do this once): <br>
```bash
python -m venv venv
```

### Activate venv
Make sure your terminal is in the root directory and run the following command to activate the virtual environment: <br> <br>
In command prompt:
```bash
venv\Scripts\activate.bat
```
In PowerShell (Might not work because of a security error):
```bash
venv\Scripts\Activate.ps1
```
For Linux/MacOS:
```bash
source venv/bin/activate
```

If you have just installed the venv, please check the python version again. It should return the same version when you are in the venv.
```bash
python -V
```

## Dependencies

### Install dependencies
Make sure your terminal is in the root directory and that you have the environment activated. Then run the following command to install the dependencies: <br>
```bash
pip install -r requirements.txt
```

### Adding dependencies
After installing new module(s) you will need to update the requirements file to include them, make sure you are in the root directory and that you have the environment activated. Then run the following command: <br>
```bash
pip freeze > requirements.txt
```
