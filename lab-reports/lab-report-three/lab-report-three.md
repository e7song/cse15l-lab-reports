# **CSE 15L Winter 2023 Lab Report 3**
### Eric Song, Wednesday B270 1 p.m.   

### Researching Commands

#### *Different ways to use grep*   
If you need to search for a specific word in a certain file, it's pretty   
straightforward to use `grep <word> <file>`. However, in the case where you   
don't know exactly what you are searching for and where you need to search for   
there are helpful modifications you can add on to the grep command.   

##### **Method  #1- Recursive Searching**   
`grep -r <word> <path (optional)>`
The modifier here will recursively search through the path given, looking at   
all the files within as well as the subdirectories until all the files are   
searched. This command is especially helpful when you don't know where the word   
you are searching for is, just that it exists.   

*Example 1:*   
```
19255@DESKTOP-5PUADJU MINGW64 ~/Documents/GitHub/docsearch (main)
$ grep -r "Lucayans" ./written_2/
./written_2/travel_guides/berlitz2/Bahamas-History.txt:Centuries before the arrival of Columbus, a peaceful Amerindian people who called themselves the Luccucairi had settled in the Bahamas. Originally from South America, they had traveled up through the Caribbean islands, surviving by cultivating modest crops and from what they caught from sea and shore. Nothing in the experience of these gentle people could have prepared them for the arrival of the Pinta, the Niña, and the Santa Maria at San Salvador on 12 October 1492. Columbus believed that he had reached the East Indies and mistakenly called these people Indians. We know them today as the Lucayans. Columbus claimed the island and others in the Bahamas for his royal Spanish patrons, but not finding the gold and other riches he was seeking, he stayed for only two weeks before sailing towards Cuba.
./written_2/travel_guides/berlitz2/Bahamas-History.txt:The Spaniards never bothered to settle in the Bahamas, but the number of shipwrecks attest that their galleons frequently passed through the archipelago en route to and from the Caribbean, Florida, Bermuda, and their home ports. On Eleuthera the explorers dug a fresh-water well — at a spot now known as “Spanish Wells” — which was used to replenish the supplies of water on their ships before they began the long journey back to Europe with their cargoes of South American gold. As for the Lucayans, within 25 years all of them, perhaps some 30,000 people, were removed from the Bahamas to work — and die — in Spanish gold mines and on farms and pearl fisheries on Hispaniola (Haiti), Cuba, and elsewhere in the Caribbean.

19255@DESKTOP-5PUADJU MINGW64 ~/Documents/GitHub/docsearch (main)
$
```   

*Example 2:*   

```
19255@DESKTOP-5PUADJU MINGW64 ~/Documents/GitHub
$ ls
CleanroomBot/  cse15l-lab-reports/  docsearch/  lab3/  wavelet/

19255@DESKTOP-5PUADJU MINGW64 ~/Documents/GitHub
$ pwd
/c/Users/19255/Documents/GitHub

19255@DESKTOP-5PUADJU MINGW64 ~/Documents/GitHub
$ grep -r "Lucayans"
docsearch/written_2/travel_guides/berlitz2/Bahamas-History.txt:Centuries before the arrival of Columbus, a peaceful Amerindian people   who called themselves the Luccucairi had settled in the Bahamas. Originally from South America, they had traveled up through the   Caribbean islands, surviving by cultivating modest crops and from what they caught from sea and shore. Nothing in the experience of   these gentle people could have prepared them for the arrival of the Pinta, the Niña, and the Santa Maria at San Salvador on 12 October  1492. Columbus believed that he had reached the East Indies and mistakenly called these people Indians. We know them today as the   Lucayans. Columbus claimed the island and others in the Bahamas for his royal Spanish patrons, but not finding the gold and other   riches he was seeking, he stayed for only two weeks before sailing towards Cuba.  
docsearch/written_2/travel_guides/berlitz2/Bahamas-History.txt:The Spaniards never bothered to settle in the Bahamas, but the number of shipwrecks attest that their galleons frequently passed through the archipelago en route to and from the Caribbean, Florida, Bermuda, and their home ports. On Eleuthera the explorers dug a fresh-water well — at a spot now known as “Spanish Wells” — which was used to  replenish the supplies of water on their ships before they began the long journey back to Europe with their cargoes of South American  gold. As for the Lucayans, within 25 years all of them, perhaps some 30,000 people, were removed from the Bahamas to work — and die —  in Spanish gold mines and on farms and pearl fisheries on Hispaniola (Haiti), Cuba, and elsewhere in the Caribbean.   

19255@DESKTOP-5PUADJU MINGW64 ~/Documents/GitHub
$
```   
This example shows how even if you don't know where the file is, you don't neen   
to specify a path. It will recursively search from your working directory.

