Make sure you use the --recursive option to clone, or otherwise
make sure the Util submodule is correctly checked out.
If you want to generate dictionaries also manually clone the DictionaryPC
repository, it needs to be at the same level as this one, not inside it.

To compile the APK, just open this repository in Android Studio.
You can also use gradle directly.
Note that compilation is only tested on Linux.
It is possible to disable the smallicu/makesmallicu step if it causes
issues, though help to debug any such issue would be welcome.

And approximation of the steps for generating dictionaries:
- go into the DictionaryPC repository
- run data/downloadInputs.sh to get the data
- run ./compile.sh (probably needs quite a few things to be installed or paths in it configured)
- run ./WiktionarySplitter.sh
- run ./generate_dictionaries.sh.
  You might want to edit the settings at the start of the file
  so it does not generate all dictionaries, and edit its input files
  like EN-trans-dictlist.txt to add new dictionaries.
  For a more manual approach, the commands it runs are something like
 ./run.sh --lang1=ES --lang2=PT --lang1Stoplist=data/inputs/stoplists/es.txt \
 --dictOut=data/outputs/ES-PT.quickdic \
 --dictInfo="(EN)Wiktionary-based ES-PT dictionary. --input1=data/inputs/wikiSplit/en/EN.data" \
 --input1Name=enwikitionary --input1Format=EnTranslationToTranslation \
 --input1LangPattern1=es --input1LangPattern2=pt
