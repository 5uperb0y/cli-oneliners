# Display the amount of disk space
`df -h`

# Convert interleaved fasta files to single-line
`awk '{if(NR==1) {print $0} else {if($0 ~ /^>/) {print "\n"$0} else {printf $0}}}' <fasta>`
https://www.ecseq.com/support/ngs-snippets/convert-interleaved-fasta-files-to-single-line

# Transcribing DNA into RNA using `tr`
`echo <dna> | tr Tt Uu`
 
# Complementing a Strand of DNA
`echo <dna> | rev | tr ATCGatcg TAGCtagc`
 
# Print line number X of a file
`head -n <num> <file> | tail -n 1`
https://www.linuxquestions.org/questions/programming-9/print-line-number-x-of-a-file-in-shell-273849/

# Remove duplicate lines from a file 
`awk '!seen[$0]++' <file>`
https://linux.cn/article-6881-1.html

# Randomly pick a line from a file
`shuf -n 1 < <file>`
 
# List docker image ids without name and tag
`docker images | awk '/(none.*){2}/ {print $3}'`
 
# Remove docker images without name and tag
`docker images | awk '/(none.*){2}/ {print $3}' | xargs -I {} docker rmi {}`
 
# Unzip files with suffix `.tar.gz`
`tar -zxvf <file>`
https://note.drx.tw/2008/04/command.html

# Unzip files with suffix `.gz`
`gunzip <file>`
https://note.drx.tw/2008/04/command.html
 
# Remove secondary alignment reads from a bam file
`samtools view -F 256 <bam>`
see flags at https://www.biostars.org/p/206396/

# Keep secondary alignment reads from a bam file
`samtools view -f 256 <bam>`
see flags at https://www.biostars.org/p/206396/