These are my notes for basic commands     <br>
**pwd** #find my position <br>
**ls**  #folder contents  <br>
**cd file_name**  #open folder <br>
**cd** #return back to home dir <br>
**cd ..** #go back 1 step <br>
**cd ../..**  #go back 2 steps<br>
**less** #show full file's content <br>
#After **less** move down fast/slow with **d/e** and up with **u/y** and return with **q** <br>
**cat** #show full content but not in a different window ##use it only for small files <br>
**nano** #It lets you edit the file <br>
#move up with **ctrl+y** or **pageup** move down with **ctrl+v** or **pagedown** and return back with **ctrl+x**<br>
**ls -lh xfile.bed** #show properties of the file ##for example size <br> 
**wc -l xfile.bed** #show the number of lines in the file <br>
**head -n 10** #show the first 10 lines <br>
**grep "^>"** #print me all the lines that start with ">" <br>
**grep -v ">"** #count me all the lines that doesn't start with ">" <br>
**grep "^.\{11\}>" xfile.fa** #check how many lines have  character 12 as ">" <br>
**sed -n '12p' out.fa | grep ">"** #go to line 12 and print it if it has '>' <br>
**sed -n '2p' genes_sequence.fa | grep -o 'A' | wc -l** # go to line 2 and for every A make a line and then count all the lines ## -o means make line for every A <br>
**grep -cP "^.{11}>"** #check how many lines have  character 12 as ">" <br>
##after p we can add \d for 0-9 \D any character except number \w for letter/number/_ \W any character except number/letter \s for space after \S no space after  **[ATCG]{10,20}**to find sequences form 10 to 20 nucleotides <br>
**head -n 200 yfile.fa | grep -cP '^[ATCG]{10,100}$'** #for the first 100 genes find count the ones with length from 10 to 100 ## if you want repeats included write -icP this way searches for the letters capitals or not <br>
**grep -iB 1 "ATGCGATCG" yfile.fa** print the genes with this sequence <br>
**awk '!seen[$$1]++'** # its one $$$ Ι cant type 1 and this means give me only what you see first time <br>
**awk '{print $$$$1, $$$$$2, $$$$$$3, $$$$$$$3}' OFS="\t" file.bed** <br>
**samtools faidx genome.fa** #Create the genome index file (.fai) <br>
**cut -f1,2 genome.fa.fai > genome.chrom.sizes** #Extract chromosome names and lengths (columns 1 and 2) <br>
****<br>
<br>

These are my notes for bedtools <br>
**Bedtools sorted -i xfile.bed > yfile.bed** #sorts your bed file according to the genomic coordinates<br>
** bedtools getfasta -fi xfile.fa -bed yfile.bed -fo yfile.fa** #get all genes fasta from xfile.fa using yfile.bed and make file yfile.fa<br>
**bedtools sort -i genes.bed -g genome.chrom.sizes > genes.sorted.bed** #Sort the BED file according to the genome chromosome order
**bedtools complement -i genes.sorted.bed -g genome.chrom.sizes > intergenic_regions.bed** #Find the regions outside gene
