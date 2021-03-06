## Welcome to Linked Drug Data

This project demonstrates SPARQL queries that make use of five kinds of drug database (USP, ATC, KEGG, SIDER, and MEDIS) to identify individual drug codes used in Japan.
To try these queries, you can download this project and do following instructions.

## Getting Started

1. Make sure that Python 3.1 or later and Java 1.7 or later are installed. 
   
   Also make sure your system has 8gb memory or more.

2. Unzip ./rdf/medis_201506.nq.zip and ./rdf/sider_201506.nq.zip

3. Run 'MakeRDF.py' to make the other RDF files. 

   This script downloads necessary resources and makes RDF files automatically.

        $ python MakeRDF.py

4. Make sure that you have five RDF files in ./rdf folder.

        medis_201506.nq, sider_201506, atc_201512.nq, usp_201512.nq, kegg_201512.nq

5. Then you can try SPARQL queries below from your terminal, which identify individual drug codes based on the details of drug properties.

## Query 1:

 Description: Querying individual drug codes that are classified as 'renin angiotensin inhibitors' in ATC Classification System.

 Results: 476 Rows.

      $ ./apache-jena-3.0.0/bin/arq --data ./rdf/atc_201512.nq --data ./rdf/medis_201506.nq --data ./rdf/kegg_201512.nq --query ./queries/q1.rq

## Query 2:

 Description: Querying individual drug codes that may cause 'leukopenia' or 'neutropenia' as adverse events, which are defined by SIDER.

 Results: 131 Rows.

 This query require your system memory 8gb or more, and may take several minutes.

      $ ./apache-jena-3.0.0/bin/arq --data ./rdf/atc_201512.nq --data ./rdf/medis_201506.nq --data ./rdf/kegg_201512.nq --data ./rdf/sider_201506.nq --query ./queries/q3.rq

## Query 3:

 Description: Querying individual drug codes that are classified as 'atypical antipsychotic drugs' in USP Classification System. They also have 5HT2C or H1 receptor inhibitory effects, which are defined by KEGG.

 Results: 79 Rows.

      $ ./apache-jena-3.0.0/bin/arq --data ./rdf/usp_201512.nq --data ./rdf/medis_201506.nq --data ./rdf/kegg_201512.nq --query ./queries/q2.rq

