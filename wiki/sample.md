# Welcome to git-wiki demo

This is a [demo](wiki/Demo.md) of git-wiki theme for jekyll.

it's a full featured wiki powered by git, github pages and pull-requests!

It means: 

* Improvements in the cooperative aspect: forks, pull-requests and roles.
* You can customize your wiki as you want with style sheets and even changing the layout.
* No databases! Only static files that can be downloaded in a few seconds.
* Markdown and html mixed together!
* History, revision comparison and everything you need from a wiki platform.
* You can edit your pages with the standard git editor, prose.io (integrated) or any kind of editor you prefer.

You can fork/copy the master branch now and start your wiki in just 1 minute.

Then [share your wiki with us!](wiki/Showreel.md) please.

**Note:**
You can even include the github wiki as a submodule and enable the conf, but it's an experimental feature and it implies less advantages and greater disadvantages for now.

## Installation instructions

1. Fork or copy [this repository](https://github.com/drassil/git-wiki)

2. copy and rename _config.yml.dist in _config.yml changing settings inside

3. create your index.md in root directory

4. push your changes in your repository, then configure the github pages in your repository settings

5. Your wiki is ready!

**Note:**

We suggest the creation of a /wiki/ subfolder that collects all your .md pages (except index.md)

## Current known limitations

* Non-existent wiki page links are not "[red](wiki/red.md)".

* You can't use the wiki link format: [[example]]. Please, use gh-pages links instead: \[example\](example) 

## Customization

You can create following files in _includes folder to costumize git-wiki without patching original code:

* head.html  -> this file will be included in <head> tag allowing you to add css/js and any kind of head tags
* sidebar.html -> this file will be included in left sidebar allowing you to create your widgets
* comments.html -> this is mostly used to integrate social comments under page contents
* footer.html -> this file will be included in left side of the footer.

## Looking for collaboration

Do you like this project? then, contact us via [chat](https://gitter.im/Drassil/general?utm_source=share-link&utm_medium=link&utm_campaign=share-link) , <a href="mailto:staff-drassil@googlegroups.com">email</a>  or send us a PR to improve it.

Thank you!

## table

| 헤더1 | 헤더2 | 헤더3 |
|:--------|:-------:|--------:|
| 컬럼1   | 컬럼2   | 컬럼3   |
| 컬럼4   | 컬럼5   | 컬럼6   |
|----
| 컬럼1   | 컬럼2   | 컬럼3   |
| 컬럼4   | 컬럼5   | 컬럼6   |
|=====
| Foot1   | Foot2   | Foot3

## code block

~~~~ c
#include <stdio.h>

int main(void)
{
    printf("Hello word!\n");
    return 1;
}
~~~~

~~~~ python
s = 'Hello word'
print(s)
~~~~

~~~~ verilog
module test;

initial
begin
    $display("Hello world");
    $finish;
end

endmodule
~~~~

~~~~ scheme
(df f-disp21
    "disp21"
    ((MACH ORBIS-MACHS) ABS-ADDR)
    20
    21
    INT
    ((value pc)
     (sub IAI (sra IAI value (const 13)) (sra IAI pc (const 13))))
    ((value pc)
     (sll IAI (add IAI value (sra IAI pc (const 13))) (const 13)))
    )
~~~~

~~~~ perl
#!/usr/local/bin/perl -w

use Getopt::Long;
use POSIX;

GetOptions(
    "help|h|?"          => \$opt{"help"},
    "address|a=s"       => \$opt{"addr"},
    "destination|d=s"   => \$opt{"dst"},
    "shift|s=s"         => \$opt{"shift"}
    );

if( defined $opt{"help"} || !defined $opt{"dst"} || !defined $opt{"addr"}){
    print <<END_OF_HELP;
Usage: wav2srec.pl -a start_address [-s shift] -d srecfile.srec wavfile1.wav [wavfile2.wav [...]]
       default shift : 2
END_OF_HELP
    exit(1);
}
~~~~

~~~~ csh
if ($uver =~ *el5*) then
    set centos_ver = '5'
else if ($uver =~ *el6*) then
    set centos_ver = '6'
else if ($uver =~ *el7*) then
    set centos_ver = '7'
else
    set centos_ver = '0'
endif
~~~~

~~~~ bash
# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth
~~~~

~~~~ kotlin
    @Throws(HidException::class)
    fun write(data: ByteArray, size: Int = packetSize) {
        val status = connection!!.bulkTransfer(endPointWrite, data, size, write_timeout)
        if (status < 0)
            throw HidException()
    }
~~~~

~~~~ java
    @Override
    protected void onStart(){
        super.onStart();
        Log.v("wang", "Sensor_Start");
        hidSetup();
    }
    @Override
    protected void onPause(){
        super.onPause();
        Log.v("wang", "Sensor_Pause");
    }
~~~~



## Components used

- [jekyll-table-of-contents](https://github.com/ghiculescu/jekyll-table-of-contents)

- [jQuery](https://jquery.com/)


[MIT LICENSE](LICENSE)
