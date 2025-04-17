```shell
text/FG - #A6A6A6
BG		- #000000
bold 	- #B7B7B7

trans 	- 20%

color palatte
#000000		#FF5252		#889BFF		#757575		#6FB4FF		#EB6AFF		#A4FF71		#FF5252
#2E3436		#FF5252		#889BFF		#757575		#6FB4FF		#EB6AFF		#A4FF71		#A4FF71
```

show bold text in colors

----------------------------------------------------------------------------------------------------------

monospace bold

155		30

1.05 	1.0

allow blinking text

underline - blinking


----------------------------------------------------------------------------------------------------------


It has always been confusing to add color to bash scripts. You need to add parameters to commands and look up the escape codes, which are not easy to find. I have made this simple "library" to add color in an easier way.

Special formatting modifiers:

$bold, $underline, $dim, $strickthrough, $blink, $reverse, $hidden

Each can be used by itself or together. To clear all the options including colors, use:

$normal

Color modifiers:

$black, $red, $green, $orange, $blue, $purple, $aqua, $gray, $darkgray, $lightred, $lightgreen, $lightyellow, $lightblue, $lightpurple, $lightaqua, $white

All color options are case sensitive! ALL CAPS modifies background, all lowercase modifies foreground.

$RED would highlight the text with red. $red would change the color of the text to red.

To clear a color (still case sensitive):

$default

Remember, the colors are caried over newlines.

Hint: you can use colors right next to text with backslashes: $red\text

Example usage:

echo $blue this is blue $RED$black\This is black with red background $underline\this is underlined $normal\normal

Copy and paste this into your script:

```shell
bold=`echo -en "\e[1m"`
underline=`echo -en "\e[4m"`
dim=`echo -en "\e[2m"`
strickthrough=`echo -en "\e[9m"`
blink=`echo -en "\e[5m"`
reverse=`echo -en "\e[7m"`
hidden=`echo -en "\e[8m"`
normal=`echo -en "\e[0m"`
black=`echo -en "\e[30m"`
red=`echo -en "\e[31m"`
green=`echo -en "\e[32m"`
orange=`echo -en "\e[33m"`
blue=`echo -en "\e[34m"`
purple=`echo -en "\e[35m"`
aqua=`echo -en "\e[36m"`
gray=`echo -en "\e[37m"`
darkgray=`echo -en "\e[90m"`
lightred=`echo -en "\e[91m"`
lightgreen=`echo -en "\e[92m"`
lightyellow=`echo -en "\e[93m"`
lightblue=`echo -en "\e[94m"`
lightpurple=`echo -en "\e[95m"`
lightaqua=`echo -en "\e[96m"`
white=`echo -en "\e[97m"`
default=`echo -en "\e[39m"`
BLACK=`echo -en "\e[40m"`
RED=`echo -en "\e[41m"`
GREEN=`echo -en "\e[42m"`
ORANGE=`echo -en "\e[43m"`
BLUE=`echo -en "\e[44m"`
PURPLE=`echo -en "\e[45m"`
AQUA=`echo -en "\e[46m"`
GRAY=`echo -en "\e[47m"`
DARKGRAY=`echo -en "\e[100m"`
LIGHTRED=`echo -en "\e[101m"`
LIGHTGREEN=`echo -en "\e[102m"`
LIGHTYELLOW=`echo -en "\e[103m"`
LIGHTBLUE=`echo -en "\e[104m"`
LIGHTPURPLE=`echo -en "\e[105m"`
LIGHTAQUA=`echo -en "\e[106m"`
WHITE=`echo -en "\e[107m"`
DEFAULT=`echo -en "\e[49m"`
```

Edit: crashorbit created a fix that allows this to be used in for loops, and shortened the size. He also created a nice demo.
