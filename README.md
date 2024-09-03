# µmagick

**µmagick** is a tiny ImageMagick Wrapper that lets you run ImageMagick scripts,
with arguments.

## Usage

```shell
$ umagick
Usage:
  umagick SCRIPT [--verbose] [ARGS...]
  umagick (--help | -h | --version)

Options:
  --verbose, -v  Show the script before running.
  --help, -h     Show this message.
  --version      Show version number.

Arguments:
  SCRIPT         Path to the ImageMagick script file.
  ARGS           key=value pairs to pass to the script.
```

## Writing the scripts

The scripts handled by µmagick are the same scripts you can use directly with
the `magick -script` command, only with these differences:

1. You can use bash `$variables`.
2. You can specify a special comment at the beginning of the file to declare
   what are the arguments this script expects to have.

## Example

Considering [this example script](examples/hello.mgk):

```bash
# examples/hello.mgk
# params: color save

-size 400x400 xc:$color
-write $save
```

Running without arguments, will show the list of needed arguments as determined
by the `params` comment:

```shell
$ umagick examples/hello.mgk
Error: missing 'color'

Usage: umagick examples/hello.mgk color=* save=*
```

Running with all arguments, will execute the cript:

```shell
$ umagick examples/hello.mgk color=red save=out.jpg
```