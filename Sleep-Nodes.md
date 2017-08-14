# Specification

A sleep node waits `sleep_interval` miliseconds before code execution continues.

## Class hierarchy

**CSleepNode** inherits from **CScriptNode**.

## Class Members:
```
unsigned int sleep_interval;
unsigned int sleep_start;
unsigned int sleep_end;
```

## Minimum and Maximum Values

```
#define INEXOR_VSCRIPT_MIN_SLEEP_INTERVAL 10
#define INEXOR_VSCRIPT_MAX_SLEEP_INTERVAL 1000 * 60 * 60 * 24  // 1 day
```

## Constructor
TODO

## Destructor
TODO

## Methods
TODO
