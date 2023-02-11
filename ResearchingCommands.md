# Researching Commands (```grep```)

---

## 1. ```-i``` option

Example 1:

    $ grep -i "lucayans" written_2/*/*/*.txt
    written_2/travel_guides/berlitz2/Bahamas-History.txt:Centuries before the arrival of Columbus, a peaceful Amerindian 
    people who called themselves the Luccucairi had settled in the Bahamas. Originally from South America, they had 
    traveled up through the Caribbean islands, surviving by cultivating modest crops and from what they caught from sea 
    and shore. Nothing in the experience of these gentle people could have prepared them for the arrivalof the Pinta, the 
    Niña, and the Santa Maria at San Salvador on 12 October 1492. Columbus believed that he had reached the East Indies 
    and mistakenlycalled these people Indians. We know them today as the Lucayans. Columbus claimed the island and others 
    in the Bahamas for his royal Spanish patrons,but not finding the gold and other riches he was seeking, he stayed for 
    only two weeks before sailing towards Cuba.
    written_2/travel_guides/berlitz2/Bahamas-History.txt:The Spaniards never bothered to settle in the Bahamas, but the 
    number of shipwrecks attest that their galleons frequently passed through the archipelago en route to and from the 
    Caribbean, Florida, Bermuda, and their home ports. On Eleuthera the explorers dug a fresh-water well — at a spot now 
    known as “Spanish Wells” — which was used to replenish the supplies of water on their ships before  they began the 
    long journey back to Europe with their cargoes of South American gold. As for the Lucayans, within 25 years all of 
    them, perhaps some 30,000 people, were removed from the Bahamas to work — and die — in Spanish gold mines and on 
    farms and pearl fisheries on Hispaniola (Haiti), Cuba, and elsewhere in the Caribbean.

