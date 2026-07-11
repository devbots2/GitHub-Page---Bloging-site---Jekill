---
layout: post
title: "දත්ත ඉංජිනේරු විද්‍යාව යනු කුමක්ද? - What is Data Engineering?"
date: 2026-07-11 10:15:00 +0530
categories: [data, database]
tags: [data, databases, pipelines, theory, sinhala]
description: "Data Engineering යන්නෙහි මූලික සංකල්ප, ETL ක්‍රියාවලිය සහ මෙවලම් පිළිබඳව සරල සිංහල පැහැදිලි කිරීමක්."
image: "https://images.unsplash.com/photo-1551288049-bebda4e38f71?auto=format&fit=crop&w=600&q=80"
---

වර්තමාන ලෝකයේ දත්ත (Data) යනු අතිශය වටිනා වත්කමකි. නමුත් මේවා අමු දත්ත (Raw Data) ලෙස පවතින විට සෘජුවම ප්‍රයෝජනයට ගත නොහැක. මෙම දත්ත ක්‍රමවත් ලෙස එක්රැස් කර, පිරිසිදු කර, විශ්ලේෂණය සඳහා සූදානම් කිරීම **දත්ත ඉංජිනේරු විද්‍යාව (Data Engineering)** මඟින් සිදු කෙරේ.

## Data Engineer කෙනෙකුගේ කාර්යභාරය කුමක්ද?
දත්ත ඉංජිනේරුවරයෙකු විසින් දත්ත ගබඩා කිරීමේ පද්ධති (Storage), දත්ත ගලායන මාර්ග (Pipelines), සහ දත්ත සමුදායන් (Databases) සැලසුම් කිරීම සහ නඩත්තු කිරීම සිදු කරයි. ඔවුන් දත්ත විද්‍යාඥයින්ට (Data Scientists) සහ ව්‍යාපාර විශ්ලේෂකයින්ට (Business Analysts) නිවැරදි දත්ත ලබාදීමට අවශ්‍ය යටිතල පහසුකම් සපයයි.

## මූලික සංකල්ප: ETL ක්‍රියාවලිය (ETL Pipeline)
Data Engineering හි වැදගත්ම ක්‍රියාවලියක් වන්නේ **ETL** ය:
1.  **Extract (දත්ත ලබාගැනීම):** විවිධ මූලාශ්‍රවලින් (API, Databases, CSV files) අමු දත්ත ලබාගැනීම.
2.  **Transform (දත්ත වෙනස් කිරීම / පිරිසිදු කිරීම):** දත්තවල ඇති දෝෂ ඉවත් කර විශ්ලේෂණයට ගැලපෙන පරිදි හැඩගැස්වීම.
3.  **Load (දත්ත ඇතුළත් කිරීම):** පිරිසිදු කරන ලද දත්ත අවසාන ගබඩාව වන Data Warehouse එකකට ඇතුළත් කිරීම.

## බහුලව භාවිත වන මෙවලම් (Tools)
*   **භාෂා (Languages):** Python, SQL, Scala.
*   **විශාල දත්ත සැකසුම් (Big Data Engines):** Apache Spark, Hadoop.
*   **ක්‍රියාවලි මෙහෙයවීම් (Orchestration):** Apache Airflow.
*   **දත්ත ගබඩා (Data Warehouses):** Google BigQuery, Snowflake, Amazon Redshift.
