
Croatian Language Dataset (CLD)
=======================================================

This is a dataset of sentences in Croatian language for anyone interested in Natural Language Processing.
The dataset is Spark's dataframe in a snappy compressed ORC format.
Most of the sentences are from the Croatian Wikipedia dump and OpenSubtitles project.
There are still entries that do not belong here, whether in a form of misspelled or grammatically incorrect sentences, logs, different languages, or weird tags.
However, those should be minimal.
The goal of this project was to create a reusable dataset with standardised use of Croatian language for various purposes.


### Size
#####14.7 million entries  
#####840 mb uncompressed size  
#####460 mb snappy compressed ORC  

### Use

```java
    val cld = spark
      .read
      .orc("src/main/resources/sentences.snappy.orc")
      .toDF()

    cld.printSchema()

    // Spark SQL usage
    cld.createOrReplaceTempView("cld")
    // filtering
    spark.sql("SELECT * FROM cld WHERE sentence LIKE '%Hannibal%'").show(30, false)
    // random
    spark.sql("SELECT *, rand() as random FROM cld order by random").drop("random").show(30, false)
```

<pre><code>
root
 |-- sentence: string (nullable = true)

+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|sentence                                                                                                                                                                      |
+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|Ali se hvata za slamčicu da je Hannibal učinio to.                                                                                                                            |
|505.	Velika pljačka vlaka; Hannibal.                                                                                                                                          |
|Dopuštaš Hannibalu da ga nabije na udicu.                                                                                                                                     |
|Da je Hannibal odgovoran.                                                                                                                                                     |
|Ako mislite da ćete uhvatiti Hannibala.                                                                                                                                       |
|Demme je izrazio svoju zainteresiranost oko filmske adaptacije knjige Hannibal 1998.                                                                                          |
|Hannibalov jedini zločin kojem sam svjedočila je navođenje.                                                                                                                   |
|Hannibal Lecture" prije nego što je počeo ići na terapiju - referenca na slavnog fiktivnog kanibala i jedan od prvih primjera pogrešnog korištenja ili iskrivljivanja pojmova.|
|Imam tekst iz Hannibala.                                                                                                                                                      |
|Hannibal mora večeras zaprositi Vanessu.                                                                                                                                      |
|Ja sam Hannibalov prijatelj.                                                                                                                                                  |
|Hannibal Lecter?                                                                                                                                                              |
|Hannibal DVD "Prilog o snimanju filma"                                                                                                                                        |
|Je li tvoja supruga svjesna koliko prisno ti i Hannibal poznajete jedan drugoga?                                                                                              |
|Hannibalovo imanje.                                                                                                                                                           |
|Kadet Hannibal Lee.                                                                                                                                                           |
|Kako poznaješ Hannibala?                                                                                                                                                      |
|Htio je biti Hannibal Dunstable.                                                                                                                                              |
|Izgleda poput hobi-sobe Hannibala Lectera.                                                                                                                                    |
|Hannibal ima određeni stil osobnosti od kojeg svi možemo učiti.                                                                                                               |
|Hannibal je pobjegao.                                                                                                                                                         |
|Hannibal gubi i ono malo pameti što je imao.                                                                                                                                  |
|Hannibal da.                                                                                                                                                                  |
|Kad jaganjci nastavku filma Hannibala Lectera.                                                                                                                                |
|Kritike za film Hannibal bile su pomiješane.                                                                                                                                  |
|Magazin Empire dao je filmu dvije od četiri zvjezdice i nazvao ga "...smiješnim i izuzetno dosadnim - Hannibal je gotovo bez zuba do pred kraj filma.                         |
|Nećeš pronaći Hannibala ovdje.                                                                                                                                                |
|lmam obavijest o Hannibalu Lecteru.                                                                                                                                           |
|Pomogla sam Masonu pronaći Hannibala.                                                                                                                                         |
|Ono od Hannibala Lectera je pravo?                                                                                                                                            |
+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
only showing top 30 rows
</code></pre>

### Created With

* [Spark 2.4](https://spark.apache.org/releases/spark-release-2-4-0.html) 
* [Postgres 10.6](https://www.postgresql.org/docs/10/release-10-6.html)
* [wget 1.19.4](https://www.gnu.org/software/wget/)
* [sed 4.4](https://www.gnu.org/software/sed/manual/sed.html)
* [jsoup 1.8.3](https://jsoup.org/)

### Results

