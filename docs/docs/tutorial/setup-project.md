# Setup project
> How to create a MkDocs site from scratch

This is a summary of the tutorial on [mkdocs.org](https://www.mkdocs.org/).


## How to use this guide

Use one of the approaches below:

- Create a quickstart project with the `new` command covered in [Create a starter site](#create-a-starter-site).
- Follow the extended guide to create a [Setup up docs site](#setup-a-docs-site) by hand.


### Basic structure

This is the simplest MkDocs site you can make:

- `docs/`
    - `index.md` - Homepage in the `docs` directory (by default).
- `mkdocs.yml` 
    - Config at the root - control appearance and navigation of your site.
    - See this project's [docs/mkdocs.yml](https://github.com/MichaelCurrin/mkdocs-quickstart/blob/master/docs/mkdocs.yml) file on GitHub.
    
Notes on fields for the config:

- `site_name` - title of your site.
- `site_description` - used as a description for SEO and you could use it somewhere in your template.
- `repo_url` - for _Edit on GitHub_ button.


### Requirements file

A requirements file is optional but it can make it easier to manage dependencies. If you choose not use the file, make sure `pip install mkdocs` and `pip install THEME` lines are your instructions.

If you want to add, then include `requirements.txt` at the root. If your project is already a Python project, you might prefer to add `mkdocs` in `requirements-dev.txt` or at `docs/requirements.txt` to keep it isolated.This file should have `mkdocs` in it and also any themes if needed.


### Create a starter site

Run this command to create a starter site. This make the steps below go quicker.

```sh
cd my-project
mkdocs new PATH
```

The result will be same as the [Basic structure](#basic-structure) defined above and will include minimal text content generated by the MkDocs CLI. This text is defined in the project's [new.py](https://github.com/mkdocs/mkdocs/blob/master/mkdocs/commands/new.py) module.

### Setup a docs site

_Tip: Optionally use the `new` command covered above to setup the config and index page first and then continue_.

1. Create doc pages.
    1. Create a `docs` directory.
    2. Create `index.md` as your homepage.
    3. Create other markdown pages (optional).
        - Use placeholder content if you want to move on and then come back to expand them.
        - If you have any existing markdown docs, these will work too.
2. Set up config.
    1. Create `mkdocs.yml` at the project root.
    2. Set up a navbar there.
    3. Choose a theme.
3. Create a favicon (optional).
    - It will be picked up at this path: `docs/img/favicon.ico`.
4. Add to your `.gitignore`.
    - Add build directory. This will prevent it from being versioned on `master` branch.
    - Add virtual environment, if using one.

You project should now look this this:

- `docs/`
    - `index.md`
    - More pages...
- `mkdocs.yml`
- `.gitignore`
- `venv`
- `requirements.txt` - optional


## Sample content

### Ignore file

`.gitignore`
```
site/

venv
```

### Navbar

`mkdocs.yml`
```yaml
nav:
    - Home: index.md
    - About: about.md
```

### Themes

#### Builtin

Use a builtin theme that comes with MkDocs.

The default.

```yaml
theme: mkdocs
```

Using ReadTheDocs theme and alternative config syntax.

```yaml
theme:
  name: readthedocs
```

Find more [supported themes](https://github.com/mkdocs/mkdocs/wiki/MkDocs-Themes). If it doesn't immediately, you'll have to use `pip` to install it and add to a `requirements.txt` file.

#### ReadTheDocs Dropdown theme

See below using [mkdocs-rtd-dropdown](https://github.com/cjsheets/mkdocs-rtd-dropdown).

`requirements.txt`:
```
mkdocs-rtd-dropdown
```

`mkdocs.yml`:

```yaml
theme:
  name: 'rtd-dropdown'
```

### Material for MkdDocs theme

See the [MkDocs for Material](https://squidfunk.github.io/mkdocs-material/) homepage. See the Setup page for config options.

`requirements.txt`:
```
mkdocs-material-extensions>=1.0
```

`mkdocs.yml`:
```yaml
theme:
  name: 'material'
```