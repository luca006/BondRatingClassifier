For what purpose was the dataset created? 

The data-set is commercially available from a leading bond index provider. The data set is created in order for asset management firms and related to have a consistent, high quality and accessible data-set of individual corporate bonds that are representative of the investible universe. 

The data-set and calculations thereof have a methodology which you can find here https://www.ice.com/publicdocs/data/Bond_Index_Methodologies.pdf


- Who created the dataset (e.g., which team, research group) and on behalf of which entity (e.g., company, institution, organization)? Who funded the creation of the dataset?

ICE is a leading index/financial securities/benchmarking data provider, it is a private for-profit corporation and among the few leaders in providing reliable, consistent and actionable corporate bond data. 

 
## Composition

- What do the instances that comprise the dataset represent (e.g., documents, photos, people, countries)?
The instances are individual corporate bonds.
Each bond has a unique set of descriptive, categorical and quantitative characteristics.
  
- How many instances of each type are there?
The whole (raw) data set counts 11,692 instances.

- Is there any missing data?
Yes, missing data reflects several specific challenges and characteristics of the corporate bond universe:
1) New bond issues will not have a full data set (for example it will not have historical performance numbers/figures as they have been recently issued)
2) Not all bonds have the same characteristics (for example some may be callable, some may have no put date etc...)

For example, Yield to Next Call has a large amount of NaNs 1,933 compared to 7,105 (after processing); this is rather due to the fact that Yield to Next Call is quite a technical field. This field is removed. 

- Does the dataset contain data that might be considered confidential (e.g., data that is protected by legal privilege or by    doctor–patient confidentiality, data that includes the content of individuals’ non-public communications)?
  
No the dataset is not confidendtial as this aggregates publicly available bond characteristics. In addition, as these are financial securities there is no concern about privacy or related confidentiality issues.

## Collection process

- How was the data acquired?
NR
- If the data is a sample of a larger subset, what was the sampling strategy?
The dataset is the full sample.
- Over what time frame was the data collected?
Single cross-section (daily i.e. one-day)

## Preprocessing/cleaning/labelling

- Was any preprocessing/cleaning/labeling of the data done (e.g., discretization or bucketing, tokenization, part-of-speech tagging, SIFT feature extraction, removal of instances, processing of missing values)? If so, please provide a description. If not, you may skip the remaining questions in this section.

1) Remove any bonds that are not labelled as "SENR" (field Type) as this better reflects the relationship of ratings and corproate bonds. The data-set is more clean and consistent.
2) Remove Yield to Next call as this has a large NaNs and is not meaningfully important compared to all other fields
3) Re-label Ratings variables for ease of using the data/code
4) Processing we remove any ID's, Issuer related names as this can increase the likelihood of overfitting as there are multipl bonds within the same corporation
- Was the “raw” data saved in addition to the preprocessed/cleaned/labeled data (e.g., to support unanticipated future uses)?
Raw data is saved in the repository
 
## Uses

- What other tasks could the dataset be used for?
Portfolio construction, protfolio optimization, clustering analysis, risk analysis, scenario analysis and much more...

- Is there anything about the composition of the dataset or the way it was collected and preprocessed/cleaned/labeled that might impact future uses? For example, is there anything that a dataset consumer might need to know to avoid uses that could result in unfair treatment of individuals or groups (e.g., stereotyping, quality of service issues) or other risks or harms (e.g., legal risks, financial harms)? If so, please provide a description. Is there anything a dataset consumer could do to mitigate these risks or harms?
Not that we are aware of.

- Are there tasks for which the dataset should not be used? If so, please provide a description.
Recommend to avoid using the data as a source of prices or trading as these do not correctly reflect best-execution prices.

## Distribution

- How has the dataset already been distributed?
  NR
- Is it subject to any copyright or other intellectual property (IP) license, and/or under applicable terms of use (ToU)?
  NR

## Maintenance

- Who maintains the dataset?
  NR

