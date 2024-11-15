# Welcome to Reflex - Interactive Dashboard!

Powered by [reflex.dev](https://reflex.dev/)



## Dashboard

Interactive dashboard with real-time data visualization

The following is a dashboard to interactively display data some data. It is a good starting point for building more complex apps that require data visualization.

## Tech Stack

- Python 3.12

- Reflex 0.5.5+, currently 0.6.4

- Pandas

  BTW - I am on Ubuntu 24.04.



## Getting Started

1. Basic setup

   ```shell
   ## Update and Upgrade
   sudo apt update && sudo apt upgrade -y
   ## Install the virtualenv tool and unzip
   sudo apt install python3.12-venv unzip
   ## Install the `bun` module for later use (Linux and macOS)
   curl -fsSL https://bun.sh/install | bash
   ## activate the .bashrc to make sure bun is accessible
   source ~/.bashrc
   ```

2. Create venv and give a go

   ```shell
   ## Make project directory
   mkdir reflex-dasnboard
   cd reflex-dashboard
   ## create a venv named as 'venv'
   python3 -m venv .venv
   ## activate it
   source .venv/bin/activate
   ## list the modules in the venv (only 'pip' itself)
   pip list
   ## Optuioally upgrade pip
   pip install --upgrade pip
   
   ## Ensure the python3 and pip are from the .venv, not the /usr/bin/
   which python3
   which pip
   ```

   Note: <font color="red">The ops below are in the Virtual Environment.</font>

3. Install the monster - Reflex

   ```shell
   ## This takes quite a while as many modules pop in
   pip install reflex==0.6.4
   ## check them out
   pip list
   ```

4. Give a go

   ```shell
   reflex init --template dashboard
   ```

   It will prompt you some templates to select with, choose the one represents 'NBA'. 

   And the process will generate quite a few files in the project folder.

5. Install some extra python modules: pandas, numpy, etc. (please do)

   ```shell
   ## edit requirements.txt file ensuring the version of reflex == 0.6.4 (>=0.5.5)
   ## because the latest version 0.6.5 is very buggy as of November 12, 2024.
   pip install -r requirements.txt
   ```

6. Start up the Reflex App

   ```shell
   reflex run
   ## In macOS, It may complain no permission to run/install ...bun_install.sh 
   ```

   Please install `bun` package (`curl -fsSL https://bun.sh/install | bash`) if you confront a warning like:

   > Warning: There was an error running command: ['/home/zenusr/.local/share/reflex/bun/bin/bun', 'install'].
   >
   > Warning: There was an error running command: ['/home/zenusr/.local/share/reflex/bun/bin/bun', 'add',...

   Eventually, you will be presented with:

   > App running at: http://localhost:3000 
   >
   > Backend running at: http://0.0.0.0:8000

7. Enjoy the show.



### Customizing to your data

Right now the apps reads from a local CSV file. You can modify this by changing the `DATA_FILE` variable in the `dashboard/dashboard/backend/table_state.py` file.

Additionally you will want to change the `Item` class to match the data in your CSV file.

```
import dataclasses

@dataclasses.dataclass
class Item:
    """The item class."""

    name: str
    payment: float
    date: str
    status: str
```



## Push the Project to GitHub

1. Create a empty repository on your GitHub space, named as, say `nba-data-dash`.

2. Edit the `.gitignore` file to exclude the `venv` folder.

3. Commit and Push to the repo:

   ```shell
   ## Add data files in
   git add .
   ## Commit
   git commit -m "nba-data"
   ## channel it to master - sorry not a fan of main
   git branch -M master
   ## conenct to remote repo
   git remote add origin https://github.com/marcuszou/nba-data-dash.git
   ## Push the project files
   git push -u origin master
   ```

   



# Welcome to Reflex!

This is the base Reflex template - installed when you run `reflex init`.

If you want to use a different template, pass the `--template` flag to `reflex init`.
For example, if you want a more basic starting point, you can run:

```bash
reflex init --template blank
```

## About this Template

This template has the following directory structure:

```bash
├── README.md
├── assets
├── rxconfig.py
└── {your_app}
    ├── __init__.py
    ├── components
    │   ├── __init__.py
    │   ├── navbar.py
    │   └── sidebar.py
    ├── pages
    │   ├── __init__.py
    │   ├── about.py
    │   ├── index.py
    │   ├── profile.py
    │   ├── settings.py
    │   └── table.py
    ├── styles.py
    ├── templates
    │   ├── __init__.py
    │   └── template.py
    └── {your_app}.py
```

See the [Project Structure docs](https://reflex.dev/docs/getting-started/project-structure/) for more information on general Reflex project structure.

### Adding Pages

In this template, the pages in your app are defined in `{your_app}/pages/`.
Each page is a function that returns a Reflex component.
For example, to edit this page you can modify `{your_app}/pages/index.py`.
See the [pages docs](https://reflex.dev/docs/pages/routes/) for more information on pages.

In this template, instead of using `rx.add_page` or the `@rx.page` decorator,
we use the `@template` decorator from `{your_app}/templates/template.py`.

To add a new page:

1. Add a new file in `{your_app}/pages/`. We recommend using one file per page, but you can also group pages in a single file.
2. Add a new function with the `@template` decorator, which takes the same arguments as `@rx.page`.
3. Import the page in your `{your_app}/pages/__init__.py` file and it will automatically be added to the app.
4. Order the pages in `{your_app}/components/sidebar.py` and `{your_app}/components/navbar.py`.


### Adding Components

In order to keep your code organized, we recommend putting components that are
used across multiple pages in the `{your_app}/components/` directory.

In this template, we have a sidebar component in `{your_app}/components/sidebar.py`.

### Adding State

As your app grows, we recommend using [substates](https://reflex.dev/docs/substates/overview/)
to organize your state.

You can either define substates in their own files, or if the state is
specific to a page, you can define it in the page file itself.
