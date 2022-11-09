---
layout: page
title: LNU-Phish
tagline: Data and Code
description: Download the LNU-Phish dataset and request access to our code.
---

Welcome to the website related to the paper "_Mitigating Adversarial Gray-box Attacks against Phishing Detectors_", accepted to IEEE Transactions on Dependable and Secure Computing (2022). 

This website contains all the resources we publicly release to the research community, as an additional contribution of our paper. Specifically, we provide:
* the **_LNU-Phish_ dataset**, containing over 20k websites (provided with their _URL_, _HTML_, _DNS record_, and _screenshot_) which we created and used for our evaluation; 
* our custom-built **feature extractor**, which we created to obtain the feature representation of each sample in LNU-Phish (and then used as basis for our analyses);
* our implementation of the **_Protective Operation Chains_** (POC) algorithm, which is proposed and evaluated in our paper. 

If you use any of such resources, we kindly ask you to cite our paper (a preprint is [here]({}/resources/tdsc22_paper.pdf)) with the following BibTeX entry:
```
  author={Apruzzese, Giovanni and Subrahmanian, V. S.},
  journal={IEEE Transactions on Dependable and Secure Computing}, 
  title={{Mitigating Adversarial Gray-Box Attacks Against Phishing Detectors}}, 
  year={2022},
  volume={},
  number={},
  pages={1-19},
  doi={10.1109/TDSC.2022.3210029},
  publisher={IEEE}}
```
---

Our Paper
---

aa


_LNU-Phish_ dataset
---

Our dataset, _LNU-Phish_ (short for "[Liechtenstein](https://www.uni.li/en) and [Northwestern](https://www.northwestern.edu/) University-Phishing"), contains information about benign and phishing websites, and can be used for a variety of purposes---including, but not limited to, the detection of phishing websites via machine learning (ML). Since _LNU-Phish_ contains samples taken "from the wild (web)", our dataset can be used both by researchers and practitioners alike.    

### Overview

The data in _LNU-Phish_ spans across a total of 23'364 websites: 7'861 are phishing websites, whereas 15'773 are legitimate websites. 

#### Creation
The _benign_ websites were taken by picking from the Alexa Top 1 Million list (as of March 2019 -- see [here]()). To create a balanced and diverse corpus containing both "well-known" websites as well as "less-known" (but still reputable) websites, we divided such list in three parts: the “top” partition includes websites from rank 1 to 10'000; the “middle” partition includes websites ranked from 10'001 to 100'000; the “bottom” partition includes all websites ranked below 100'001. We extract ∼5'000 websites from each partition. All such operations

The phishing websites were taken by crawling two well-known repositories of phishing websites: [PhishTank](https://phishtank.org/) and [OpenPhish](https://openphish.com/). Specifically, we developed a crawler that iteratively monitored such repositories, and promptly visited each new URL that was added to such lists. If the URL was valid, we then saved the URL, as well as the entire (raw) HTML _and_ a screenshot of the (rendered) landing webpage (we used [Dryscrape](https://dryscrape.readthedocs.io/en/latest/) for this). Moreover, we also used the URL to retrieve the DNS record of the webpage. Such operations were carried out between March and April 2019, and


### Formats

You can download the dataset at this link: [LNU-Phish](TBD)

Source Code
___


[Access link](TBD)