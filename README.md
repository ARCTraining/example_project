# Steps

An example data science project to demonstrate GitHub.

## 1. [Create a GitHub repository](https://docs.github.com/en/get-started/quickstart/create-a-repo)  

- [Version control (Software Carpentry)](https://swcarpentry.github.io/git-novice/)
- [Version control (The Alan Turing Institute)](https://alan-turing-institute.github.io/rse-course/html/module04_version_control_with_git/04_00_introduction.html)

## 2. [Create a conda environment](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#creating-an-environment-with-commands)  

For example:

```bash
conda create -n example_project -c conda-forge python==3.8.* jupyterlab jupyter-book numpy cookiecutter pytest
conda activate example_project
```    

If want to use Jupyter Lab for development, then create a kernel for this environment:
```bash
python -m ipykernel install --user --name example_project --display-name "example_project"
```

## 3. Create a structure for the project

For example, using [cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) and the [data science template](https://github.com/drivendata/cookiecutter-data-science):

```bash
cookiecutter -c v1 https://github.com/drivendata/cookiecutter-data-science
# fill in details
cd example_project
```    

### Project Organization

    ├── LICENSE
    ├── Makefile           <- Makefile with commands like `make data` or `make train`
    ├── README.md          <- The top-level README for developers using this project.
    ├── data
    │   ├── external       <- Data from third party sources.
    │   ├── interim        <- Intermediate data that has been transformed.
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   └── raw            <- The original, immutable data dump.
    │
    ├── docs               <- A default Sphinx project; see sphinx-doc.org for details
    │
    ├── models             <- Trained and serialized models, model predictions, or model summaries
    │
    ├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
    │                         the creator's initials, and a short `-` delimited description, e.g.
    │                         `1.0-jqp-initial-data-exploration`.
    │
    ├── references         <- Data dictionaries, manuals, and all other explanatory materials.
    │
    ├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
    │   └── figures        <- Generated graphics and figures to be used in reporting
    │
    ├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
    │                         generated with `pip freeze > requirements.txt`
    │
    ├── setup.py           <- makes project pip installable (pip install -e .) so src can be imported
    ├── src                <- Source code for use in this project.
    │   ├── __init__.py    <- Makes src a Python module
    │   │
    │   ├── data           <- Scripts to download or generate data
    │   │   └── make_dataset.py
    │   │
    │   ├── features       <- Scripts to turn raw data into features for modeling
    │   │   └── build_features.py
    │   │
    │   ├── models         <- Scripts to train models and then use trained models to make
    │   │   │                 predictions
    │   │   ├── predict_model.py
    │   │   └── train_model.py
    │   │
    │   └── visualization  <- Scripts to create exploratory and results oriented visualizations
    │       └── visualize.py
    │
    └── tox.ini            <- tox file with settings for running tox; see tox.readthedocs.io

## 4. [Initialise the repository](https://docs.github.com/en/get-started/importing-your-projects-to-github/importing-source-code-to-github/adding-an-existing-project-to-github-using-the-command-line)

For example:

```bash
git init
git add .
git commit -am "Initialising repository"
git branch -M main
git remote add origin git@github.com:username/example_project.git
git push -u origin main
```    

## 5. Create the [documentation](https://www.software.ac.uk/blog/2019-06-21-what-are-best-practices-research-software-documentation)

For example, using [Jupyter Book](https://jupyterbook.org/start/your-first-book.html):

```bash
rm -rf docs # as the default within the template uses Sphinx

jupyter-book create docs

jupyter-book build docs

git add docs
git commit -am "Adding documentation"
git push
```

Can view the documentation locally by viewing the file `docs/_build/html/intro.html` within a browser.

## 6. Add code and data

- Source code: [`src/`](https://github.com/ARCTraining/example_project/tree/main/src) 
- Jupyter notebooks: [`notebooks/`](https://github.com/ARCTraining/example_project/tree/main/notebooks) 
- Data: [`data/`](https://github.com/ARCTraining/example_project/tree/main/data)    

## 7. Add [tests](https://alan-turing-institute.github.io/rse-course/html/module05_testing_your_code/05_00_introduction.html)

For example, [`pytest`](https://docs.pytest.org/en/6.2.x/):

```bash
mkdir tests
```

Create files within `tests/` e.g., `test_example.py`:

```python
def increment_by_one(x):
    return x + 1


def test_increment_by_one():
    assert increment_by_one(3) == 4
    
```

Then run pytest in the terminal:

```bash
$ pytest
================================================ test session starts ================================================
platform linux -- Python 3.10.2, pytest-7.0.0, pluggy-1.0.0
rootdir: /home/earlacoa/repos/example_project
plugins: anyio-3.5.0
collected 1 item                                                                                                    

tests/test_example.py .                                                                                       [100%]

================================================= 1 passed in 0.02s =================================================
```

## 8. Automate your workflow

For example, using [GitHub Actions](https://github.com/features/actions), see [`.github/workflows/deploy.yml`](https://github.com/ARCTraining/example_project/blob/main/.github/workflows/deploy.yml).

## 9. [Capture your environment](https://the-turing-way.netlify.app/reproducible-research/renv.html)

For example, using [conda](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#sharing-an-environment):

```bash
conda env export --name example_project > environment.yml

rm -f requirements.txt # alternate method

git add environment.yml
git commit -am "Adding conda environment"
git push
```

## 10. [Choose a software license](https://the-turing-way.netlify.app/reproducible-research/licensing.html)

- Create/update the [`LICENSE`](https://github.com/ARCTraining/example_project/blob/main/LICENSE) file

## 11. Update [README](https://the-turing-way.netlify.app/project-design/project-repo/project-repo-readme.html)

- Describe project
- Steps to reproduce
- Key resources
- How to cite
- How to contribute

## 12. Publish online

For example, using [GitHub Pages](https://pages.github.com/) (for a [Jupyter Book](https://jupyterbook.org/start/publish.html)):

- Settings > Pages > Source = `Branch: gh-pages`, Folder = `/docs`.

Now, viewable [here](https://arctraining.github.io/example_project/).

## 13. [Release your project and make it citable](https://the-turing-way.netlify.app/communication/citable.html)

- [Create the release](https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository)
- [Cite it](https://docs.github.com/en/repositories/archiving-a-github-repository/referencing-and-citing-content) using [Zenodo](https://zenodo.org/)
    - [Create](https://the-turing-way.netlify.app/communication/citable/citable-cff.html#) the [`CITATION.cff`](https://github.com/ARCTraining/example_project/blob/main/CITATION.cff) file
