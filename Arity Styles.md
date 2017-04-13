# Arity Styles

## Functional

```
launch_nukes(nuked_id, target_x, target_y, is_test)
```

## Globals

```
global_config.is_test = is_test
launch_nuke(nuke_id, target_x, target_y)
```

# Mega Class

```
global_config.is_test = is_test
global_config.launch_nukes(nuke_id, target_x, target_y)
```

# Dependency Injection

```
launcher = NukeLauncher(is_test)
launch_nukes(launcher, nuke_id, target_x, target_y)
```

# Configuration or injection in Constructor

```
launcher = NukeLauncher(is_test)
launcher.launch_nukes(nuke_id, target_x, target_y)
```

