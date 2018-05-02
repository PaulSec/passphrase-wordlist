# Overview
People think they are getting smarter by using passphrases. Let's prove them wrong!

This project includes a massive wordlist of phrases (17,737,982) and two hashcat rule files for GPU-based cracking.

The 'passphrases.txt' file is stored in Git Large File Storage (GLFS), so **download via <a download href="https://github.com/initstring/passphrase-wordlist/raw/master/passphrases.txt">this link</a>** or use git if you known what you're doing with GLFS.

Use both rules for best results.

Here is an example for NTLMv2 hashes:

```
./hashcat64.bin -a 0 -m 0 hashes.txt ~/passphrase-wordlist/passphrases.txt -r ~/passphrase-wordlist/rule1.rule -r ~/passphrase-wordlist/rule2.rule -w 2
```

# Sources Used
So far, I've scraped the following: <br>
- [15,000 Useful Phrases](https://www.gutenberg.org/ebooks/18362)
- Urban Dictionary dataset pulled Dec 09 2017 using [this great script](https://github.com/mattbierner/urban-dictionary-word-list).
- Song lyrics for Rolling Stone's "top 100" artists using my [lyric scraping tool](https://github.com/initstring/lyricpass).
- Movie titles and lines from this [Cornell project](http://www.cs.cornell.edu/~cristian//Cornell_Movie-Dialogs_Corpus.html).
- "Titles" from the [IMDB dataset](https://www.kaggle.com/orgesleka/imdbmovies) on Kaggle.
- [Global POI dataset](http://download.geonames.org/export/dump/) using the 'allCountries' file.
- [Quotables](https://www.kaggle.com/alvations/quotables) dataset on Kaggle.
- [MemeTracker](https://www.kaggle.com/snap/snap-memetracker) dataset from Kaggle.
- [Wikipedia Article Titles](https://www.kaggle.com/residentmario/wikipedia-article-titles) dataset from Kaggle.
- [1,800 English Phrases](https://www.phrases.org.uk/meanings/phrases-and-sayings-list.html)
- [2016 US Presidential Debates](https://www.kaggle.com/kinguistics/2016-us-presidential-primary-debates) dataset on Kaggle.

# Cleaning sources
Check out the script [cleanup.py](https://github.com/initstring/passphrase-wordlist/blob/master/cleanup.py) to see how I've cleaned the raw sources. You can find the pre-cleaned data [here](https://github.com/initstring/passphrase-wordlist/tree/master/raw-sources).

# Hashcat Rules
Given the phrase `take the red pill` the first hashcat rule will output the following
```
take the red pill
take-the-red-pill
take.the.red.pill
take,the,red,pill
take_the_red_pill
taketheredpill
Take the red pill
TAKE THE RED PILL
tAKE THE RED PILL
Taketheredpill
tAKETHEREDPILL
TAKETHEREDPILL
Take The Red Pill
TakeTheRedPill
Take-The-Red-Pill
Take.The.Red.Pill
Take,The,Red,Pill
Take_The_Red_Pill
```

Adding in the second hashcat rule makes things get a bit more interesting. That will return a huge list per candidate. Here are a couple examples:

```
T@k3Th3R3dPill!
T@ke-The-Red-Pill
taketheredpill2020!
T0KE THE RED PILL (unintentional humor)
```

Enjoy!
