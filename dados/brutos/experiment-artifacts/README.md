# A Controlled Experiment on the Impact of Microservice API Patterns on Understandability

This repository includes the data set of responses from 66 participants and the analysis scripts of a controlled experiment about the impact of microservice API patterns on understandability.

The following files can be found here:

- A Markdown file with all experiment tasks (`pattern-tasks.md`)
- A Jupyter notebook for the cleaning and preprocessing of the raw data (`01-data-preprocessing.ipynb`)
- A Jupyter for the analysis of the final experiment data (`02-data-analysis.ipynb`)
- The raw data set exported from the experiment tool, which is used by notebook 01 (`results-01-raw.csv`)
- The cleaned data set, which is the output of notebook 01 (`results-02-cleaned.csv`)
- The final data set used by notebook 02, which is a refined version of the cleaned set based on a manual evaluation of free-text questions (`results-03-final.csv`)

To install the necessary dependencies for the Jupyter notebooks, execute `pip install -r requirements.txt`.