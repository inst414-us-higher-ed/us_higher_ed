Written by Diamond Andy, Lily Gates, Mia Leandri, and Colin Thompsom  
University of Maryland, Spring 2025

# Project Overview

## Description
Exploring the differences between American research colleges and universities through data visualization.

## Research Question/Topic
1. Descriptive and Comparative Question

**How do different tiered American research colleges and universities compare in terms of location, admissions, academic offerings, doctoral degrees awarded, and other institutional characteristics?**

2. Analytical and Inferential Question

**How do other institutional characteristics, besides financial expenditures, predict or correlate with research designation tiers among American colleges and universities?**

# Data and Research Sources
Cleaned CSV versions of the "Carnegie Classification of Institutions of Higher Education"
https://carnegieclassifications.acenet.edu/


1. `carnegie_classification_stats`

Original data from: https://carnegieclassifications.acenet.edu/institutions/?inst=&basic2021__bc%5B%5D=21

Variables:
* School information
    * Contains columns that seperates schools by flagship name and seperate campuses
        - e.g., University of Maryland, College Park has the "core name" University of Maryland and the "specific name" College Park
* Public or private (non-profit, for-profit)
* Description of types of degree programs offered
* Enrollment information
* Research classification from 2025

2. `carnegie_spending_doctorate_awards`

Original data from: https://carnegieclassifications.acenet.edu/carnegie-classification/research-designations/

Variables:
* School information
* Research classification from 2021 and 2025
* Expenses (2021, 2022, 2023)
* Research Doctorates Awarded (2020, 2021, 2022)

## Description of Variables
* `classification_df` is from the `carnegie_classification_stats`
* `spending_df` is from the `carnegie_spending_doctorate_awards`

**Basic School Information**

NAME
- `unitid` - unique ID number
- `name.x` - name of school
    - orig from `classification_df`
    - NOTE: is later renamed to `name` while `name.y` is dropped
- `name.y` - name
    - orig from `spending_df`
- `core_name` - name of the main university (e.g., "University of Maryland")
    - orig from the `classification_df`
- `spec_name` - name of the specific campus/satellite (e.g., "College Park")
    - orig from the `classification_df`

SCHOOL TYPE 
- `public_private_profit` - public, private (for-profit, non-profit)
    - orig from `classification_df`

SCHOOL LOCATION
- `city` - city
- `state` - state abbreviation
- `size_setting` - size, 4-year vs. graduate/professional, how residential the school is
    - orig from `classification_df`

**Enrollment and Admissions**
- `level` - four or more years as opposed to associate degree 2-year programs such as community colleges
    - orig from `classification_df`
- `enrollment_profile` -  distribution of undergrad vs. graduate students
    - orig from `classification_df`
- `size_setting` - student body population 
    - orig from `classification_df`
      - *size*:
        - very small (less than 999)
        - small (1000 to 2999)
        - medium (3000 to 9999)
        - large (10000 or greater)
      - *residential*: percentage of living on-campus students
        - primarily non-res: less than 25% FT students
        - primarily residential: 25 to 50% FT students
        - highly residential: more than 50% FT students
- `undergrad_profile` - for 4-year universities
    - orig from `classification_df`
        - *full/part-time*:
            - higher part-time (over 40% PT)
            - medium-full-time (21-39% PT)
            - full-time (less than 20% PT)
      - *selective*:
        - inclusive (ACT equivalent <19)
        - more selective (ACT equivalent 19 to 23)
        - selective (ACT equivalent over 23)
      - *transfer in*:
        - lower (<20%)
        - higher (greater than 20%)


**Research Classification Ranking**
- `research_tier_2025` - 2025 tier ranking 
    - orig from `classification_df`
- `classific_2021` - 2021 tier ranking
    - orig from `spending_df`
- `classific_2025` - 2025 tier ranking
    - orig from `spending_df`

**Finances**  
orig from `spending_df`
- `herd_fy21` - 2021 fiscal year expenses on research
- `herd_fy22` - 2022 fiscal year expenses on research
- `herd_fy23` - 2023 fiscal year expenses on research
- `herd_avg_fy21_to_fy23` - Average expenses on research from 2021 to 2023


**Types of Academic Programs and Degrees Offered**  
orig from `classficiation_df`
- `degree_focuses` - degree level and academic focus overview
    - *top degree level offered*: bacc, masters, doctoral, special, tribal
    - *focus*: arts and science, diverse, engineering and tech, medical, other health, special focus, research, or NULL
    - *size*: of program (only for Masters Universities)
    - *research activity*: only for Doctoral Universities
- `undergrad_program` - distribution of undergrad degrees in certain academic fields
    - *dominant subj*:
"arts and sciences" OR "professions" OR NULL
    - *balanced vs plus vs focus*:
measured by the percentage of bachelor's degrees awarded in arts and sciences (rather than professions)
    - *graduate degree coexistence*:
percentage of graduate degrees in undergraduate fields
        - e.g., a BS in Computer Science AND a MS or PHD in Computer Science is also offered at the same school
        - measured by "none" (0%) OR "some" (0 to 50%) or "high" (greater than 50%)
- `grad_program` - distribution of grad degrees in certain academic fields
    - *program level*: undergrad only, postbac, research doctorate, NULL
    - *single or comprehensive*: multiple subject fields or single subject
    - *focus*: education, business, humanities, STEM, professional
      
**Research Doctorates Awarded**  
orig from  `spending_df`

Number of doctoral research degrees conferred for...
- `num_doc_degrees_2020_2021` - the 2020-2021 school year
- `num_doc_degrees_2021_2022` - the 2021-2022 school year
- `num_doc_degrees_2022_2023` - the 2022-2023 school year

**Miscellaneous**  
orig from `classification_df`  
Not important, used for Carnegie's specific engagement and purposes, special program with Carnegie
- `community_engage` - whether they were classified by Carnegie
- `leadership_for_public_prax` - whether they were classified by Carnegie

# Usage and Notes

## Required Dependencies
- tidyverse
- readr
- tidyr
- dplyr
- lubridate
- stringr

## Future Steps
TBD
