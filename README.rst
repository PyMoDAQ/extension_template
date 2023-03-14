Extension template
##################
This is a template to follow in order tocreate new extensions of PyMoDAQ. 

These extensions can either be launched as standalone programs, or launched from a dashboard (using 'Extensions' in the top bar menu).
The template generates a default interface containing a bunch of useful functionalities: some viewers, parameter trees, a module manager, etc. The code serves as an example of how all this is implemented, and should therefore provide a good starting point to design custom applications.

Getting started with the template
*********************************

As an example, say we create an extension called 'Move Everywhere'. 

Go to the GitHub repository: https://github.com/PyMoDAQ/extension_template
Then click on the green button "Use this template", then "Create new repository". This will directly create a repository with the correct structure. Clone this repo to your local computer, and you can start editing.

For the extension to be findable and have the right name, you need to change:

- Rename all folders and files accordingly. folder: `myextension`__ -> move_everywhere, file: `extension.py`__  -> move_everywhere.py

- In move_everywhere.py, rename the default MyExtension class:
  
  ::
  
    class MoveEverywhere(gutils.CustomApp):
      # list of dicts enabling the settings tree on the user interface
      params = [
      ...

- In `setup.cfg`__: 

  * all metadata that you like to change (name, email, url, etc)
  
  * ``py_module = move_everywhere``   (this will be the name of the python package, e.g. pymodaq when you do "pip install pymodaq")
  
  * ``install_requires``, ``python_requires``: list all dependices that need to be installed automatically when installing your extension
  
  * at the bottom, you can use a short name or the full name:
  
    ::
   
      pymodaq.extensions =
           move = move_everywhere
  * and if you want to create a script to launch your extension from the command line, you can add at the bottom:
  
    ::
   
      console_scripts =
           move = move_everywhere.move_everywhere.main
           
    (this means that typing ``move``in your console will launch the main() function in the move_everywhere.py file, itself in the move_everywhere module)


- Finally, the last one can be a little hard to find: in `src/move_everywhere/__init__.py`__ (in the same folder as your main move_everywhere.py file)
  
  ::
  
    NICE_NAME = 'Move Everywhere'
    module_name = 'move_everywhere'
    klass_name = 'MoveEverywhere'
    
  ``NICE_NAME`` is the text that will appear in the DashBoard/Extensions menu, module_name must match the ``py_module`` in setup.cfg, and ``klass_name`` must   match the name of your class in move_everywhere.py.
  
From there, you can install the module in "developer mode": with your command line in the /src folder, ``pip install -e .``
You should already be able to launch move_everywhere.py, which by default will open a dashboard with a Mock actuators and then show the example Extension interface. 
Now the rest of the coding of your actual extension is up to you!


__ https://github.com/PyMoDAQ/extension_template/tree/main/src/myextension
__ https://github.com/PyMoDAQ/extension_template/blob/main/src/myextension/extension.py
__ https://github.com/PyMoDAQ/extension_template/blob/28403fd9018badb3611f13b8d356514ee2624a08/setup.cfg
__ https://github.com/PyMoDAQ/extension_template/blob/main/src/myextension/__init__.py



Published under the CeCILL-B FREE SOFTWARE LICENSE

GitHub repo: https://github.com/PyMoDAQ/extension_template

