# µmagick - Tiny ImageMagick Wrapper

This wrapper lets you run ImageMagick scripts, with variable substitution.

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

## Example

Running the [example script](example/script.mgk):

```shell
$ umagick example/script.mgk
Error: missing 'background'

Usage: umagick example/script.mgk background=* save=*

$ umagick example/script.mgk background=SkyBlue save=out.jpg
# => Image saved
```