##### **Method  #2- Only Finding Files**   
These examples are very helpful in showing you how to find a word in a file.   
However, it is clear that these results quickly clutter your terminal. To   
minimize this clutter, you can use another modifier.

`grep -r -l <word> <path (optional)>` or more simply, `grep -rl <word> <path (optional)>`   

*Example #1:*   
```
19255@DESKTOP-5PUADJU MINGW64 ~/Documents/GitHub/docsearch (main)
$ grep -r -l "Lucayans"
written_2/travel_guides/berlitz2/Bahamas-History.txt
```   
This example shows how much more convenient this modifier is. 

*Example #2:*   
```
19255@DESKTOP-5PUADJU MINGW64 ~/Documents/GitHub/docsearch (main)
$ grep -rl "weird" ./written_2/
./written_2/non-fiction/OUP/Kauffman/ch6.txt
./written_2/travel_guides/berlitz1/WhatToFWI.txt
./written_2/travel_guides/berlitz1/WhatToIbiza.txt
./written_2/travel_guides/berlitz1/WhereToFrance.txt
./written_2/travel_guides/berlitz1/WhereToHongKong.txt
./written_2/travel_guides/berlitz1/WhereToIbiza.txt
./written_2/travel_guides/berlitz1/WhereToMadrid.txt
./written_2/travel_guides/berlitz2/Algarve-WhereToGo.txt
./written_2/travel_guides/berlitz2/Paris-WhatToDo.txt
```
These two examples show how much more compact the information given is. Had we   
not added the modifier `-l`, the terminal would have been flooded with   
extra information.   


##### **Method  #3- Ignore Case**   
Another common problem you might run into is when you want to search for a   
word but you don't know what that word looks like exactly. For our previous   
examples, we knew that the word "Lucayans" was in the file. However, what if   
we didn't know that "Lucayans" has a capital L?

*Example 1- regular search*   
```   
19255@DESKTOP-5PUADJU MINGW64 ~/Documents/GitHub/docsearch (main)
$ grep -rl "Lucayans"
written_2/travel_guides/berlitz2/Bahamas-History.txt

19255@DESKTOP-5PUADJU MINGW64 ~/Documents/GitHub/docsearch (main)
$ grep -rl "lucayans"

19255@DESKTOP-5PUADJU MINGW64 ~/Documents/GitHub/docsearch (main)
$ 
```   
As this code snippet demonstrates, grep is case-sensitive. That is why   
"Lucayans" throws out a result, but "lucayans" does not. To get rid of this   
case-sensitivity when searching, you can use the `-i` modifier.

`grep -i <word> <path>`

Combining with the previous two examples, we have the following usages:

