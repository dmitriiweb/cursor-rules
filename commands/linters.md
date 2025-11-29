
Run linters with the following commands:
for format code:
make format

for linters and mypy:
make lint

fix linters errors firstly if they happend
than run make lint one more time
fix mypy issues if the exist - if need to install new pacckage add with uv to dev section (look into pyproject.toml) needed library and never use mypy install missing libraries command
