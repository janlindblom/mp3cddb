# mp3cddb
   
## About
   Mp3cddb is a small perl script that helps you recognizing your unknown
   music albums. If you have a complete music album in MPEG layer III
   (.mp3) compressed audio format, but you don't know its
   artist/title/the names of the songs/etc, you only know that it's a
   complete album and the files are in a correct order (e.g. track01.mp3,
   etc), mp3cddb analyzes these files and tries to identify the album
   using the compact disc database at www.freedb.org (note that
   mp3cddb was formerly using www.cddb.com but it became commercial).
   If this database contains information about the album you're looking
   for, mp3cddb saves all information in a file called "cddbinfo.txt".
   This information usually consists of the performer, the title of the
   album and the titles of the tracks (it contains the genre of the music
   as well, however this may be somewhat inaccurate due to the limited
   possibilities of the CDDB standard). You can then edit this plain
   textfile, if necessary, insert any additional information (comment,
   year, genre) or modify the existing. Then mp3cddbtag, a small shell
   script (also included) processes this file, tags (adds these
   information to the .mp3 file using the ID3v1 format) and renames your
   .mp3 files.
   
## Requirements
   This system has been written and tested on a Linux system and it
   requires the GNU Bourne Again Shell (bash). This is included in the
   most of Linux distributions, but is also downloadable at
   ftp://prep.ai.mit.edu/pub/gnu/bash/.
   
   Additional software required:
   
   * a Perl interpreter (http://www.perl.com)
   * the CDDB module for Perl
       (http://www.perl.com/CPAN/authors/id/R/RC/RCAPUTO/CDDB-1.02.tar.gz)
   * the MPEG::MP3Info module for Perl
       (http://www.perl.com/CPAN/authors/id/CNANDOR/MPEG-MP3Info-0.80.tar.gz)
   * the mp3info program
       (ftp://ftp.ibiblio.org/pub/linux/apps/sound/mp3-utils/mp3info/mp3info-0.8.2.tgz)
       
   The Perl interpreter and mp3info are likely available in pre-made
   packages for your distribution. If you use Debian GNU/Linux, you need
   the following packages: perl, mp3info. For more information, visit the
   website of your distribution.
   
## Usage
   First, try to identify your files using mp3cddb. Please note, that the
   order of the files does matter, since CDDB stores the information
   about albums using an identification number, which is calculated using
   the order and the lenght of the tracks. The names of the files are not
   important, as long they are in the correct order (alphabetically). If
   you've got the information in cddbinfo.txt, modify it according to
   your needs, then run mp3cddbtag to tag & rename your files.
   
   Example:
   
   $ ls -la
   total 24527
   drwxr-xr-x    2 bali     users        1024 Feb 24 15:21 .
   drwxr-xr-x   63 bali     users       13312 Feb 24 15:19 ..
   -rw-r--r--    1 bali     users     5207306 Feb 16  2000 1.mp3
   -rw-r--r--    1 bali     users     8929166 Feb 16  2000 2.mp3
   -rw-r--r--    1 bali     users     5386874 Feb 16  2000 3.mp3
   -rw-r--r--    1 bali     users     5471960 Feb 16  2000 4.mp3
   $ mp3cddb *
   searching for discid: 2a04e004, total tracks: 4, total time: 1248 ...
   match: rock      2e04e904        Pierre Henry - Michel Colombier / Psyché Rock
   saving information to cddbinfo.txt...
   $ mp3cddbtag cddbinfo.txt
   processing cddbinfo.txt (Pierre Henry - Michel Colombier / Psyché Rock)...
   tagging 4 tracks...
   01. Pierre Henry - Michel Colombier / Psyché Rock (Malpaso Radio Edit) (Psyché Rock)
   02. Pierre Henry - Michel Colombier / Psyché Rock (Malpaso Mix) (Psyché Rock)
   03. Pierre Henry - Michel Colombier / Psyché Rock (Metal Time Machine Edit) (Psyché Rock)
   04. Pierre Henry - Michel Colombier / Psyché Rock (Psyché Dub) (Psyché Rock)
   done.
   $ mp3info 01*mp3
   File: 01-Psyche_Rock_Malpaso_Radio_Edit.mp3
   Title:   Psyché Rock (Malpaso Radio Edi Track:
   Artist:  Pierre Henry - Michel Colombie
   Album:   Psyché Rock                    Year:
   Comment:                                Genre: Rock [17]
   $
   
## Changelog
*   Feb 19 2011
     * Modified the mp3cddb script to use MP3::Info.
     * Added [åäÅÄ] to formatstr() in mp3cddbtag.
     
*   Mar 10 2001
     * Modified the mp3cddb script so that it now uses freedb.freedb.org
       as the CDDB server since cddb.com became commercial. Unfortunately
       freedb does not hold as much information as cddb does, but it
       works at least. And it's free.
     * Started version numbering.
     * Included license information.
     * Updated documentation.
       
*   Feb 24 2001
     * Applied patch from Frederic Crozat <fred@crozat.net> so that mp3cddb saves the
       genre information from the CDDB entry and mp3cddbtag uses mp3info
       from Ricardo Cerqueria and Cedric Tefft.
     * Applied patch from Ben Jackson <ben@ben.com> that implements the 'seq'
       function (since seq is not a standard unix program) and makes
       mp3cddbtag only try to rename the files if their name changed.
     * Updated the documentation.
       
*   Nov 25 1999
     * First release
   
## Author
   The mp3cddb script is based on the mp3tocddb script of Meng Weng Wong.
   Minor modifications, this page and the mp3cddb script were made by
   Andras Bali. The original mp3tocddb script by Meng Weng Wong is
   included in the MPEG::MP3Info module for Perl (see Requirements).
   
## License
   The whole mp3cddb package (including mp3cddb and mp3cddbtag) is free
   software; you can redistribute it and/or modify it under the terms of
   the GNU General Public License as published by the Free Software
   Foundation; either version 2 of the License, or (at your option) any
   later versions. This program is distributed in the hope that it will
   be useful, but WITHOUT ANY WARRANTY; without even the implied warranty
   of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
   GNU General Public License (http://www.gnu.org/copyleft/gpl.html)
   for details.
   
## Contacting me
   Please feel free to contact me if you have ideas, suggestions,
   problems, found some bugs, or just want to tell me what you think of
   it.
   
   * E-mail: drewie@bigfoot.com
   * IRC: [drewie] on iRCnet
   _________________________________________________________________
   
   last updated: 03/10/2001

