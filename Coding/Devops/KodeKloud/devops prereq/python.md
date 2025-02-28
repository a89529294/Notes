- `requirements.txt` is the equivalent of `package.json`, 
  `pip install -r requirements.txt`.
- `pip install flask`
- `pip uninstall flask`
- `pip install flask --upgrade`
- `pip list` shows all installed packages
- `pip show flask` shows specific package

## virtual environment

```bash
python -m venv myenv
source myenv/bin/activate
pip install -r requirements.txt

python your_script.py

# when done run 
deactivate # while in vir env
# then
rm -rf myenv
```

### **What is `myenv`?**

- `myenv` is **just a directory** with a specific structure created by `python -m venv`. It contains:
    - A copy of the Python interpreter.
    - A `site-packages` directory for installed packages.
    - Activation scripts (`activate`, `deactivate`).
    - Other supporting files for the isolated environment.  
- There is **nothing special** about `myenv` beyond its structure and purpose. You can delete it, recreate it, or even move it (though moving it is not recommended as it may break paths).

## gunicorn
a popular WSGI (Web Server Gateway Interface) HTTP server for Python web applications.

- `gunicorn main:app -w 2`
	- **`main`**: Refers to the filename (e.g., `main.py`) where your WSGI application is defined.
	- **`app`**: Refers to the variable name (e.g., `app = Flask(__name__)`) that holds the WSGI application object.
	- `-w 2`: 2 workers

A **WSGI application** is simply a Python callable that follows the WSGI specification. Frameworks like Flask and Django wrap this concept into user-friendly objects (like `app`)

