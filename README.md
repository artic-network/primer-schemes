# primer-schemes

Primer schemes for real-time genome epidemiology

## updated scheme file format

> updated: 25.08.2020

### changes

With the major version bump to [Primal Scheme](https://github.com/aresti/primalscheme), primer schemes are now output to `*.primer.bed` files.

These new files aren't much different to the old `*.scheme.bed` files and the same information is contained within, but they now conform to the [BED standard](https://genome.ucsc.edu/FAQ/FAQformat.html#format1).

The new format has the following columns:

| column | name       | type         | description                                               |
| ------ | ---------- | ------------ | --------------------------------------------------------- |
| 1      | chrom      | string       | primer reference sequence                                 |
| 2      | chromStart | int          | starting position of the primer in the reference sequence |
| 3      | chomEnd    | int          | ending position of the primer in the reference sequence   |
| 4      | name       | string       | primer name                                               |
| 5      | primerPool | int          | primer pool<sup>\*</sup>                                  |
| 6      | strand     | string (+/-) | primer direction                                          |

<sup>\*</sup> column 5 in the BED spec is an int for score, whereas here we are using it to denote primerPool.

### liftover

The `liftover.py` script was used to create files in the new format for existing schemes in this repository.

Schemes were updated using the following command:

```
for i in */V*/*.scheme.bed; do scripts/liftover.py -i $i -o ${i%%.scheme.bed}.primer.bed
```
