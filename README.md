![license](https://img.shields.io/badge/License-GPL%20v3-blue.svg)
![pyversion](https://img.shields.io/pypi/pyversions/DisplayCAL.svg)
![pypiversion](https://img.shields.io/pypi/v/DisplayCAL.svg)
![wheel](https://img.shields.io/pypi/wheel/DisplayCAL.svg)

DisplayCAL Python 3 Project
===========================

This project intended to modernize the DisplayCAL code including Python 3 support.

Florian Höch, the original developer, did an incredible job of creating and maintaining
DisplayCAL for all these years. But, it seems that, during the pandemic, very
understandably, he lost his passion to the project. Now, it is time for us, the
DisplayCAL community, to contribute back to this great tool.

This project is based on the ``HEAD`` of the Sourceforge version, which had 5 extra
commits that Florian has created over the ``3.8.9.3`` release on 14 Jan 2020.

Thanks to all the efforts put by the community DisplayCAL is now working with Python
3.9+:

![image](screenshots/DisplayCAL-screenshot-GNOME-3.9.5-running_on_python3.10.png)

Installation Instructions
=========================

Follow the instructions depending on your OS:

- [Windows](docs/install_instructions_windows.md)
- [MacOS](docs/install_instructions_macos.md)
- [Linux](docs/install_instructions_linux.md)

Development (Modern Workflow)
=============================

For day-to-day development and testing, use the `pyproject.toml` + wheel workflow:

```shell
python3 -m venv .venv
source .venv/bin/activate
pip install uv
uv pip install -r requirements-tests.txt -r requirements-dev.txt
python -m build
uv pip install dist/*.whl --force-reinstall
pytest -n auto -W ignore --color=yes
```

Supported Python versions for this project are 3.9 through 3.14. CI currently validates:
- Linux: Python 3.9-3.14
- Windows: Python 3.9-3.11

Default CI and `make tests` runs are deterministic and skip network-marked tests.
To enable network-backed tests locally, set `DISPLAYCAL_ALLOW_NETWORK_TESTS=1`.

The `Makefile` targets (`make venv build install`, `make tests`, `make launch`) are
supported convenience wrappers around this workflow.

Legacy Packaging Paths
======================

Legacy `setup.py`-driven release tasks (for example `py2app` and other platform
specific packaging helpers) are still kept for release engineering needs. Prefer the
modern wheel workflow above for normal development, CI, and bug fixing.

Have fun!
