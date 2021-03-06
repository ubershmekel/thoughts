# Arity Styles

Function signatures should be concise. Extraneous function parameters are tedious, tedium promotes mistakes. But implicitly changing behaviors can be hard to notice from reading the code. This post is a short exploration into this tension.

## Functional
The most explicit, clear, and controlled. But the API is less ergonomic, less focused and perhaps overly verbose because `is_test` has nothing to do with launching a nuke. The main function of a large program having the sum of all of its descendants' arguments is the extreme case.

```
launch_nuke(nuked_id, target_x, target_y, is_test)
```

## Globals
Easy to guarantee behaviors (e.g. this avoids the potential bug of not passing `is_test` down everywhere), harder to see and predict what the code will do, impossible to thread or cooperatively use multiple different instances, can create bugs where different parts of the program contend for overriding the global.

```
global_config.is_test = is_test
launch_nuke(nuke_id, target_x, target_y)
```

## Mega Class
Conflates unrelated parts of the program.
```
global_config.is_test = is_test
global_config.launch_nuke(nuke_id, target_x, target_y)
```

## Functional Dependency Injection

```
launcher = NukeLauncher(is_test)
launch_nuke(launcher, nuke_id, target_x, target_y)
```

## Constructor Configuration

```
launcher = NukeLauncher(is_test)
launcher.launch_nuke(nuke_id, target_x, target_y)
```

## Branching
May cause code duplication and the tests aren't covering the production code.

```
if is_test:
    test_launch_nuke(nuke_id, target_x, target_y)
else:
    launch_nuke(nuke_id, target_x, target_y)
```

## Personal Preference

It depends but I personally like `Constructor Configuration` and `Globals` the most.
