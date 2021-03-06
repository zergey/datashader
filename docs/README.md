See https://ioam.github.io/nbsite/Usage.html for more details.

0. Set up environment so you can run the examples

1. Install nbsite: `conda install -c conda-forge sphinx beautifulsoup4
   graphviz numpydoc && pip install sphinx_ioam_theme nbsite`

2. `cd docs`

3. Generate rst containers for notebooks:
   `nbsite_nbpagebuild.py bokeh datashader ../examples .`

4. Build site: `sphinx-build -b html . ./_build/html` followed by
   `nbsite_fix_links.py _build/html`

5. Inspect result: `pushd _build/html && python -m http.server`

6. Clean up for deployment: `nbsite_cleandisthtml.py ./_build/html take_a_chance`

7. Deploy to S3 bucket: `pushd _build/html && aws s3 sync --delete --acl public-read . s3://datashader.org`
