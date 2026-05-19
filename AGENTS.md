# Repository Guidelines

## Project Structure & Module Organization

`crisp_gym/` contains the Python package. Core Gymnasium environments live in `crisp_gym/envs/`, policy adapters in `crisp_gym/policy/`, teleoperation helpers in `crisp_gym/teleop/`, dataset recording utilities in `crisp_gym/record/`, and CLI entry points in `crisp_gym/scripts/`. YAML defaults are under `crisp_gym/config/`; these may be extended through `CRISP_CONFIG_PATH`. Static assets are in `media/`, examples are in `examples/`, and setup scripts are in `scripts/`.

## Build, Test, and Development Commands

- `pixi run configure`: run repository setup via `scripts/configure.sh`.
- `pixi shell -e humble` or `pixi shell -e humble-lerobot`: enter a ROS/LeRobot development environment.
- `pixi run ruff check .`: lint Python files using the configured Ruff rules.
- `pixi run ruff format .`: format Python files.
- `crisp-check-config`: inspect active CRISP config search paths.
- `crisp-record-leader-follower --help`: view teleop recording options.
- `crisp-deploy-policy --help`: view policy deployment and recording options.

Use `humble-lerobot` or `lerobot` environments for code paths importing `lerobot`.

# Hardware safety

Never run commands within the ros2 environement that move the real robot, activate real controllers,
switch controllers, command effort/torque, or connect to the Franka FCI
unless explicitly instructed.

Safe commands:
- colcon build
- colcon test
- ros2 pkg list
- ros2 interface show
- ros2 launch ... only for simulation
- ros2 topic list
- ros2 node list

## Coding Style & Naming Conventions

Python targets 3.11. Use 4-space indentation, double quotes, and a 100-character line length, matching `pyproject.toml`. Ruff enforces import sorting, pydocstyle Google docstrings, and type annotation rules. Prefer dataclasses for configuration objects and factory functions named `make_*` for constructed runtime objects, following existing patterns such as `make_env`, `make_policy`, and `make_recording_manager`.

Keep ROS topic, config, and observation key names explicit and stable. Dataset-facing observation keys should follow the existing `observation.state.*` and `observation.images.*` patterns.

## Testing Guidelines

There is currently no dedicated `tests/` directory. Do not add tests unless specifically requested by the user. Instead, check changes using safe commands.

## Commit & Pull Request Guidelines

Recent history uses short imperative commit subjects, sometimes with conventional prefixes, for example `Update config`, `fix sub failure`, and `chore(main): release 4.2.1`. Keep subjects concise and action-oriented; use prefixes like `fix:`, `feat:`, or `chore:` when helpful.

Pull requests should describe the behavior change, list validation commands, mention affected configs or ROS namespaces, and link related issues. Include screenshots or logs only when they clarify config discovery, recording, or deployment behavior.

## Configuration & Safety Notes

Do not hard-code local robot paths or private dataset IDs. Prefer YAML configs resolved by `CRISP_CONFIG_PATH`. Be careful when changing controller names, gripper modes, action dimensions, or LeRobot feature schemas; those are compatibility boundaries for deployed robots and recorded datasets.