*Example 2*   
```
19255@DESKTOP-5PUADJU MINGW64 ~/Documents/GitHub/docsearch (main)
$ grep -rli "lucayans"
written_2/travel_guides/berlitz2/Bahamas-History.txt

19255@DESKTOP-5PUADJU MINGW64 ~/Documents/GitHub/docsearch (main)
$ grep -r -l -i "lucayans"
written_2/travel_guides/berlitz2/Bahamas-History.txt

19255@DESKTOP-5PUADJU MINGW64 ~/Documents/GitHub/docsearch (main)
$ 
```   
*Example 3*   
```
19255@DESKTOP-5PUADJU MINGW64 ~/Documents/GitHub/docsearch (main)
$ grep -rl "BrIdGeS"

19255@DESKTOP-5PUADJU MINGW64 ~/Documents/GitHub/docsearch (main)
$ grep -rli "BrIdGeS"
written_2/non-fiction/OUP/Castro/chA.txt
written_2/travel_guides/berlitz1/HistoryItaly.txt
written_2/travel_guides/berlitz1/IntroIstanbul.txt
written_2/travel_guides/berlitz1/WhereToDublin.txt
written_2/travel_guides/berlitz1/WhereToEdinburgh.txt
written_2/travel_guides/berlitz1/WhereToFrance.txt
written_2/travel_guides/berlitz1/WhereToFWI.txt
written_2/travel_guides/berlitz1/WhereToHongKong.txt
written_2/travel_guides/berlitz1/WhereToIbiza.txt
written_2/travel_guides/berlitz1/WhereToIndia.txt
written_2/travel_guides/berlitz1/WhereToIstanbul.txt
written_2/travel_guides/berlitz1/WhereToItaly.txt
written_2/travel_guides/berlitz1/WhereToJapan.txt
written_2/travel_guides/berlitz1/WhereToLakeDistrict.txt
written_2/travel_guides/berlitz1/WhereToMalaysia.txt
written_2/travel_guides/berlitz1/WhereToMallorca.txt
written_2/travel_guides/berlitz2/Algarve-History.txt
written_2/travel_guides/berlitz2/Algarve-WhatToDo.txt
written_2/travel_guides/berlitz2/Algarve-WhereToGo.txt
written_2/travel_guides/berlitz2/Amsterdam-History.txt
written_2/travel_guides/berlitz2/Amsterdam-Intro.txt
written_2/travel_guides/berlitz2/Amsterdam-WhatToDo.txt
written_2/travel_guides/berlitz2/Amsterdam-WhereToGo.txt
written_2/travel_guides/berlitz2/Bahamas-WhereToGo.txt
written_2/travel_guides/berlitz2/Bali-WhereToGo.txt
written_2/travel_guides/berlitz2/Beijing-WhereToGo.txt
written_2/travel_guides/berlitz2/Berlin-History.txt
written_2/travel_guides/berlitz2/Berlin-WhereToGo.txt
written_2/travel_guides/berlitz2/Bermuda-WhereToGo.txt
written_2/travel_guides/berlitz2/Boston-WhereToGo.txt
written_2/travel_guides/berlitz2/California-WhatToDo.txt
written_2/travel_guides/berlitz2/California-WhereToGo.txt
written_2/travel_guides/berlitz2/Canada-WhereToGo.txt
written_2/travel_guides/berlitz2/China-History.txt
written_2/travel_guides/berlitz2/China-WhereToGo.txt
written_2/travel_guides/berlitz2/Costa-History.txt
written_2/travel_guides/berlitz2/Costa-WhereToGo.txt
written_2/travel_guides/berlitz2/Cuba-WhereToGo.txt
written_2/travel_guides/berlitz2/NewOrleans-History.txt
written_2/travel_guides/berlitz2/Paris-WhereToGo.txt
written_2/travel_guides/berlitz2/Portugal-WhereToGo.txt
written_2/travel_guides/berlitz2/PuertoRico-WhereToGo.txt
written_2/travel_guides/berlitz2/Vallarta-WhereToGo.txt

19255@DESKTOP-5PUADJU MINGW64 ~/Documents/GitHub/docsearch (main)
$
```   
This modifier is useful because it gives us greater flexibility when we are   
searching for a word. At this point, we can recursively search every file for   
any string that matches the word we want and then return a single line that   
represents the location of the file where that word is found.   

##### **Method 4- Number of Occurences**   
The two modifiers `-r` and `-l` are really powerful for easily identifying   
the file that has the word you want. However, a downside of using `-l` is that   
it does not tell you how many times that the word occurs in that that file.   
You can use the `c` modifier to count the number of occurances that the word   
has in the file.   
`grep -c <word> <path>`   

*Example 1*
```
19255@DESKTOP-5PUADJU MINGW64 ~/Documents/GitHub/docsearch (main)
$ grep -c "Lucayans" written_2/travel_guides/berlitz2/Bahamas-History.txt 
2
```   
Based on the results, it seems that the word "Lucayans" occurs twice in the file   
Bahamas-History.txt.   

*Example 2*   
```
19255@DESKTOP-5PUADJU MINGW64 ~/Documents/GitHub/docsearch (main)
$ grep -r -c "bridge" ./written_2/travel_guides/berlitz2/Amsterdam*
./written_2/travel_guides/berlitz2/Amsterdam-History.txt:1
./written_2/travel_guides/berlitz2/Amsterdam-Intro.txt:2
./written_2/travel_guides/berlitz2/Amsterdam-WhatToDo.txt:1
./written_2/travel_guides/berlitz2/Amsterdam-WhereToGo.txt:10
```   
For the sake of readability, the `-c` modifier was only used on the Amsterdam  
files. The number of times the word "bridge" occurs is indicated by the number   
following the colon on the far right of each line. Adding this modifier let us   
find both the files that contain the word and the number of times that word   
occurs.


Click on [this link](https://www.cyberciti.biz/faq/howto-use-grep-command-in-linux-unix/) for more information   
This website contains more comprehensive information about all the grep modifiers   
that I used.   

***Works Cited***   
How to Use GREP Command in Linux/ Unix with Examples - Nixcraft. <br />https://www.cyberciti.biz/faq/howto-use-grep-command-in-linux-unix/. 