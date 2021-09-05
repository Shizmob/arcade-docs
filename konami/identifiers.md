# Konami Identifiers

This file describes the various identifiers and their formats that are used in products by Konami.

## Sources

* [bemaniwiki](http://bemaniwiki.com/)
* Game/cabinet manuals
* MAME
* Various sources around the internet

## Format

The format of each identifier/ID is described as a perl/php/shell-style string with `$` denoting
that a variable is resolved, e.g. `$a` "resolve variable a". Additionally, a more complex regex
string is provided to constrain the format properly.

### Variables and values

The following variables are used across the different identifiers and can denote the listed values:

* `$p`: Product
  * `G`: Game
* `$t`: Type of product
  * `C`: Upgrade: software only
  * `E`: Upgrade: hardware (conversion) kit + software
  * `K`: Upgrade: offline/no eamuse software version
  * `N`: ???
  * `O`: ???
  * `Q`: Dedicated cabinet assembly/main body
  * `U`: "Utilities", e.g. DVD software update kit, replacement monitors
  * `X`: Hardware/board ???
* `$g`: Gamecode, identifies a game or series in [Konami's product portfolio](products.md)
  * Format: `yxx`
    * `y`: `A` + (project development start year - 2000) (`L`: 2011, `T`: 2019, etc.)
    * `xx`: Remainder, (incremental) game/product identifier
  * Example: `LDJ`
* `$d`: Destination, target locale/market
  * `A`: Asia
  * `C`: China
  * `E`: Europe
  * `J`: Japan
  * `K`: Korea
  * `U`: US
  * `Y`: Indonesia
* `$s`: Specification: Product type and game dependent, e.g. type of cabinet or hardware
  * `A`, `B`, `C`, ..., `Z`
* `$r`: Software revision. Modern games utilizing the extension part pinned this to the value `A`
  * `A`, `B`, `C`, ..., `Z`
* `$e`: Extension/build date of the software
  * Format: `yyyymmddnn`
    * `yyyy` = year, e.g. `2020`
    * `mm` = month, e.g. `11` for November
    * `dd` = day of month, e.g. `03`
    * `nn` = build number on the day, e.g. `00`, `01`, ...
  * Example: `201807300200`

## Identifiers

### Product identifier

* [Products or packages](products.md) that can be acquired, e.g. bought or leased
* Format: `$p$t$g-$d$s`
* Example: [GQLDJ-JA](product/GQLDJ-JA.md)

### Mcode

* Source: License dongle certificate CN
* Format: `$g-$n`
  * `$n`: An integer number, e.g. `001`
* Example: `PIX-001`

### Security code

* Source: License dongle certificate subjectAltName
* Format: `$p$t$g$d$s$r`
* Example: `GQPIXJBA`

### Release code

* Source: Game data
* Format: `$e`
* Example: `201807300200`

### System ID

* Source: Account dongle certificate CN
* Format: `0120$x0$y`
  * `$x`: `1` or `2`
  * `$y`: 14-digit hex string
* Example: `0120100000000160B3D2`

### License ID

* Source: License dongle serial number
* Format: `012$x$y`
  * `$x`: `1` or `2`
  * `$y`: 8-digit numeric value
* Example: `012194810293`

### Account ID

* Source: Account dongle serial number
* Format: `012$x$y`
  * `$x`: `1` or `2`
  * `$y`: 8-digit numeric value
* Example: `012291862492`

### Hardware ID

* Source: MAC address
* Format: `0100$y`
  * `$y`: 12-digit hex string
* Example: `0100705CAD0365F2`

### Software ID

* Alias for License ID
* Format: `012$x$y`
  * `$x`: `1` or `2`
  * `$y`: 8-digit numeric value
* Example: `012194810293`

### Soft ID code

* Source: [Security code](#security-code) and [release code](#release-code) combined and shown in-game
* Format: `$g:$d:$s:$r:$e`
* Example: `PIX:J:B:A:201807300200`
