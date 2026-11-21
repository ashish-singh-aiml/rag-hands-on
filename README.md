# rag-hands-on

## Project Setup

This project uses [uv](https://docs.astral.sh/uv/) to manage Python and its packages. It requires **Python 3.14**.

### 1. Install uv

Skip this step if `uv --version` already works.

**Windows (PowerShell)**

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

**macOS / Linux**

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### 2. Install Python 3.14

```bash
uv python install 3.14
```

### 3. Create the virtual environment and install the packages

From the project root, run:

```bash
uv sync
```

This creates `.venv/` and installs the exact package versions pinned in `uv.lock`.

### 4. Activate the environment (optional)

`uv run <command>` works without activating anything.

**Windows (PowerShell)**

```powershell
.venv\Scripts\activate
```

**macOS / Linux**

```bash
source .venv/bin/activate
```

### 5. Add your API key

Create a `.env` file in the project root:

```
OPENAI_API_KEY=your-key-here
```

Don't commit `.env`.

### 6. Run the notebooks

**VS Code**

1. Open a `.ipynb` file.
2. Click **Select Kernel → Python Environments**.
3. Choose `.venv\Scripts\python.exe` (Windows) or `.venv/bin/python` (macOS / Linux).

**Jupyter in the browser (optional)**

Register the kernel:

```bash
uv run python -m ipykernel install --user --name rag-hands-on --display-name "Python 3.14 (rag-hands-on)"
```

Then start Jupyter. `--with` adds JupyterLab for this one run without adding it to the project:

```bash
uv run --with jupyterlab jupyter lab
```

### Check the setup

```bash
uv run python --version   # should print Python 3.14.x
uv pip list               # lists the packages installed in .venv
```

### Manage packages

```bash
uv add <package>          # add a package to pyproject.toml and .venv
uv remove <package>       # remove a package
uv sync                   # make .venv match uv.lock
```

### Fallback: pip-style setup without pyproject.toml

```bash
uv venv --python 3.14
uv pip install -r requirements.txt ipykernel
```
