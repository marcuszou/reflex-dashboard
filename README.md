# Welcome to Reflex - Interactive Dashboard!

Powered by [reflex.dev](https://reflex.dev/)



## Dashboard

Interactive dashboard with real-time data visualization

The following is a dashboard to interactively display data some data. It is a good starting point for building more complex apps that require data visualization.

### Setup

Install reflex in a venv

```shell
pip install reflex
```



To run this app locally, install Reflex and run:

```
reflex init --template dashboard
```



To run the app, use:

```
reflex run
```



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
