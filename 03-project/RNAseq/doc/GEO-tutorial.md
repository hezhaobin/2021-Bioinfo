## Goal

Understand the type of data GEO stores and how it stores them, and how to access them. For example, is GEO only for transcriptomics data? Does it store raw sequencing data? Does it accept or even require the authors to upload processed data in the form of log2 ratios or read counts per gene?

## Notes

Mostly based on the GEO [faq page](https://www.ncbi.nlm.nih.gov/geo/info/faq.html#kinds) 

### What types of data does GEO store?

GEO was designed around the common features of most of the high-throughput and parallel molecular abundance-measuring technologies in use today. These include data generated from microarray and high-throughput sequence technologies, for example:

- Gene expression profiling by microarray or next-generation sequencing (see [examples](https://www.ncbi.nlm.nih.gov/gds?term=(expression+profiling+by+array[DataSet+Type]+OR+expression+profiling+by+genome+tiling+array[DataSet+Type]+OR+expression+profiling+by+high+throughput+sequencing[DataSet+Type])+AND+gse[Entry Type]))
- Non-coding RNA profiling by microarray or next-generation sequencing (see [examples](https://www.ncbi.nlm.nih.gov/gds?term=(non+coding+rna+profiling+by+array[DataSet+Type]+OR+non+coding+rna+profiling+by+genome+tiling+array[DataSet+Type]+OR+non+coding+rna+profiling+by+high+throughput+sequencing[DataSet+Type])+AND+gse[Entry Type]))
- Chromatin immunoprecipitation (ChIP) profiling by microarray or next-generation sequencing (see [examples](https://www.ncbi.nlm.nih.gov/gds?term=(genome+binding/occupancy+profiling+by+array[DataSet+Type]+OR+genome+binding/occupancy+profiling+by+genome+tiling+array[DataSet+Type]+OR+genome+binding/occupancy+profiling+by+high+throughput+sequencing[DataSet+Type])+AND+gse[Entry Type]))
- Genome methylation profiling by microarray or next-generation sequencing (see [examples](https://www.ncbi.nlm.nih.gov/gds?term=(methylation+profiling+by+array[DataSet+Type]+OR+methylation+profiling+by+genome+tiling+array[DataSet+Type]+OR+methylation+profiling+by+high+throughput+sequencing[DataSet+Type])+AND+gse[Entry Type]))
- High-throughput RT-PCR (see [examples](https://www.ncbi.nlm.nih.gov/gds?term="expression+profiling+by+rt+pcr"[DataSet+Type]))
- Genome variation profiling by array (arrayCGH) (see [examples](https://www.ncbi.nlm.nih.gov/gds?term=(genome+variation+profiling+by+array[DataSet+Type]+OR+genome+variation+profiling+by+genome+tiling+array[DataSet+Type]+OR+genome+variation+profiling+by+snp+array[DataSet+Type])+AND+gse[Entry Type]))
- SNP arrays (see [examples](https://www.ncbi.nlm.nih.gov/gds?term=snp+genotyping+by+snp+array[DataSet+Type]+AND+gse[Entry Type])) (see [human subject FAQ](https://www.ncbi.nlm.nih.gov/geo/info/faq.html#patient))
- Serial Analysis of Gene Expression (SAGE) (see [examples](https://www.ncbi.nlm.nih.gov/gds?term=expression+profiling+by+sage[DataSet+Type]+AND+gse[Entry Type]))
- Protein arrays (see [examples](https://www.ncbi.nlm.nih.gov/gds?term=protein+profiling+by+protein+array[DataSet+Type]+AND+gse[Entry Type]))

### Does GEO store raw and processed data?

Again from GEO [faq page](https://www.ncbi.nlm.nih.gov/geo/info/faq.html#kinds): "Yes. GEO requires raw data, processed data and metadata. Raw data facilitates the unambiguous interpretation of the data and potential verification of conclusions. For microarray data, raw data may be supplied either within the Sample record data tables or as external supplementary data files, e.g., Affymetrix CEL. **For high-throughput sequencing, GEO brokers the complete set of raw data files, e.g., FASTQ, to the SRA database on your behalf.**" (emphasis added)

### What is the data structure in GEO?

Based on [GEO overview](https://www.ncbi.nlm.nih.gov/geo/info/overview.html), the GEO database is organized as follows:

![GEO database organization](https://www.ncbi.nlm.nih.gov/geo/img/geo_overview.jpg)

- Platform
  composed of a summary description of the array or sequencer and, for array-based Platforms, a data table defining the array template.Each Platform record is assigned a unique and stable GEO accession number (GPLxxx). A Platform may reference many Samples that have been submitted by multiple submitters.
- Sample
  describes the conditions under which an individual Sample was handled, the manipulations it underwent, and the abundance measurement of each element derived from it. Each Sample record is assigned a unique and stable GEO accession number (GSMxxx). A Sample entity must reference only one Platform and may be included in multiple Series.
- Series
  links together a group of related Samples and provides a focal point and description of the whole study. Series records may also contain tables describing extracted data, summary conclusions, or analyses. Each Series record is assigned a unique and stable GEO accession number (GSExxx).
- Datasets
  is assembled by GEO curators and represents a curated collection of biologically and statistically comparable GEO Samples, based on the same platform and calculated in an equivalent manner, that is, considerations such as background processing and normalization are consistent across the DataSet.
  **warning**: Not all submitted data are suitable for DataSet assembly and we are experiencing a backlog in DataSet creation, so not all Series have corresponding DataSet record(s).
- Profile
  is derived from a Dataset and focuses on a single gene: a Profile consists of the expression measurements for an individual gene across all Samples in a DataSet. Profiles can be searched using the GEO Profiles interface.

### How can I query and analyze GEO data?

"Once you have found a curated DataSet or Series of interest, there are several features available that help identify interesting gene expression profiles within that study. Curated DataSets include a [find genes](https://www.ncbi.nlm.nih.gov/geo/info/datasets.html#findgenes) feature, [cluster heatmaps](https://www.ncbi.nlm.nih.gov/geo/info/datasets.html#heatmap) and a [t-test sample comparison tool](https://www.ncbi.nlm.nih.gov/geo/info/datasets.html#compare). Once you have identified gene expression [profile charts](https://www.ncbi.nlm.nih.gov/geo/info/profiles.html#chart) of interest, there are several types of [neighbors links](https://www.ncbi.nlm.nih.gov/geo/info/profiles.html#e) on the Profile records that help identify related genes of interest. If no curated DataSet is available, it may be appropriate to analyze the Series using [GEO2R](https://www.ncbi.nlm.nih.gov/geo/geo2r/), which compares groups of Samples and identifies differentially expressed genes. Alternatively, if you prefer to perform your own analysis using your favorite software package, the value matrix tables within the DataSet full SOFT files available from the [DataSet records](https://www.ncbi.nlm.nih.gov/geo/info/datasets.html#record), or the Series Matrix File or supplementary files linked at the foot of Series records, may prove suitable. Finally, thousands of GEO data tracks have been uploaded for viewing on NCBI’s Genome Data Viewer. All records with tracks can be retrieved by searching with [trackfilter](https://www.ncbi.nlm.nih.gov/gds/?term=trackfilter); the 'See on Genome Data Viewer' button on those records links to corresponding tracks on NCBI’s Genome Data Viewer (see [example tracks](https://www.ncbi.nlm.nih.gov/genome/gdv/browser/?context=GEO&acc=GSE86740))."

### What data types are provided with next-generation sequence submissions?

*Processed sequence data files*: GEO hosts processed sequence data files, which are linked at the bottom of Sample and/or Series records as supplementary files. Requirements for processed data files are not yet fully standardized and will depend on the nature of the study, but data typically include genome tracks or expression counts.

*Raw sequence data files*: Raw data are loaded to NCBI's [Sequence Read Archive](https://trace.ncbi.nlm.nih.gov/Traces/sra/sra.cgi?) (SRA) database. Use the [SRA Run Selector](https://www.ncbi.nlm.nih.gov/Traces/study/?go=home) to list and select Runs to be downloaded or analyzed with the [SRA Toolkit](https://trace.ncbi.nlm.nih.gov/Traces/sra/sra.cgi?view=toolkit_doc). If you have questions about SRA format or the SRA toolkit, please [e-mail SRA](mailto:sra@ncbi.nlm.nih.gov) directly.