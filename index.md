---
layout: page
title: LNU-Phish
tagline: Data and Code
description: Download the LNU-Phish dataset and request access to our code.
---

Welcome to the website related to the paper "[Mitigating Adversarial Gray-box Attacks against Phishing Detectors](https://ieeexplore.ieee.org/document/9904297)", accepted to IEEE Transactions on Dependable and Secure Computing (Sept. 2022). 

This website contains all the resources we publicly release to the research community, as an additional contribution of our paper. Specifically, we provide:
* the **_LNU-Phish_ dataset**, containing over 20k websites (provided with their _URL_, _HTML_, _DNS record_, and _screenshot_) which we created and used for our evaluation; 
* our custom-built **feature extractor**, which we created to obtain the feature representation of each sample in _LNU-Phish_ (and then used as basis for our analyses);
* our implementation of the **_Protective Operation Chains_** (POC) algorithm, which is proposed and evaluated in our paper. 

If you use any of such resources, we kindly ask you to cite our work with the following BibTeX entry:
```
  @article{apruzzese2022mitigating,
  author={Apruzzese, Giovanni and Subrahmanian, V. S.},
  journal={IEEE Transactions on Dependable and Secure Computing}, 
  title={Mitigating Adversarial Gray-Box Attacks Against Phishing Detectors}, 
  year={2022},
  volume={},
  number={},
  pages={1-19},
  doi={10.1109/TDSC.2022.3210029},
  publisher={IEEE}}
```
---

## Paper

Our paper (a preprint is [here](resources/tdsc22_paper.pdf)) tackles the problem of adversarial attacks against Phishing Detectors (PD) relying on Machine Learning (ML).
At a high-level, we make 3 contributions:
* We carry out a **large evaluation** of "Gray-Box" adversarial attacks against ML-based PD. 
  * We consider 4 dataset, 13 classifiers, and 10 different families of Gray-Box attack in which we vary the portion of the features used by the PD known by the attacker.
* We propose a **new defensive mechanism**, the _Protective Operation Chains (POC)_ algorithm. 
  * We show that PD using POC are more robust that the baselines against our attacks, and show that POC does not degrade baseline performance while (potentially) confusing the attacker.
* We create a **new dataset** for phishing website detection, _LNU-Phish_.
  * Our dataset overcomes the problems of most existing datasets for PD, i.e., it provides the _full information_ of each sample (the raw HTML, URL, DNS records, screenshot, as well as its feature representation -- few datasets provide all of these) collected _at the time_ of creating the dataset (phishing websites get taken down quickly, and it is not possible to collect such samples later).

We publicly release our dataset, our implementation of POC (together with an example of its application), and our feature extractor.


#### Abstract
 Although machine learning based algorithms have been extensively used for detecting phishing websites, there has been relatively little work on how adversaries may attack such “phishing detectors” (PDs for short). In this paper, we propose a set of Gray-Box attacks on PDs that an adversary may use which vary depending on the knowledge that he has about the PD. We show that these attacks severely degrade the effectiveness of several existing PDs. We then propose the concept of operation chains that iteratively map an original set of features to a new set of features and develop the Protective Operation Chain (POC for short) algorithm. POC leverages the combination of random feature selection and feature mappings in order to increase the attacker’s uncertainty about the target PD. Using 3 existing publicly available datasets plus a fourth that we have created and will release upon the publication of this paper, we show that POC is more robust to these attacks than past competing work, while preserving predictive performance when no adversarial attacks are present. Moreover, POC is robust to attacks on 13 different classifiers, not just one. These results are shown to be statistically significant at the _p_ < 0.001 level.

___


## Our _LNU-Phish_ dataset


Our dataset, _LNU-Phish_ (short for "[Liechtenstein](https://www.uni.li/en) and [Northwestern](https://www.northwestern.edu/) University-Phishing"), contains information about benign and phishing websites, and can be used for a variety of purposes---including, but not limited to, the detection of phishing websites via machine learning (ML). Since _LNU-Phish_ contains samples taken "from the wild (web)", our dataset can be used both by researchers and practitioners alike.    

### Overview

The data in _LNU-Phish_ spans across a total of 23'364 websites: 7'861 are phishing websites, whereas 15'773 are legitimate websites. 

#### Samples and Information

Each sample in _LNU-Phish_ is a website, which can be either benign or malicious. Regardless of its nature, each sample in _LNU-Phish_ is provided with the following information:
* its **URL** (which typically corresponds to the "homepage" of the website)
* the (raw) **HTML** of the landing webpage of the URL
* the **screenshot** showing the rendered webpage
* the **DNS records**, such as _whois_ info, _SSL_ certificate, and _pagerank_.

