### jupyter-notebook-gist

Create a gist from the Jupyter Notebook UI.

To install, simply run `pip install jupyter-notebook-gist`. Alternatively, clone/download the project and run `pip install .` from a shell in the project's root directory.

After installing, edit your `jupyter_notebook_config.py` file to specify the github client id and secret:

If your `jupyter_notebook_config.py` file does not exist, you can create one by running `jupyter notebook --generate-config`. You can check the location of this file by running `jupyter --config-dir`.

```python
from notebook.services.config import ConfigManager
c = get_config()
cm = ConfigManager()
c.NotebookApp.oauth_client_id = "my_client_id"         # FIXME
c.NotebookApp.oauth_client_secret = "my_client_secret" # FIXME
cm.update('notebook', {"oauth_client_id": c.NotebookApp.oauth_client_id})
```

Replace the vars above with a working client_id / secret. You can create one
[here](https://github.com/settings/applications).

Then run `jupyter notebook` from the repo root.

NOTE: Uninstalling jupyter-spark via `pip uninstall jupyter-spark` will uninstall the server extension but leave the client extension in a partially installed state. To fully remove the extension:

1. Run `pip uninstall jupyter-spark`
2. Delete `spark.js` from your `nbextensions` folder.
3. Delete any references to `jupyter-spark.spark` in `jupyter_notebook_config.json` (in your .jupyter directory)
4. Delete any references to `spark` in `notebook.json` (in .jupyter/nbconfig)
