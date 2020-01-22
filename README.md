# Github Pages Template for IPython Notebooks

This repo contains an adaptation of the [minima theme](https://jekyll.github.io/minima/) that styles IPython notebooks beautifully in GitHub pages.

GitHub Pages uses [Jekyll](https://jekyllrb.com/) as a static site generator. Checkout the [Github Pages Documentation](https://pages.github.com/) for more info.

**Modificatons from Jekyll Minima**

* `_sass/custom.scss`: Custom styles for displaying .ipynb's beautifully

* `_layout/notebook.html`: A custom layout for notebooks

* `_includes/head.html`: Slight modification of minima's `head.html` file to display favicons properly.

* `_notebooks`: folder that contains notebook collections in Jekyll readable format like markdown or html (including `layout: notebook` in front matter)

# Usage Instructions

You have two options for using this theme. Pick the option that best suits you...

## Option 1: I already have my .ipynb files in a jekyll compatible format (html, css) and just want your theme

If this is the case, all you need to do is

* **Enable GitHub Pages:** from your repository go to Settings --> GitHub Pages --> enable GitHub pages on the `master branch` or `master branch /docs` folder

* **Add Remote Theme:** In your `_config.yml`, add this `remote-theme: nancynobody/minima-ipynb`

* **Add your notebooks in html or md format:** Now just put your notebook html or markdown files in a `_notebooks` folder at the root of your GitHub pages site and add an `index.html` or `index.md` and whatever other things you want to your site.

Yay! Now you have Jekyll Minima with customizations for displaying ipython nbs [as shown here](https://nancynobody.github.io/minima-ipynb/).

## Option 2: I just have my .ipynb notebooks in a repo and want to generate the static site directly from those 

So you don't want to convert your .ipynb files to markdown or html manually!? Go figure...I don't blame you. I didn't either.

The following are repos containing notebooks and a GitHub pages site that is displaying them.

* https://github.com/nancynobody/python3_fluency

* https://github.com/nancynobody/data_science_mastery

Your repo will have the following structure when we are done.

* `notebooks/`: contains contains your .ipynb notebooks; here you edit your notebooks just like normal

* `tools_ipynb_to_jekyll/`: contains script tools to convert the .ipynb files in your `notebooks` folder to jekyll compatible so GitHub can display your site.

* `docs/`: folder that contains all site configs

* `docs/_config.yml`: contains site configurations (eg. theme, site title, etc); update site title, description, etc here

* `docs/_notebooks/`: contains the notebooks that have been converted using the `tools_ipynb_to_jekyll.py` script; they contain front matter, site info and notebook content

*Note: Just like any Jekyll theme you can override defaults (like `_sass`, `_layouts`, etc) as desired.*

## Step 1: Setup GitHub Pages

### Create a `docs` folder
This will be the root folder for your site

### Enable GitHub Pages

* Enable github pages [as described here](https://guides.github.com/features/pages/)

* In the `Settings` tab of your repo, point the pages source to be the `docs/` folder rather than the master branch.

:exclamation: Don't chose a theme using the Github GUI! The minima theme is already in the `docs/_config.yml` repo already!

## Step 2: Grab the Convert Tools

From inside your repo add the tools as a git submodule

```bash
git submodule add https://github.com/nancynobody/tools_ipynb_to_jekyll.git
```

*Note: You can also just download the toolset or grab them in any other way you see fit. I just like the submodule method in this case.*

## That's it!

**Updating, adding removing notebooks:** Now you can git add, commit, push to keep your notebooks folder up to date just like you normally would. 

**Building your Site:** When you want to rebuild your site (that is, update all current notebooks on the site using your `notebooks` folder) just run the python script in tools, then git add, commit, push.

**Build Site (based on current `notebooks/`)**
```bash
cd tools
python convert_ipynbs.py

```

# Notes for me

Consider keeping fork up to date occasionally

```bash
git clone
git remote add upstream https://github.com/jekyll/minima.git
git remote -v
# see whats updated, merge (pull, fetch/merge, rebase)
```