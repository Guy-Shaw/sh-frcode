# sh-frcode

### Homan-readable, shell-executable front-compression

`sh-frcode` does GNU-frcode-style front-compression on a list of paths,
but produces a human-readable shell script, which defines
some variable names and compresses the paths by doing
inverse shell variable substitution.

### Input

  1. A list of shell variable assignments;
  2. A list of pathnames.

Neither list need be sorted, because what compression there is
relies solely on the defined variables and their values, and how
much space is saved by doing shell variable substitution;
not based on any other context;
not based on automatic detection of dictionary entries,
and not based on back-references to previous paths or locality of any kind.

### Output

A shell script, consisting of:

  1. Assignments to variable names;
  2. One or more 'cat' commands, with input from a shell "here document".

The resulting shell script, when executed,
produces the original (uncompressed) list of pathnames,
exactly.

### Why

Binary compression has its disadvantages.

You need to be sure you have the correct compression / decompression
software on your system.

The result is not directly usable.

You cannot just look at the result and see what is going on.

But, with `sh-frcode` compression, you just need a shell
that knows about here documents.

The results are easy to view directly,
without running the decompressor.

In fact, the resulting compressed version of a list
of pathnames _can_ be even easier to view than the original,
provided the variable names for path prefixes are meaningful.

At times, I have used `sh-frcode` for compression,
not because I feel the need to save disk space,
but because the result is easier to view on a screen,
or just easier to read, in general.

I have applied `sh-frcode`
(or something like it)
to the result of builds using `make`,
just to make it easier to read the `make` log.

I use things like:
  1. `WS` for workspace
  2. `SRC` for top of source code
  3. `BLD` for the top of the build output
  4. `LIB` for a library directory,

etc.

The output of `sh-frcode` can easily be commented,
annotated, reformatted in ways to make it more readable.
This can often be done in ways that do not alter the
outcome of the decoding.  Or, if it does, the differences
are trivial, and can be handled by a `sed` one-liner.



## Example

The examples directory has an example of a project workspace.
It is a real-world example, except a company name was "sanitized".

To run the example and verify that the decompress(compress)
gives back the original data, just run `make` in the examples
directory.

## License

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU Lesser General Public License as
published by the Free Software Foundation; either version 3 of the
License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
Lesser General Public License for more details.

You should have received a copy of the GNU Lesser General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.

##

-- Guy Shaw

   gshaw@acm.org

