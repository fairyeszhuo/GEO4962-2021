---
title: "Jupyterhub"
teaching: 0
exercises: 0
questions:
- "How to get access to Jupyterhub?"
- "How to start/stop Jupyter notebooks in the Jupyterhub?"
objectives:
- "Learn about Jupyterhub"
keypoints:
- "Jupyterhub"
---

*   [Introduction to Jupyterhub and JupyterLab](#introduction-to-jupyterhub-and-jupyterlab)
  * [Setup instructions for accessing Jupyterhub](#Setup-instructions-for-accessing-Jupyterhub)
	* [Login to the JupyterHub](#login-to-the-jupyterhub)
	* [Start and stop your server](#start-and-stop-your-server)
	* [JupyterLab](#jupyterlab)
  

# Introduction of Jupyterhub

The CMIP6 data analysis will be conducted directly at [jupyterhub](https://jupyter.org/hub). We will be using [https://geo4962.tacco.sigma2.no/](https://geo4962.tacco.sigma2.no/).
The main advantage of this is that all the data we need are directly accessible through the web 
interface and the necessary post-processing and visualization packages we need are already available.   



##  Setup instructions for accessing Jupyterhub

- You should have received an info email containing an invitation link. If not please request it to the course organizers.
- Follow the invitation link in the email message
- If you don't already have a Feide guest user account click "Feide guest users". (If you already have a Feide guest user account, skip this step)
    - register a new account (do not use your UiO username as it may be confusing for everyone).
    - finish the registration process
    - click again on the "invitation link" in the email
- Login with "Feide guest users"
- Accept the different policies
- Agree to become a member of the **NS1004K**: the browser should display the message "Loading group details"
- Now go to [GEO4962 Jupyterhub](https://geo4962.tacco.sigma2.no/)
- Click "Sign in with Dataporten"
- Login with Feide Guest User (Not your UiO username)
- Finally the web browser should display a page with "jupyterlab" on the upper left side

For later usage of the notebooks just use the [GEO4962 Jupyterhub link](https://geo4962.tacco.sigma2.no/)

## Login to the JupyterHub

<img src="../fig/jupyterhub_login.png" width="500">

- Click on **Dataporten**

<img src="../fig/jupyterhub_login2.png" width="500">

- **Do not use your Feide user account, so click on **Can't find your user account?**

- In **Other login alternatives**, click on **Feide guest users**

<img src="../fig/jupyterhub_feide_guest.png" width="500">

- Use the username and password you have received and **sign In**.

<img src="../fig/jupyterhub_feide_guest2.png" width="500">

> ## Tips
> Before getting to the username/password login page, your browser may warn you about the security
> of the website and get a message such as "This site is not secure". In order to bypass this security message,
> you need to accept to proceed. Let us know if you still have problems to login.
>
{: .callout}
 
## Start and stop your server

When you manage to successfully login to the Jupyterhub, you should have the following panels:

<img src="../fig/jupyterhub_panels.png" width="600">

To start/stop your server, click on **Hub Control Panel**:

<img src="../fig/jupyterhub_start_stop_server.png" width="600">

When your server is not running, the button "Stop My Server" does not appear and you only see the button "My Server".

- To stop your server, click on "Stop My Server"
- To start your server, click on "My Server"

> ## Important note
>
> Make sure you stop your server once you have finished your session. We need to do this to release resources for next time. 
>
{: .callout}

## The JupyterLab Interface

By default, you will get the web-based user interface for Project Jupyter that is called [JupyterLab](https://jupyterlab.readthedocs.io/en/stable/).


<img src="../fig/jupyterlab.png" width="600">

### Menu Bar

The menu bar at the top of JupyterLab has top-level menus that expose actions available in JupyterLab with 
their keyboard shortcuts. The default menus are:

- **File**: actions related to files and directories
- **Edit**: actions related to editing documents and other activities
- **View**: actions that alter the appearance of JupyterLab
- **Run**: actions for running code in different activities such as notebooks and code consoles
- **Kernel**: actions for managing kernels, which are separate processes for running code
- **Tabs**: a list of the open documents and activities in the dock panel
- **Settings**: common settings and an advanced settings editor
- **Help**: a list of JupyterLab and kernel help links

### Left Sidebar

The left sidebar contains a number of commonly-used tabs, such as a file browser, a list of running 
kernels and terminals, the command palette, and a list of tabs in the main work area:

<img src="../fig/jupyterlab_file_browser.png" width="600">

If you move your mouse on the other icon of this left sidebar, a short information is given on its functionality.

If you click on the "stop button" icon, you can see what is currently running on your server and you can click on 
"SHUT DOWN" to stop a running Python notebook or Terminal.

<img src="../fig/jupyterlab_running.png" width="600">

### Start a new Terminal

Similarly, you can start a new Terminal by clicking on "Terminal" in the Launcher. 

<img src="../fig/jupyterlab_start_terminal.png" width="500">


> ## Tips
> If the **Launcher** tab does not exist 
> anymore in your JupyterLab, you can start a new one in "**File** --> **New Launcher**".
{: .callout}

### Create a new python 3 notebook

Go back to the **File Browser** left sidebar tab and in the launcher select **Python 3** under the Notebook 
section:

<img src="../fig/jupyterlab_start_notebook.png" width="500">

By default, your new notebook is named as "**Untitled.ipynb**":

- **ipynb** is the extension for any Jupyter notebook and you should make sure all your notebooks get this extension (otherwise it is not recognized as a Jupyter notebook)
- you can rename your jupyter notebook with the tab "File --> Rename Notebook..." or 
  right click on its name.


### Getting help in a jupyter notebook

Python (general and available outside jupyter notebook)

In addition to online help, you can use `help` function:

~~~
import matplotlib
help(matplotlib)
~~~
{: .language-python}


The Jupyter Notebook has two ways to get help:

- Place the cursor inside the parentheses of the function, hold down shift, and press tab.
- Or type a function name with a question mark after it.

{% include links.md %}

