![Version](https://img.shields.io/github/v/release/DCMLab/wf_bach_sonatas?display_name=tag)
[![DOI](https://zenodo.org/badge/388190018.svg)](https://doi.org/10.5281/zenodo.14997133)
![GitHub repo size](https://img.shields.io/github/repo-size/DCMLab/wf_bach_sonatas)
![License](https://img.shields.io/badge/license-CC%20BY--NC--SA%204.0-9cf)


This is a README file for a data repository originating from the [DCML corpus initiative](https://github.com/DCMLab/dcml_corpora)
and serves as welcome page for both 

* the GitHub repo [https://github.com/DCMLab/wf_bach_sonatas](https://github.com/DCMLab/wf_bach_sonatas) and the corresponding
* documentation page [https://dcmlab.github.io/wf_bach_sonatas](https://dcmlab.github.io/wf_bach_sonatas)

For information on how to obtain and use the dataset, please refer to [this documentation page](https://dcmlab.github.io/wf_bach_sonatas/introduction).

When you use (parts of) this dataset in your work, please read and cite the accompanying data report:

_Hentschel, J., Rammos, Y., Neuwirth, M., & Rohrmeier, M. (2025). A corpus and a modular infrastructure for the 
empirical study of (an)notated music. Scientific Data, 12(1), 685. https://doi.org/10.1038/s41597-025-04976-z_

# Wilhelm Friedemann Bach – Piano Sonatas (A corpus of annotated scores)

The eldest of the Bach sons was arguably the most personally headstrong and professionally unsuccessful of them. This
may have found some expression in his style, which remained committed to Baroque complexity even as his younger brothers
adopted more fashionable, accessible styles. Of the three sonatas in this repository, only F.3 was published in the
composer's lifetime; the other two are known through undated manuscripts. These are highly virtuosic works befitting
their composer's reputation as a ferocious improviser. Examination of the harmonies at work here reveals the composer's
application of a harmonic technique resembling that of his father to the expansive sonata forms that were emergent over
the course of the 18th century, making this repository of little-known works remarkably pivotal in understanding this
period.

## Getting the data

* download repository as a [ZIP file](https://github.com/DCMLab/wf_bach_sonatas/archive/main.zip)
* download a [Frictionless Datapackage](https://specs.frictionlessdata.io/data-package/) that includes concatenations
  of the TSV files in the four folders (`measures`, `notes`, `chords`, and `harmonies`) and a JSON descriptor:
  * [wf_bach_sonatas.zip](https://github.com/DCMLab/wf_bach_sonatas/releases/latest/download/wf_bach_sonatas.zip)
  * [wf_bach_sonatas.datapackage.json](https://github.com/DCMLab/wf_bach_sonatas/releases/latest/download/wf_bach_sonatas.datapackage.json)
* clone the repo: `git clone https://github.com/DCMLab/wf_bach_sonatas.git` 


## Data Formats

Each piece in this corpus is represented by five files with identical name prefixes, each in its own folder. 
For example, the first movement of the C-major sonata F. 1 has the following files:

* `MS3/F001_n08a.mscx`: Uncompressed MuseScore 3.6.2 file including the music and annotation labels.
* `notes/F001_n08a.notes.tsv`: A table of all note heads contained in the score and their relevant features (not each of them represents an onset, some are tied together)
* `measures/F001_n08a.measures.tsv`: A table with relevant information about the measures in the score.
* `chords/F001_n08a.chords.tsv`: A table containing layer-wise unique onset positions with the musical markup (such as dynamics, articulation, lyrics, figured bass, etc.).
* `harmonies/F001_n08a.harmonies.tsv`: A table of the included harmony labels (including cadences and phrases) with their positions in the score.

Each TSV file comes with its own JSON descriptor that describes the meanings and datatypes of the columns ("fields") it contains,
follows the [Frictionless specification](https://specs.frictionlessdata.io/tabular-data-resource/),
and can be used to validate and correctly load the described file. 

### Opening Scores

After navigating to your local copy, you can open the scores in the folder `MS3` with the free and open source score
editor [MuseScore](https://musescore.org). Please note that the scores have been edited, annotated and tested with
[MuseScore 3.6.2](https://github.com/musescore/MuseScore/releases/tag/v3.6.2). 
MuseScore 4 has since been released which renders them correctly but cannot store them back in the same format.

### Opening TSV files in a spreadsheet

Tab-separated value (TSV) files are like Comma-separated value (CSV) files and can be opened with most modern text
editors. However, for correctly displaying the columns, you might want to use a spreadsheet or an addon for your
favourite text editor. When you use a spreadsheet such as Excel, it might annoy you by interpreting fractions as
dates. This can be circumvented by using `Data --> From Text/CSV` or the free alternative
[LibreOffice Calc](https://www.libreoffice.org/download/download/). Other than that, TSV data can be loaded with
every modern programming language.

### Loading TSV files in Python

Since the TSV files contain null values, lists, fractions, and numbers that are to be treated as strings, you may want
to use this code to load any TSV files related to this repository (provided you're doing it in Python). After a quick
`pip install -U ms3` (requires Python 3.10 or later) you'll be able to load any TSV like this:

```python
import ms3

labels = ms3.load_tsv("harmonies/F001_n08a.harmonies.tsv")
notes = ms3.load_tsv("notes/F001_n08a.notes.tsv")
```


## Version history

See the [GitHub releases](https://github.com/DCMLab/wf_bach_sonatas/releases).

## Questions, Suggestions, Corrections, Bug Reports

Please [create an issue](https://github.com/DCMLab/wf_bach_sonatas/issues) and/or feel free to fork and submit pull requests.

## Cite as

> Hentschel, J., Rammos, Y., Neuwirth, M., & Rohrmeier, M. (2025). A corpus and a modular infrastructure for the empirical study of (an)notated music. Scientific Data, 12(1), 685. https://doi.org/10.1038/s41597-025-04976-z

## License

Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License ([CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)).

![cc-by-nc-sa-image](https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png)

## File naming convention

```regex
F(?<falck>\d{3})_
n(?<no>\d{2})
(?<movement>a|b|c)
```

## Overview
|file_name|measures|labels|standard|                     annotators                     |reviewers|
|---------|-------:|-----:|--------|----------------------------------------------------|---------|
|F001_n08a|      63|   204|2.3.0   |Christos Giannopoulos (1.0.0), Davor Krkljus (2.3.0)|DK, AN   |
|F001_n08b|      40|    77|2.3.0   |Christos Giannopoulos (1.0.0), Davor Krkljus (2.3.0)|DK, AN   |
|F001_n08c|     101|   217|2.3.0   |Christos Giannopoulos (1.0.0), Davor Krkljus (2.3.0)|DK, AN   |
|F002_n07a|      62|   140|2.3.0   |Christos Giannopoulos (1.0.0), Davor Krkljus (2.3.0)|DK, AN   |
|F002_n07b|      44|   120|2.3.0   |Christos Giannopoulos (1.0.0), Davor Krkljus (2.3.0)|DK, AN   |
|F002_n07c|      66|   166|2.3.0   |Christos Giannopoulos (1.0.0), Davor Krkljus (2.3.0)|DK, AN   |
|F003_n04a|      83|   316|2.3.0   |Christos Giannopoulos (1.0.0), Davor Krkljus (2.3.0)|DK, ST   |
|F003_n04b|      64|   223|2.3.0   |Christos Giannopoulos (1.0.0), Davor Krkljus (2.3.0)|DK, ST   |
|F003_n04c|     108|   290|2.3.0   |Christos Giannopoulos (1.0.0), Davor Krkljus (2.3.0)|DK, AN   |


*Overview table automatically updated using [ms3](https://ms3.readthedocs.io/).*
