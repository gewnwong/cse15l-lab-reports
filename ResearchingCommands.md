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

Example 2:

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

