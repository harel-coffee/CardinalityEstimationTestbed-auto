# CardinalityEstimationTestbed
CardinalityEstimationTestbed

## Experiment of synthetic
#### Generate_data_sql
`cd CardinalityEstimationTestbed\Synthetic`\
`python generate_data_sql.py --cols ' + str(cols) + ' --distinct ' + str(distinct) + ' --corr ' + str(corr) + ' --skew ' + str(skew)`
#### Get_sql_truecard
`python get_truecard.py --version cols_' + str(cols) + '_distinct_' + str(distinct) + '_corr_' + str(corr) + '_skew_' + str(skew)`
#### Get_result
`python get_result.py`

## Experiment of overall
### Real Datasets download
- Download the [IMDB](http://homepages.cwi.nl/~boncz/job/imdb.tgz) data tables to: `../train-test-data/imdbdataset-str/`\
- Download the [forest, power](http://archive.ics.uci.edu/) data tables to: `../train-test-data/forest_&_power-data-sql/`\
Begin by doing a simple job on the table, removing some unused columns. For Forest We use ﬁrst 10 numeric attributes; For Power We used the 7 numeric attributes after the ﬁrst two attributes (date and time).
### Imdb
- First, the strings in the data tables should be converted to numbers.\
`cd CardinalityEstimationTestbed\Overall\imdb`\
`python data_str2num.py`
#### Cols
- Start by generating training and testing queries queries for different columns.\
`cd CardinalityEstimationTestbed\Overall\imdb\cols`\
`python generate_sql.py`
- Data tables and queries paths need to be configured, and some methods need Schemafile to be rewritten.
- Then refer to `run.sh` in each method folder to execute the code to get the result.
#### Distinct
- First, the data of the distinct is generated and populated.\
`cd CardinalityEstimationTestbed\Overall\imdb\distinct`\
`python data_process.py`
- Next, generate training and testing queries of different distinct.\
`python sql_generate.py`
- Data tables and queries paths need to be configured, and some methods need Schemafile to be rewritten.
- Then refer to `run.sh` in each method folder to execute the code to get the result.

### Forest_&_power
- Start by generating training and testing queries for different columns.\
`cd CardinalityEstimationTestbed\Overall\forest_&_power`\
`python generate_sql.py`
- Data tables and queries paths need to be configured, and some methods need Schemafile to be rewritten.
- Then refer to `forest.sh, power.sh` in each method folder to execute the code to get the result.
