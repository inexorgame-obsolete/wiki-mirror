# Specification

A sleep node waits `sleep_interval` miliseconds before code execution continues.

## Constructors
TODO

## Destructors
TODO

## Members
```
unsigned int sleep_interval;
unsigned int sleep_start;
unsigned int sleep_end;
```

## Methods
TODO

## Minimum and Maximum Values

```
#define INEXOR_VSCRIPT_MIN_SLEEP_INTERVAL 10
#define INEXOR_VSCRIPT_MAX_SLEEP_INTERVAL 1000 * 60 * 60 * 24  // 1 day
```
