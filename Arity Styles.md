# Arity Styles

## Functional
The most explicit, clear, and controlled. But the API is less ergonomic, less focused and overly verbose.
```
launch_nukes(nuked_id, target_x, target_y, is_test)
```

## Globals
Easy to arrange, harder to see and predict what the code will do.
```
global_config.is_test = is_test
launch_nuke(nuke_id, target_x, target_y)
```

## Mega Class
Conflates unrelated parts of the program.
```
global_config.is_test = is_test
global_config.launch_nukes(nuke_id, target_x, target_y)
```

## Functional Dependency Injection

```
launcher = NukeLauncher(is_test)
launch_nukes(launcher, nuke_id, target_x, target_y)
```

## Constructor Configuration

```
launcher = NukeLauncher(is_test)
launcher.launch_nukes(nuke_id, target_x, target_y)
```

## Branching
May cause code duplication and the tests aren't covering the production code.

```
if is_test:
    test_launch_nukes(nuke_id, target_x, target_y)
else:
    launch_nukes(nuke_id, target_x, target_y)
```
