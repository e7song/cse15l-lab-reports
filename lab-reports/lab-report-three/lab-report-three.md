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


*Example #2:*   





















Click on [this link](https://www.cyberciti.biz/faq/howto-use-grep-command-in-linux-unix/) for more information

***Works Cited***   
How to Use GREP Command in Linux/ Unix with Examples - Nixcraft. <br />https://www.cyberciti.biz/faq/howto-use-grep-command-in-linux-unix/. 