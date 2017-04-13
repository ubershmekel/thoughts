# Arity Styles

## Functional

launch_nukes(nuked_id, target_x, target_y, is_test)

## Python globals

```
global_config.is_test = is_test
launch_nuke(nuke_id, target_x, target_y)
```

# Python Mega Class

```
global_config.is_test = is_test
global_config.launch_nukes(nuke_id, target_x, target_y)
```

# Python Configuration in Constructor

```
launcher = NukeLauncher(global_config)
launcher.launch_nukes(nuke_id, target_x, target_y)
```
