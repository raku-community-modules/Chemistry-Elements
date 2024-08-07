[![Actions Status](https://github.com/raku-community-modules/Chemistry-Elements/actions/workflows/linux.yml/badge.svg)](https://github.com/raku-community-modules/Chemistry-Elements/actions) [![Actions Status](https://github.com/raku-community-modules/Chemistry-Elements/actions/workflows/macos.yml/badge.svg)](https://github.com/raku-community-modules/Chemistry-Elements/actions)

NAME
====

Chemistry::Elements - do things with the Periodic Table

SYNOPSIS
========

    use Chemistry::Elements;

    put "Name for 37 is ", get_name_by_Z( 37 );
    put "Name for Rb is ", get_name_by_symbol( 'Rb' );

    put "Symbol for 37 is ", get_symbol_by_Z( 37 );
    put "Symbol for Rubidium is ", get_symbol_by_name( 'Rubidium' );
    put "Symbol for Rubidium is ", get_symbol_by_name( 'Rubidium',  );

    put "Atomic number for Rb is ", get_Z_by_symbol( 'Rb' );
    put "Atomic number for Rubidium", get_Z_by_name( 'Rubidium' );

    # use a German name
    put "Atomic number for Rubidium is ", get_symbol_by_name( 'Schwefel', 'de'  );

    # Use some types

    my ZInt $Z    = 37; # works
    my ZInt $BigZ = 138; # nope, because that's not on the chart (yet)
    my $minimum = min_Z(); # Always 1, unless something big changes
    my $maximum = max_Z(); # More

    my ChemicalSymbol $symbol       = 'Rb'; # okay
    my ChemicalSymbol $other_symbol = 'X9'; # not okay, not a known symbol

DESCRIPTION
===========

The Perl version of `Chemistry::Elements` was my first module, so I'm making it my first Raku module too. It's not complicated.

The module maps between element names (_e.g._ Rubidium), symbol (_e.g._ Ru ), and number (_e.g._ 37). It's multi-language aware although the language switching isn't sophisticated yet.

class Chemistry::Elements
-------------------------

Do various things with chemical elements. Convert between symbols, names, and atomic numbers.



A Str that is one of the known chemical symbols

### method max_Z

```raku
method max_Z() returns Chemistry::Elements::ZInt
```

Return the maximum recognized atomic number (as a ZInt type).

### method min_Z

```raku
method min_Z() returns Chemistry::Elements::ZInt
```

Return the minimum recognized atomic number. This is always be 1 (as a ZInt type).



A Str that is one of the known chemical symbols

### method get_name_by_Z

```raku
method get_name_by_Z(
    Chemistry::Elements::ZInt(Cool) $Z,
    Str:D $lang = "default"
) returns Str:D
```

Return the element name by the atomic number. You can pass an untyped number or a ZInt

### method get_name_by_symbol

```raku
method get_name_by_symbol(
    Str $symbol where { ... },
    Str:D $lang = "default"
) returns Str:D
```

provide a second argument to choose the language.

### method get_symbol_by_Z

```raku
method get_symbol_by_Z(
    Chemistry::Elements::ZInt(Cool) $Z
) returns Chemistry::Elements::ChemicalSymbol
```

Return the chemical symbol (as a ChemicalSymbol type) by the atomic number.

### method get_symbol_by_name

```raku
method get_symbol_by_name(
    Str:D $name
) returns Chemistry::Elements::ChemicalSymbol
```

Return the chemical symbol (as a ChemicalSymbol object) by the element name.

### method get_Z_by_symbol

```raku
method get_Z_by_symbol(
    Str $symbol where { ... }
) returns Chemistry::Elements::ZInt
```

Return the atomic number (as a ZInt type) by the ChemicalSymbol.

### method get_Z_by_name

```raku
method get_Z_by_name(
    Str:D $name,
    Str:D $lang = "default"
) returns Chemistry::Elements::ZInt
```

Return the atomic number (as a ZInt type) by the element name.

TO DO
=====

  * Integrate the other languages in the Lib/Languages directory.

  * Guess the langauge based on a name or symbol

  * Allow historical symbols that aren't

SEE ALSO
========

SOURCE AVAILABILITY
===================

This module is in Github:

    https://github.com/raku-community-modules/Chemistry-Elements

AUTHORS
=======

  * brian d foy

  * Raku Community

COPYRIGHT AND LICENSE
=====================

Copyright © 2016-2022, brian d foy <bdfoy@cpan.org>. All rights reserved.

Copyright © 2024 Raku Community

This program is free software; you can redistribute it and/or modify it under the Artistic License 2.0.

