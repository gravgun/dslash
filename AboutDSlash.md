## Advantages ##
### Speed ###
When invoked with the inline option [`-i`], DSlash is extremely fast. This is because most trimmers operate by copying the data from one ROM file into a new blank file, from the beginning of the file until the end of the useful data is reached. This creates excess filesystem activity which slows things down especially on a flash drive. DSlash truncates the original ROM file in place with a simple system call. hyplex says this is like, totally way faster than the other thing.

### STDIN/STDOUT processing ###
DSlash can operate directly on .nds files, but it also operates as a standard linux-style command line tool, processing input from STDIN and generating output on STDOUT. So you can pipe output from any shell command through DSlash, or you can pipe DSlash's output through other commands.


### Usage Examples ###
  * Standard usage, trimming an .nds file:
    * `dslash untrimmed_rom.nds trimmed_rom.nds`
  * Or, done another way:
    * `cat untrimmed_rom.nds | dslash - > trimmed_rom.nds`
  * To trim a zipped ROM file on the fly:
    * `unzip -c zipped_nds_rom.zip | dslash - > unzipped_and_trimmed_rom.nds`
  * Show a game's official title:
    * `dslash -p romfile.nds | grep -i title`