Example 2:

    $ grep -i "PeArLs" written_2/travel_guides/berlitz1/*.txt
    written_2/travel_guides/berlitz1/WhatToHongKong.txt:        for both jade and freshwater pearls. This is not the 
    place to make
    written_2/travel_guides/berlitz1/WhatToHongKong.txt:        Popular purchases include diamonds and freshwater pearls.
    If you do
    written_2/travel_guides/berlitz1/WhatToMallorca.txt:        fossils, and bargains include Mallorca’s artificial 
    pearls and
    written_2/travel_guides/berlitz1/WhatToMallorca.txt:        Mallorcan cultured (artificial) pearls, manufactured in
    written_2/travel_guides/berlitz1/WhereToItaly.txt:        2,000 precious stones, including pearls, garnets, sapphires, 
    emeralds
    written_2/travel_guides/berlitz1/WhereToLakeDistrict.txt:        Buttermere is one of the pearls of the Lake district.

Explanation of function: The ```-i``` option for ```grep``` looks through the files in a given directory to return the ones matching the given pattern (in quotation marks) without regard for case in the pattern. This is useful because it is less picky with syntax, and may be helpful if one is looking for all occurances of a pattern, regardless of capitalization techniques. 

https://man7.org/linux/man-pages/man1/grep.1.html

## 2. ```-c``` option

Example 1:

    $ grep -c "jungle" written_2/travel_guides/berlitz2/*.txt
    written_2/travel_guides/berlitz2/Algarve-History.txt:0
    written_2/travel_guides/berlitz2/Algarve-Intro.txt:0
    written_2/travel_guides/berlitz2/Algarve-WhatToDo.txt:0
    written_2/travel_guides/berlitz2/Algarve-WhereToGo.txt:0
    written_2/travel_guides/berlitz2/Amsterdam-History.txt:0
    written_2/travel_guides/berlitz2/Amsterdam-Intro.txt:0
    written_2/travel_guides/berlitz2/Amsterdam-WhatToDo.txt:0
    written_2/travel_guides/berlitz2/Amsterdam-WhereToGo.txt:0
    written_2/travel_guides/berlitz2/Athens-History.txt:0
    written_2/travel_guides/berlitz2/Athens-Intro.txt:0
    written_2/travel_guides/berlitz2/Athens-WhatToDo.txt:0
    written_2/travel_guides/berlitz2/Athens-WhereToGo.txt:0
    written_2/travel_guides/berlitz2/Bahamas-History.txt:0
    written_2/travel_guides/berlitz2/Bahamas-Intro.txt:0
    written_2/travel_guides/berlitz2/Bahamas-WhatToDo.txt:0
    written_2/travel_guides/berlitz2/Bahamas-WhereToGo.txt:0
    written_2/travel_guides/berlitz2/Bali-History.txt:0
    written_2/travel_guides/berlitz2/Bali-WhatToDo.txt:0
    written_2/travel_guides/berlitz2/Bali-WhereToGo.txt:1
    written_2/travel_guides/berlitz2/Barcelona-History.txt:0
    written_2/travel_guides/berlitz2/Barcelona-WhatToDo.txt:0
    written_2/travel_guides/berlitz2/Barcelona-WhereToGo.txt:0
    written_2/travel_guides/berlitz2/Beijing-History.txt:0
    written_2/travel_guides/berlitz2/Beijing-WhatToDo.txt:0
    written_2/travel_guides/berlitz2/Beijing-WhereToGo.txt:0
    written_2/travel_guides/berlitz2/Berlin-History.txt:0
    written_2/travel_guides/berlitz2/Berlin-WhatToDo.txt:0
    written_2/travel_guides/berlitz2/Berlin-WhereToGo.txt:0
    written_2/travel_guides/berlitz2/Bermuda-WhatToDo.txt:0
    written_2/travel_guides/berlitz2/Bermuda-WhereToGo.txt:0
    written_2/travel_guides/berlitz2/Bermuda-history.txt:0
    written_2/travel_guides/berlitz2/Boston-WhereToGo.txt:0
    written_2/travel_guides/berlitz2/Budapest-History.txt:0
    written_2/travel_guides/berlitz2/Budapest-WhatToDo.txt:0
    written_2/travel_guides/berlitz2/Budapest-WhereoGo.txt:0
    written_2/travel_guides/berlitz2/California-History.txt:0
    written_2/travel_guides/berlitz2/California-WhatToDo.txt:0
    written_2/travel_guides/berlitz2/California-WhereToGo.txt:2
    written_2/travel_guides/berlitz2/Canada-History.txt:0
    written_2/travel_guides/berlitz2/Canada-WhereToGo.txt:1
    written_2/travel_guides/berlitz2/CanaryIslands-History.txt:0
    written_2/travel_guides/berlitz2/CanaryIslands-WhatToDo.txt:0
    written_2/travel_guides/berlitz2/CanaryIslands-WhereToGo.txt:0
    written_2/travel_guides/berlitz2/Cancun-History.txt:4
    written_2/travel_guides/berlitz2/Cancun-WhatToDo.txt:1
    written_2/travel_guides/berlitz2/Cancun-WhereToGo.txt:6
    written_2/travel_guides/berlitz2/China-History.txt:0
    written_2/travel_guides/berlitz2/China-WhatToDo.txt:0
    written_2/travel_guides/berlitz2/China-WhereToGo.txt:0
    written_2/travel_guides/berlitz2/Costa-History.txt:0
    written_2/travel_guides/berlitz2/Costa-WhatToDo.txt:0
    written_2/travel_guides/berlitz2/Costa-WhereToGo.txt:0
    written_2/travel_guides/berlitz2/CostaBlanca-History.txt:0
    written_2/travel_guides/berlitz2/CostaBlanca-WhatToDo.txt:0
    written_2/travel_guides/berlitz2/Crete-History.txt:0
    written_2/travel_guides/berlitz2/Crete-WhatToDo.txt:0
    written_2/travel_guides/berlitz2/Crete-WhereToGo.txt:0
    written_2/travel_guides/berlitz2/CstaBlanca-WhereToGo.txt:0
    written_2/travel_guides/berlitz2/Cuba-History.txt:0
    written_2/travel_guides/berlitz2/Cuba-WhatToDo.txt:0
    written_2/travel_guides/berlitz2/Cuba-WhereToGo.txt:0
    written_2/travel_guides/berlitz2/Nepal-History.txt:0
    written_2/travel_guides/berlitz2/Nepal-WhatToDo.txt:1
    written_2/travel_guides/berlitz2/Nepal-WhereToGo.txt:4
    written_2/travel_guides/berlitz2/NewOrleans-History.txt:0
    written_2/travel_guides/berlitz2/Paris-WhatToDo.txt:0
    written_2/travel_guides/berlitz2/Paris-WhereToGo.txt:0
    written_2/travel_guides/berlitz2/Poland-History.txt:0
    written_2/travel_guides/berlitz2/Poland-WhatToDo.txt:1
    written_2/travel_guides/berlitz2/Portugal-History.txt:0
    written_2/travel_guides/berlitz2/Portugal-WhatToDo.txt:0
    written_2/travel_guides/berlitz2/Portugal-WhereToGo.txt:0
    written_2/travel_guides/berlitz2/PuertoRico-History.txt:0
    written_2/travel_guides/berlitz2/PuertoRico-WhatToDo.txt:0
    written_2/travel_guides/berlitz2/PuertoRico-WhereToGo.txt:0
    written_2/travel_guides/berlitz2/Vallarta-History.txt:0
    written_2/travel_guides/berlitz2/Vallarta-WhatToDo.txt:5
    written_2/travel_guides/berlitz2/Vallarta-WhereToGo.txt:4

Example 2:

    **$ grep -c "tower" written_2/non-fiction/OUP/Rybczynski/*.txt
    written_2/non-fiction/OUP/Rybczynski/ch1.txt:1
    written_2/non-fiction/OUP/Rybczynski/ch2.txt:8
    written_2/non-fiction/OUP/Rybczynski/ch3.txt:1**

Explanation of function: Output count of matching lines only.

https://man7.org/linux/man-pages/man1/grep.1.html

## 3. ```-n``` option

Example 1:

Example 2:

Explanation of function: Precede each matching line with a line number.

https://man7.org/linux/man-pages/man1/grep.1.html

## 4. ```-v``` option

Example 1:

Example 2:

Explanation of function: Invert match.

https://man7.org/linux/man-pages/man1/grep.1.html

