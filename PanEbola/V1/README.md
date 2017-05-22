#Pan-Ebola multiplex PCR scheme (1kb - for ONT)
#Contributors: Nick Loman, Josh Quick, Andrew Rambaut

Requirements:

- Entrez eutils
- Primal Scheme (primal.zibraproject.org)

1) ``grep ">" EBOV_Reference_Set_35.fasta | cut -f1 -d '|' | sed 's/>//' > accessions.txt``
2) ``cat accessions.txt | xargs -L1 ./getacc.sh > EBOV_Reference_Set_35.originals.fasta``
3) Run result through Primal Scheme (primal.zibraproject.org) with 1000 amplicon size.