#### Creation and Lists
We follow a standardized procedure to create _LNU-Phish_. 
We developed a **data-collection script** that visited each URL in a given list. If the URL was valid, we then created a new "sample", thereby saving the URL, as well as the entire (raw) HTML _and_ a screenshot of the (rendered) landing webpage (we used [Dryscrape](https://dryscrape.readthedocs.io/en/latest/) for this). Moreover, we also used the URL to retrieve the DNS record of the webpage.


The **benign** websites were taken by picking from the Alexa Top 1 Million list (as of March 2019). To create a balanced and diverse corpus containing both "well-known" websites as well as "less-known" (but still reputable) websites, we divided such list in three parts: the “top” partition includes websites from rank 1 to 10'000; the “middle” partition includes websites ranked from 10'001 to 100'000; the “bottom” partition includes all websites ranked below 100'001. We extract a ~5000 URLs from each partition, and used them as input to our data-collection script. Ultimately, _LNU-Phish_ contains 5'354, 3'824, and 6'595 samples from the "bottom", "medium", and "top" partitions, respectively. 

The **phishing** websites were taken by crawling two well-known repositories of phishing websites: [PhishTank](https://phishtank.org/) and [OpenPhish](https://openphish.com/). Specifically, we devised a crawler that iteratively monitored such repositories for several days between March and April 2019. At the end of each "crawled day", we used the collected URLs as input to our data-collection script. Ultimately, _LNU-Phish_ contains 5'399 websites from PhishTank and 2'462 websites from OpenPhish (all distinct).

Upon completing all such operations, we created a **feature extractor** based on the guidelines provided in the [UCI Phishing Website dataset](https://archive.ics.uci.edu/ml/datasets/phishing+websites) (originally proposed in the works by Mohammad et al. [[1](https://ieeexplore.ieee.org/abstract/document/6470857), [2](https://link.springer.com/article/10.1007/s00521-013-1490-z), [3](https://ietresearch.onlinelibrary.wiley.com/doi/full/10.1049/iet-ifs.2013.0202)] and still used even recently, e.g., [[Jain 2018](https://link.springer.com/article/10.1007/s11235-017-0414-0), [Sharma 2020](https://ieeexplore.ieee.org/abstract/document/9198349), [Hannousse 2021](https://www.sciencedirect.com/science/article/pii/S0952197621001950)]). We release our feature extractor as an additional contribution of our paper.

### Formats

We provide our _LNU-Phish_ dataset in 3(+1) diverse formats:

* **Feature-only (1.5MB)**. This format contains _only the features_ generated via our custom feature extractor. It is the "ML-ready" format of our dataset.
  * Access: [Link](resources/LNU-Phish_features.zip) [[SHA256](resources/LNU-Phish_Features-SHA256)]
* **No-screenshots (550MB).** This format contains all information for each sample (i.e., the raw URL, HTML and DNS information, as well as the feature representation) aside from the screenshots. It is useful to generate new features, or craft adversarial perturbations in the [problem space](https://ieeexplore.ieee.org/abstract/document/9152781) (as done, e.g., in [SpacePhish](https://spacephish.github.io/)).
  * Access: [Link (OneDrive)](https://1drv.ms/u/s!AiRbxLvsK4bMojXskQc3HktxlAX7?e=eezuf7) [[SHA256](resources/LNU-Phish_noScreenshots-SHA256)]
* **Full (34GB)**. This format contains _everything_, including the screenshot. It is the most complete format of _LNU-Phish_, but also the largest one.
  * Access: via explicit request (see bottom of the page for instructions)
* **Full-snippet (50MB).** This format contains a subset of 100 samples (60 benign and 40 phishing) taken from the "Full" format of _LNU-Phish_ (this snippet was provided to the referees of TDSC during the peer-review process of our paper). It is meant to allow researchers to understand the data included in the Full versions of _LNU-Phish_.
  * Access: [Link](resources/LNU-Phish_snippet.zip) [[SHA256](resources/LNU-Phish_snippet-SHA256)]

(all archives are protected with a password: "dsail", without quotes and lowercase)

___

## Source Code (and Access)

Alongside our dataset, we also disclose our source-code to implement _POC_, together with a notebook containing an example of its application to harden a ML-based classifier on our _LNU-Phish_ dataset. We also provide the code of our feature extractor (which still works today), alongside a notebook showcasing its application the "snippet" version of _LNU-Phish_.

All such resources are included in a private GitHub repository. We will provide (read) access to such repository to any interested researcher or enthusiasts.

### Access

To obtain access to our resources, you can either:
* send an **email** to [Giovanni Apruzzese](mailto:giovanni.apruzzese@uni.li) (be sure to put the term "LNU-Phish" in the subject of the email!);
* contact [Giovanni Apruzzese](https://giovanniapruzzese.com) in **any other means** (useful if, e.g., your mail is blocked);
* fill out the **form** available at the following link: [Google Form](https://forms.gle/3XgGJtThDAohjbmQ8)

In any case, please **include your affiliation** when requesting access to our resources.