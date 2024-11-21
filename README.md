# PyGithubInLogseq
Example Logseq graph attempting to install and import PyGithub within Embedded Python

## Python code
This is the Python code used in this example. It is included in the Home page of the graph.

As is, the code runs and returns 'true', indicating that 'PyGithub' is in the list of installed modules.

If I try to import PyGithub, the script exits.

See the included comments for more information.

```# Trying to run the Python PyGithub module in Logseq
#
# This is all based on ideas about embedding JS and Python into Logseq found at
# https://discuss.logseq.com/t/edit-and-run-javascript-code-inside-logseq-itself/20763
# and 
# https://discuss.logseq.com/t/edit-and-run-python-code-inside-logseq-itself/20829
# along with the video at
# https://www.youtube.com/watch?v=u1hi7HjG66A
# and it's accompanying logseq graph
# https://github.com/adxsoft/logseq-code-execution-demo-graph
# 
# I am trying to use the Python PyGithub module
# The following code runs in the shell (after pip install PyGithub)
#
# from github import Github
# from github import Auth
# auth = Auth.Token(<access token>)
# with Github(auth=auth) as g:
#     do some github stuff
# 

import js
pyodide = js.logseq.Language.python.Pyodide

await pyodide.loadPackage('micropip')
import micropip 

# PyGithub is not included with Pyodide, need to install from wheel
# Following suggestings at https://pyodide.org/en/stable/usage/loading-packages.html

# I can install PyGithub but I cannot import it

# Install PyGithub
# I can install using 'PyGithub' or an URL to the wheel
# Both ways seem to work the same
# await micropip.install('PyGithub')
PyGithub_wheel_string = "https://files.pythonhosted.org/packages/37/05/bfbdbbc5d8aafd8dae9b3b6877edca561fccd8528ef5edc4e7b6d23721b5/PyGithub-2.5.0-py3-none-any.whl"
await micropip.install(PyGithub_wheel_string)

# Import PyGithub
# I cannot import PyGithub using any of the following methods
# (I get a message that the run failed if I turn on messages)

# If you leave these commented, the script will run and display 'true'
# denoting that 'PyGithub' is installed
# If you uncomment one of them, the script will fail

# from github import Github  # this works in shell
# from github import Auth  # this works in shell
# from PyGithub import Github
# from pygithub import Github
# import PyGithub
# import pygithub

# I can import modules installed with Pyodide
import requests

# I can install and import other Python modules
await micropip.install('Spiffworkflow')
import SpiffWorkflow 

# 'PyGithub' is in the list of modules
items = micropip.list()
# items
'PyGithub' in items```
