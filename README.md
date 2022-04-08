# actions-python-poetry
GH Actions that setups Python and Poetry with cache.

Optionally also setups Nexus package registry.

How to use
```yaml
jobs:
  Linting:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Install python and poetry
        uses: ./.github/actions/python-poetry
        with:
          python-version: '3.9'
          nexus-user: ${{ secrets.NEXUS_USER }}  # optional
          nexus-password: ${{ secrets.NEXUS_PASSWORD }}  # optional

      - name: Install dependencies
        run: poetry install

      - name: Install dependencies
        run: poetry run pytest --cov=src --color=yes tests/
```

To setup nexus in your repostiory use

```toml
[[tool.poetry.source]]
name = "facily"
url = "https://nexus.faci.ly/repository/facily-pypi-group/simple/"
```
