# Week 5 Lab Report: Researching Commands


## Command-Line Options For ***grep***



### Grep Headliner



### '''grep -i '''

grep -i searches for the inputed keyword, but disregards capitalization.

**Example 1**

    ivor@Ivors-Air docsearch % grep -i "We found that" technical/biomed/*.txt
    technical/biomed/1471-2091-2-7.txt:        neddylation. On the other hand, we found that a sizable
    technical/biomed/1471-2091-3-14.txt:          IL-8 at the G1/S border, we found that all Tat containing
    technical/biomed/1471-2091-3-18.txt:          unlabeled TP as the DNA trap. We found that E-TP binary
    technical/biomed/1471-2091-3-30.txt:        (MDCK) cells. We found that inhibition of MEK1 by U0126
    technical/biomed/1471-2091-3-30.txt:          2 S727A and we found that the
    //more followed




In this case we are searching the files in technical for the phrase "We found that", but the capitalization does not matter. This is useful becuase when doing this search we don't necessarily carse if that phrase is the start of the scentence, and -i will find it with or without 'W' being capitalized. 



**Example 2**

    ivor@Ivors-Air docsearch % grep -i " 59" technical/biomed/*.txt
    technical/biomed/1471-2091-2-10.txt:          performed as described [ 59 ] . Stable NIH 3T3 infectants
    technical/biomed/1471-2091-2-13.txt:        59°C and at an external pH between 1-2 [ 20 ] . A
    technical/biomed/1471-2091-3-13.txt:          domain (Top67), a stop codon at amino acid 598 was
    technical/biomed/1471-2091-3-14.txt:          down-regulation of the JNK, AKT, and ERK kinases [ 59 ]
    technical/biomed/1471-2091-3-14.txt:          five are intronless genes [ 59 ] located on chromosome 2
    technical/biomed/1471-2091-3-4.txt:        inhibitor binding [ 37 42 55 56 57 58 59 ] . All of the
    technical/biomed/1471-2105-2-1.txt:          QUASI [ 59, 51]. Indeed, QUASI identifies six of the
    technical/biomed/1471-2105-3-2.txt:        large subunit [ 58 59 ] ) groups). With significant
    technical/biomed/1471-2105-3-2.txt:            contain ten or less introns. In contrast, 59%
    //more lines

I wanted to provide this case to demonstrate that numbers and symbols have no effect on -i. This is due to the case that -i only considers letters and capitalization. So i expect any and all files with " 59" to be returned.



**Example 3**

    ivor@Ivors-Air docsearch % grep -i "rna" technical/biomed/*.txt > RNAlinecount.txt



With an easy command such as this one above, you can store all the lines in the entire biomed file that contain rna, with any capitalization, and then observe or use that file as need be. 



### "grep -v"


**Example 1**

    technical/biomed/gb-2003-4-9-r58.txt:        voltage-sensor) in non-vertebrate Kv3 K +channels is of
    technical/biomed/gb-2003-4-9-r58.txt:        interest. The presence of four such repeats in invertebrate
    technical/biomed/gb-2003-4-9-r58.txt:        Kv3 channels and six in vertebrate Kv3 K +channels may help
    technical/biomed/gb-2003-4-9-r58.txt:        amino-acid mutations in this domain can affect


The -v makes it so the only lines that are returned are those without what is in the quotation. This a valueable tool which you can use to fine lines or sections within files that are **not** about a certain topic.



**Example 2**


    ivor@Ivors-Air docsearch % ls -1|grep -v ".txt"                
    DocSearchServer.java
    DocSearchTest.java
    README.md
    Server.java
    lib
    technical


Combining ls with the grep -v command allows you to return all the files that do not contain your parameters. This can be used to not have to see files or a certain type when searching or not show a group of names of files that you had earlier set. 



**Example 3**

    ivor@Ivors-Air docsearch % grep -v " " technical/biomed/*.txt         
    technical/biomed/1468-6708-3-1.txt:
    technical/biomed/1468-6708-3-10.txt:
    technical/biomed/1468-6708-3-3.txt:
    technical/biomed/1468-6708-3-4.txt:
    technical/biomed/1468-6708-3-7.txt:
    technical/biomed/1471-2091-2-10.txt:
    //many more below


I wanted to see if there are just plain empty lines in the files, and there are plenty. You can do with as you see, and either pry more to see if its a line break of is uncessary and can be delted.



### "grep -n"
Grep -n shows you the line of the match within the file. 
    ivor@Ivors-Air docsearch % grep -n "DNA" technical/biomed/*.txt 
    technical/biomed/1471-2105-3-28.txt:10:          G, C, and T for the four nucleotides found in DNA
    technical/biomed/1471-2105-3-28.txt:24:          n has the value of 2 for DNA and 5
    technical/biomed/1471-2105-3-28.txt:34:          s is mapped. For DNA one possible
    technical/biomed/1471-2105-3-3.txt:414:          two measurements, where genomics DNA sample of yeast
    technical/biomed/1471-2105-3-30.txt:12:        cis- regulatory DNA sequences. Here,
    technical/biomed/1471-2105-3-30.txt:107:          "words" in noncoding DNA, and applied to yeast. However,
    technical/biomed/1471-2105-3-30.txt:414:        DNA (a module). Ahab ignores distances between binding
    technical/biomed/1471-2105-3-34.txt:2



You can use this to quickly jump to specific parts of files since the line is more given information. 

**Example 2**

    ivor@Ivors-Air docsearch % grep -i -n "We found that" technical/biomed/*.txt
    technical/biomed/rr166.txt:380:        we found that both COX-2 protein expression and PGE 
    technical/biomed/rr167.txt:429:          microscopy, we found that the mean cross sectional
    technical/biomed/rr171.txt:356:          enzyme COX-2 [ 18 ] . We found that COX-2 mRNA was
    technical/biomed/rr171.txt:571:        kinases and TNF-α [ 45 46 47 ] . We found that endotoxin
    technical/biomed/rr171.txt:588:        NF-κB and CREB [ 21 ] . We found that activated NF-κB and
    technical/biomed/rr191.txt:67:        pathways. We found that insulin probably inhibits SP-A gene
    technical/biomed/rr191.txt:474:        We found that wortmannin and rapamycin had no effect on



This case shows us how it returns the exact same thing as the grep -i of "We found that" but with the line added.

**Example 3** 

    ivor@Ivors-Air docsearch % grep -v -n " " technical/biomed/*.txt    
    technical/biomed/rr166.txt:1:
    technical/biomed/rr167.txt:1:
    technical/biomed/rr171.txt:1:
    technical/biomed/rr172.txt:1:
    technical/biomed/rr191.txt:1:
    technical/biomed/rr196.txt:1:
    technical/biomed/rr37.txt:1:
    technical/biomed/rr73.txt:1:
    technical/biomed/rr74.txt:1:


With this quick test I found out that all the rr files dont have any text on thier first line. 