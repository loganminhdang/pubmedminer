# pubmedminer

🚀 Getting Started

Literature mining can take days. I created this script to speed up this process, taking advantage of APIs, parallelisation, and the PubMed digital literature repository. 

**1. Prerequisites**

First, ensure you have Python 3.8+ installed. Then, clone the repository and install the necessary dependencies.

*A. Clone the repository:*

```bash
git clone https://github.com/your-username/publication-miner.git
cd publication-miner
```

*B. Install dependencies:*
The only external library required is requests. You can install it directly.

```bash
# It is recommended to use a virtual environment (either Mamba or python)
python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`

# Install from requirements file
pip install -r requirements.txt
(If a requirements.txt file is not available, simply run pip install requests)
```

**2. Prepare Your Input Files**

The tool requires two input files: a list of genes and a JSON file defining your search terms.

Gene List File (genes.txt)
Create a simple text file with one gene symbol (or any search term) per line.

Example genes.txt:

```text
TCF21
WT1
TBX18
VEGFA
PDGFRA
```

Semantics Keyword File (semantics.json)
Create a JSON file that groups your search concepts. Each key is a category, and the value is a list of related keywords and synonyms.

Example semantics.json for a cardiac study:

```json
{
    "coronary_vessel": [
        "coronary vessel",
        "coronary vasculature",
        "coronary angiogenesis"
    ],
    "myocardial_growth": [
        "myocardial growth",
        "cardiomyocyte proliferation",
        "heart development"
    ],
    "valvulogenesis": [
        "valvulogenesis",
        "heart valve development",
        "endocardial cushion"
    ]
}
```
**3. Run the Tool**
Execute the script from your terminal. You must provide the paths to your two input files, a name for your output file, and your email address for polite API access.

*Basic Usage*

This command runs a search on your gene list with the specified semantics and saves the output to epicardial_results.tsv.

```bash
python publication_miner.py genes.txt semantics.json epicardial_results.tsv --email "your.name@example.com"
```
*Advanced Usage*

This example performs a broader search. It includes pre-prints, uses a different context keyword ("sleep"), increases the number of results to 15 per gene, and uses 12 parallel threads for more speed.

```bash
python publication_miner.py genes.txt semantics.json sleep_study_results.tsv --email "your.name@example.com" --context "sleep" --include-preprints -n 15 -t 12
```
**4. Check Your Output**

After the script completes, you will find a new file named epicardial_results.tsv (or whatever you named it) in your directory. This file is a tab-separated values (TSV) file, which can be opened directly in Excel, Google Sheets, R, or Python for your analysis.
