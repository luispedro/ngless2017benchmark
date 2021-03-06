# MOCAT benchmark

Note that the results of running this benchmark are provided in
`../data/precomputed`.

Provided results were generated with MOCAT v2.0.3

## Requirements

You must have [jug](http://jug.rtfd.io) and [pandas](https://pandas.pydata.org)
and have run the `download-data.py` script at the top level of this repository.

Additionally you should run `download-mocat-and-data.py` which will download
MOCAT, all necessary data and execute MOCAT to index and prepare.
This will require ca. 140GB of disk space and access to an SGE queuing system.


## Running MOCAT benchmark

After done with `download-mocat-and-data.py`, running:

    jug execute

will generate the file `mocat_benchmark.csv` with the results. Note that this
will produce very large intermediate files and take several days to complete.
Most steps can be run with under 32GB of RAM with exception of Ocean profiling
which on our local benchmark required ~350GB of RAM.

The files `run_mocat_gut.sh` and `run_mocat_tara.sh` contain the full pipelines.


## Troubleshooting

If your perl installation is missing some third party libraries you might run
into errors. If this happens check the files in the logs/ folder for debugging
information.

Depending on your system it may also be necessary to modify `MOCAT_dir` in
`MOCAT.cfg` and `MOCAT-simulated.cfg` to be an absolute path to the MOCAT subfolder
in the same location as this README. That is, if this README is in `/path/to/README`
`MOCAT_dir` should read `/path/to/MOCAT`.

### OM-RGC profiling

MOCAT's OM-RGC.zip includes a `functional.map` file with incorrect IDs.
These don't match the OM-RGC fasta file in the same zip file.

To address this a new `functional.map` file was created.
The correct version is now downloaded by download-mocat-and-data.py .
