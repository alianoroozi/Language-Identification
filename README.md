# Language Identifier

A Python implementation of **language identification** using [Canvar and Trenkle’s approach](https://www.let.rug.nl/vannoord/TextCat/textcat.pdf) and the [WiLI-2018 - Wikipedia Language Identification database](https://zenodo.org/record/841984).

The WiLI-2018 – Wikipedia Language Identification dataset has been designed as a benchmark dataset and contains 235,000 paragraphs in 235 languages. The dataset is balanced and a train-test split is provided. 

Instead of working with all 235 languages, I work with 20 languages to make the analysis easier.

I use Canvar and Trenkle’s seminal paper from 1994 to compute n-grams, with n varying from 1 to 5, and then use a vector containing the most frequent 300 n-grams as a signature or profile of the language under consideration. So, to start, I compute a language profile set. e.g. P = {pe, ps} where pe is the profile vector for English, and ps is the profile vector for Spanish.

Given a test document t whose language is not known, the algorithm creates a profile pt for it using the same approach, i.e., by computing n-grams and making a 300-long vector of most common n-grams in t. It then computes the distance between the profile vectors for the two languages, pe and ps, and the test document vector pt. The distance can be computed using Canvar and Trenkle’s out-of-place measure. The document t is assumed to be in the language whose profile is the nearest.

Finally, the accuracy of language identification for the 20-language dataset is measured.

