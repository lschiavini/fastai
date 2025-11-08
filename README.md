# running jupyter notebooks

# UV
## Setting up environment

1. install uv
   uv installation options

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
``` 

2.install a specific version

```bash
curl -LsSf https://astral.sh/uv/0.6.1/install.sh | sh
 ```

3. wget instead of curl

```bash
wget -qO- https://astral.sh/uv/install.sh | sh
```

4. check it's running

```bash
uv
```

5. shell autocompletion

```bash
echo 'eval "$(uv generate-shell-completion bash)"' >> ~/.bashrc
```

6. install python

```bash
uv python install
uv python install 3.10 # defaults to lastest
```

## Running uv

1. run script

```bash
uv run script-name.py
```

2. check available versions

```bash
uv python list
```

## Isolated Virtual Envs

1. set up and activate environment

```bash
uv venv --python 3.11
source .venv/bin/activate
```

2. init project with specific version

```bash
uv init my-project --python 3.10
```

## Managing deps

1. installing deps

```bash
uv pip install dependency-name-opt-version
uv add dependency-name-opt-version
```

2. sync(in case a dep was manually added to `pyproject.toml`)

```bash
uv sync
```


# Jupyter Notebooks

1. install 
```bash
uv pip install notebook
```

Next, give your uv project a dedicated python kernel. This keeps any project-level installed packages isolated within the project environment.

If you haven’t already set up ipykernel as a dev dependency, do that first (this needs to be done only once, or if your dev env needs refreshing):

2. python kernel
```bash
uv add --dev ipykernel
```

Then run the following on a per project basis
``` bash
uv run ipython kernel install --user --env VIRTUAL_ENV $(pwd)/.venv --name=<project>
```
3. finally, run the notebook 
```bash
uv run --with jupyter jupyter lab
```


from https://monicaspisar.com/posts/ghostty-plus-uv/