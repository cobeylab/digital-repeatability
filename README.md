# Digital Validation in Research

### The Science of Repeatability

_Alex Byrnes, Christopher Russo, Marcos Vieira_

## Introduction

Repeatability, in science and computation, is conceptually very simple. Make conditions the same, as exactly as necessary, and the process will repeat. Drop an apple and it will fall. There are, of course, details that can be omitted. Knowing which details are indispensable is essential to ensuring repeatability.

## Motivation

"An article about computational science in a scientific publication is not the scholarship itself, it is merely advertising of the scholarship. The actual scholarship is the complete software development environment and the complete set of instructions which generated the figures." &mdash; Jonathan Buckheit and David Donoho (1995), paraphrasing Jon Claerbout[^nas-2017]

The challenge of reproducing the computation involved in a research finding was first described in the early 1990s[^claerbout-1992] when distribution of source code and data &mdash; on CD ROMs &mdash; was in its infancy. Since then, dissemination has become easier, but validating complex computer programs and verifying their agreement with a paper has become more difficult.


The complexity of code, and amount of computing power used, has made it more likely that a finding is only discernable by asking a computer. For all but the simplest analyses, checking computational results by hand is no more feasible than checking by naked eye observations made under a microscope. So the modern computer has begun to resemble any other instrument in that the findings themselves depend on it. A bug may convince both researchers and readers of something that's not real, in other words.

The phenomenon &mdash; results that depend on a bug &mdash; has occurred even with a simple computation with high stakes, in the case of the economics paper "Growth in a Time of Debt" in which an Excel error invalidated the conclusions and had implications for austerity policies around the world[^herndon-2014]. In 2006, five papers were retracted due to software that transposed two columns of crystallography data[^miller-2006]. More recently, a bug was found in a paper on psychedelic drugs that was subsequently retracted[^herzog-2022].  Libraries, and other dependencies, are also not immune to bugs, even ones in the scientific literature. In 2019, over 100 organic chemistry papers may have been affected by a Python script that didn't behave identically on different operating systems[^bhandari-2019]. It's difficult to know how common bug-dependent results are, but the idea that many computations are not practically possible without the use of a computer is trivially true: even short, routine computations require billions of operations that would be nearly impossible to confirm any other way.

It's for these reasons that digital reproducibility can be understood as part of a spectrum[^peng-2011] that includes concerns about actual conclusions. Visualizing verification this way also ensures that nothing suggestive of an error is left out, from mundane lack of data, to lack of methods, to methodological errors. It's also possible that lack of "lower level" reproducibility materials is a sign of problems at higher ones[^wicherts-2011].

_Incentives_

Digital replication is also important to the working scientist because publishing and funding incentives are changing. Many publishers and funders already require data and code sharing, and signs suggest the trend is increasing. Funders such as NIH[^nih-2022] and NSF[^nsf-2022] have emphasized reproducibility and data sharing. The Journal of the American Statistical Association now has eight[^jasa-2022] reproducibility editors who "enforce the requirement that the data and code that support the claims in an article are made available."[^baker-2016] Funders and publishers who follow recent results in metascience[^osc-2015] may tend to require more guarantees. Replication research in 2021 continues to find problems in with analytical, and scientific replication[^errington-2021].

It's estimated that only about 9% of papers include publication of "full primary raw data"[^alsheikh-ali-2011], and the availability of data decreases rapidly with age[^vines-2014]. Despite this, there are dangers to withholding materials, and apparent benefits for those who share. Withholding materials decreases, as one would expect, replication[^baker-2-2016], and sharing it is associated with a higher citation rate[^piwowar-2013].


## The Spectrum of Verifiability

The lowest level of verifiability rests on "completeness,"  meaning _enough_ information has been provided, whether or not that information is correct, compatible with a computer system, or leads to a valid conclusion. Completeness, or "preproducibility"[^stark-2018] is essential, and is common barrier even among open science publications[^wicherts-2006].

Assuming enough information has been provided to test any claims, the spectrum starts with the ability to mechanically execute the steps provided, regardless of outcome. Initiatives like [CODECHECK](https://codecheck.org.uk/) have a purposefully low bar: "check[ing that] the code runs and generates the expected number of output files."[^eglen-2019] This could be called "Runnability."

There is one discontinuity in the spectrum where results are not expected to be statistically the same (drawn from the same theoretical distribution, or the same population). Concepts like _conceptual replication_ don't fit neatly into a spectrum since the amount of confirmation is subject to interpretation. _Scientific generalizability, and replicability_ are among the highest goals of science, and may depend on support all the way down to data sharing, but defining them in terms of _what has been precisely repeated_ is beyond the current scope.


#### Table 1. The Reproducibility Spectrum

* _Digital Runnability_: Analysis runs to completion and output superficially supports that it ran as intended. The right number of files is produced, the files are of the right kind, have the right column names, etc.
* _Digital Repeatability_: Analysis generates results, which are comparable, but may differ from the published result. The values in the output make sense (they're numbers when they should be numbers, plots when they should be plots, etc.) but the precise values may differ from those in the paper.
* _Digital Reproducibility_: Analysis runs and output is the same as the published result.
* _Digital Reimplementation_: Analysis runs after being rewritten without common libraries and code that could perpetuate errors in the original.
* _Scientific Reproducibility_: Same methodology on the same statistical population confirms the published result. Also known as direct, or exact replication.

#### Table 2. The Generalizability Spectrum

* _Scientific Replicability_: Same methodology with a different statistical population confirms the published result.
* _Scientific Generalizability_: Different analysis on a different statistical population confirms the published result.

Note: The definition that goes with the word for some of these terms varies by discipline[^nas-2019].

There is some debate in the literature about whether conceptual replication deserves to be higher[^crandall-2016] or lower[^chambers-2019] than exact replication. There's debate about the value of exact replication since, for instance, populations change over time[^stroebe-2014]. And whether irreproducibility is a problem[^osc-2015] or unavoidable[^firestein-2016]. However, all of these authors agree irreproducibility is _some kind of error_, whether necessary, forgivable, or regrettable. There is little disagreement on the status of reproduction as necessary to consider something a fact, and possibly is the only way to define them. From "The Logic of Scientific Discovery:"

"Indeed the scientifically significant physical effect may be defined as that which can be regularly reproduced by anyone who carries out the appropriate experiment in the way prescribed."[^popper-1959]


### Variables that affect digital repeatability

Repeatability hinges on control of starting conditions (data and software), and the execution environment (hardware). The logic every computer uses is assumed to be universal and deterministic. So the challenge is to control factors that may cause one computer to use a different set of instructions from another. This can really only be done through inaccuracy or omission. Assuming everything published in a repository is accurate and all data and software have been provided, the problem simplifies further to deciding what to include and what to omit about the original execution environment.

Some details can be reliably omitted. For instance, the brand of _PC_, a term that's synonymous with having a processor with the x86 architecture, can be omitted. Every brand of PC can be assumed to run equivalently given the same machine code, which is assumed to be identical to any other set of instructions produce from the same source code. Variations do exist, but substantial effects on the result are rare.

Some details cannot be reliably omitted such as the version of the language and libraries that were used. Large differences exist among versions of languages and libraries. This can, most often, lead to an analysis that doesn't run at all. In some cases, the analysis will run but give a different output.

It's also important to remember that the conditions are always future conditions. If some of the input, or software, changes because it depends on a resource on the internet that may change over time, the likelihood of achieving repeatability drops significantly[^vines-2014].


#### Table 2. Sources of Variation

**Hardware**

* Resources such as amount of hard drive space or memory.
* CPU Architecture
* Network connectivity
* GPU Architecture

**Software**

* Operating System and version
* Source code version
* Programming language version
* Compiler or interpreter (often determined by the language version, but not always)
* Library versions
* System libraries
* Standalone software versions (BLAST, MAFFT, OpenCV)
* Configuration including [environment variables](https://en.wikipedia.org/wiki/Environment_variable) and user preferences.
* Input (in the computational sense, meaning study data, all parameters and configuration)


In practical terms, only a few of the possible sources of variation account for the majority of preventable repeatability problems:

* Operating system and version
* Source code version
* Programming language version
* Library versions
* Standalone software version
* Input

Since the problem reduces to omission, it is sufficient to describe of these variables in detail. Luckily, it is standard to publish any of these resources such that they can be described bit-for-bit using only their version number. This means that any copy of Python 3.2 is identical to any other now and in the future (redownloading Python 3.2 has no effect). Analysis code should follow the same rule in that once a release is done as version 1.2, any changes to it necessitates a new release with a new, higher version, say 1.3.

It is also customary to consider changes to more significant digits in the version number as a higher kind of change[^semver-2022]. For analyses that are only expected to have a few versions, simply doing releases and versions at all goes a long way.

Unversioned libraries, or resources downloaded from the most recent commit of the main branch of a repository instead of a versioned release are expected to change radically over time. As a general rule, all resources should be pinned to a particular versioned release that will continue to be available, and identical, in the future.

Input such as study data can be versioned and frozen, and given a DOI for the same reasons.


#### Other input

Once, the execution environment has been described with version numbers and the data has been provided, there's little else that can generally differ from the original environment. However, there are two other categories that deserve special attention: configuration, and parameters. The solution to controlling them on other machines will be familiar.

_Configuration_

Configuration refers to parameters to an application or analysis that are outside of the main scientific questions involved such as parameters that are infrequently changed, or personal preferences. As a general rule, any configuration that affects the running or output of an analysis should be used unless it is provided in the published repository.

Configuration usually affects execution because it's accidentally included, not because it's a natural part of publishing code. Configuration, almost by definition, will not be identical on another machine.


_Parameters_

Parameters are input to an application like data but generally control _how_ the data is processed. Computationally, however, they are the same as any other input to an application. Parameters can vary widely and affect the runnability, and eventual output and conclusions so they should be specified precisely. If the range of possible parameters is large, a representative set of parameters, and the expected output will enhance runnability.

Techniques for this include unit tests, which are sets of input/output pairs that are known to be correct, and runbooks, which can be developed into a "run file," a simple executable file that runs the analysis with default parameters.


#### Method

The method for controlling all of these variables on readers' machines and achieving repeatability is therefore straightforward:

1. Test sources of variation that _can't be controlled_ such as operating system. Testing the code on several operating systems and accounting for the difference, either with notes, or changes to the code that make it run similarly on the other systems.

2. Specify variation that _can be controlled_, such as language and library versions, data versions et cetera. Library, language, and standalone application developers will naturally try to make their work run identically on all supported operating systems. Specifying versions, preferably through a build file, lock file, or requirements file that will control them exactly for dependencies will prevent many problems. At the very least, these versions should be listed in the documentation.


### Summary

The conditions necessary for scientific and those necessary for digital verification are analogous. Due to the unique status of the modern computer, and the complexity of ordinary computations, scientific and digital verifications are also _intertwined_. It's often the case that computers act as scientific instruments on which real conclusions rest. It is important, therefore, to provide all necessary materials, and specify precise methodology for rerunning an analysis. Erring on the side of _over_ explaining is justifiable, but it suffices to provide exact descriptions of a few key variables (language version, library versions et cetera) and to publish code with a versioned release that doesn't change without re-releasing with a new version number. Additionally, there are a small number of possible sources of variability in total. Knowing all of them and testing, or accounting for them will ensure digital repeatability.



## References


[^nas-2017]: National Academies of Sciences, Engineering, and Medicine; Policy and Global Affairs; Committee on Science, Engineering, Medicine, and Public Policy; Committee on Responsible Science. Fostering Integrity in Research. Washington (DC): National Academies Press (US); 2017 Apr 11. 9, Identifying and Promoting Best Practices for Research Integrity. Available from: https://www.ncbi.nlm.nih.gov/books/NBK475944/

[^claerbout-1992]: Claerbout, Jon F., and Martin Karrenbach. "Electronic Documents Give Reproducible Research a New Meaning." SEG Technical Program Expanded Abstracts 1992, Society of Exploration Geophysicists, Jan. 1992, https://doi.org/10.1190/1.1822162.

[^baker-2016]: Baker, M. Why scientists must share their research code. Nature (2016). https://doi.org/10.1038/nature.2016.20504

[^errington-2021]: Timothy M Errington, Maya Mathur, Courtney K Soderberg, Alexandria Denis, Nicole Perfito, Elizabeth Iorns, Brian A Nosek (2021) Investigating the replicability of preclinical cancer biology eLife 10:e71601. https://doi.org/10.7554/eLife.71601

[^eglen-2019]: Eglen, S., & Nüst, D. (2019). CODECHECK: An open-science initiative to facilitate the sharing of computer programs and results presented in scientific publications. Septentrio Conference Series, (1). https://doi.org/10.7557/5.4910

[^stark-2018]: Stark PB. Before reproducibility must come preproducibility. Nature. 2018 May;557(7707):613. doi: 10.1038/d41586-018-05256-0. PMID: 29795524.

[^wicherts-2006]: Wicherts, Jelte M., et al. "The Poor Availability of Psychological Research Data for Reanalysis." American Psychologist, vol. 61, no. 7, American Psychological Association (APA), 2006, pp. 726–28. https://doi.org/10.1037/0003-066x.61.7.726.

[^alsheikh-ali-2011]: Alsheikh-Ali, Alawi A., et al. “Public Availability of Published Research Data in High-Impact Journals.” PLoS ONE, edited by Isabelle Boutron, vol. 6, no. 9, Public Library of Science (PLoS), Sept. 2011, p. e24357. https://doi.org/10.1371/journal.pone.0024357.


[^vines-2014]: Vines, Timothy H et al. “The availability of research data declines rapidly with article age.” Current biology: CB vol. 24,1 (2014): 94-97. doi:10.1016/j.cub.2013.11.014

[^baker-2-2016]: Baker, M. 1,500 scientists lift the lid on reproducibility. Nature 533, 452–454 (2016). https://doi.org/10.1038/533452a

[^piwowar-2013]: Piwowar HA, Vision TJ. Data reuse and the open data citation advantage. PeerJ. 2013 Oct 1;1:e175. doi: 10.7717/peerj.175. PMID: 24109559; PMCID: PMC3792178.

[^herndon-2014]: Herndon, Thomas, et al. “Does High Public Debt Consistently Stifle Economic Growth? A Critique of Reinhart and Rogoff.” Cambridge Journal of Economics, vol. 38, no. 2, 2014, pp. 257–79. JSTOR, http://www.jstor.org/stable/24694929.

[^miller-2006]: Miller, G. (2006). A Scientist’s Nightmare: Software Problem Leads to Five Retractions. Science, 314(5807), 1856–1857. https://doi.org/10.1126/science.314.5807.1856

[^bhandari-2019]: Bhandari Neupane, J., Neupane, R. P., Luo, Y., Yoshida, W. Y., Sun, R., & Williams, P. G. (2019). Characterization of Leptazolines A–D, Polar Oxazolines from the Cyanobacterium Leptolyngbya sp., Reveals a Glitch with the “Willoughby–Hoye” Scripts for Calculating NMR Chemical Shifts. Organic Letters, 21(20), 8449–8453. https://doi.org/10.1021/acs.orglett.9b03216

[^herzog-2022]: Herzog, R., Mediano, P.A.M., Rosas, F.E. et al. Retraction Note: A mechanistic model of the neural entropy increase elicited by psychedelic drugs. Sci Rep 12, 15500 (2022). https://doi.org/10.1038/s41598-022-20093-y

[^peng-2011]: Peng, Roger D. "Reproducible Research in Computational Science." Science, vol. 334, no. 6060, American Association for the Advancement of Science (AAAS), Dec. 2011, pp. 1226–27. https://doi.org/10.1126/science.1213847.

[^jasa-2022]: "Journal of the American Statistical Association." Taylor & Francis, https://www.tandfonline.com/action/journalInformation?show=editorialBoard&journalCode=uasa20.

[^nih-2022]: "Data Management & Sharing Policy Overview | Data Sharing." National Institutes of Health, https://sharing.nih.gov/data-management-and-sharing-policy/about-data-management-and-sharing-policies/data-management-and-sharing-policy-overview

[^nsf-2022]: "Dear Colleague Letter: Reproducibility and Replicability in Science (nsf23018) | NSF - National Science Foundation." National Science Foundation, https://www.nsf.gov/pubs/2023/nsf23018/nsf23018.jsp

[^wicherts-2011]: Wicherts, Jelte M., et al. “Willingness to Share Research Data Is Related to the Strength of the Evidence and the Quality of Reporting of Statistical Results.” PLoS ONE, edited by Rochelle E. Tractenberg, vol. 6, no. 11, Public Library of Science (PLoS), Nov. 2011, p. e26828. https://doi.org/10.1371/journal.pone.0026828.

[^nas-2019]: National Academies of Sciences, Engineering, and Medicine; Policy and Global Affairs; Committee on Science, Engineering, Medicine, and Public Policy; Board on Research Data and Information; Division on Engineering and Physical Sciences; Committee on Applied and Theoretical Statistics; Board on Mathematical Sciences and Analytics; Division on Earth and Life Studies; Nuclear and Radiation Studies Board; Division of Behavioral and Social Sciences and Education; Committee on National Statistics; Board on Behavioral, Cognitive, and Sensory Sciences; Committee on Reproducibility and Replicability in Science. Reproducibility and Replicability in Science. Washington (DC): National Academies Press (US); 2019 May 7. 3, Understanding Reproducibility and Replicability. Available from: https://www.ncbi.nlm.nih.gov/books/NBK547546/

[^crandall-2016]: Christian S. Crandall, Jeffrey W. Sherman,
On the scientific superiority of conceptual replications for scientific progress,
Journal of Experimental Social Psychology,
Volume 66,
2016,
Pages 93-99,
ISSN 0022-1031,
https://doi.org/10.1016/j.jesp.2015.10.002.
(https://www.sciencedirect.com/science/article/pii/S0022103115300020)

[^chambers-2019]: Chambers, Chris. The Seven Deadly Sins of Psychology: A Manifesto for Reforming the Culture of Scientific Practice. Princeton University Press, 2017. JSTOR, https://doi.org/10.2307/j.ctvc7742b.

[^stroebe-2014]: Stroebe W, Strack F. The Alleged Crisis and the Illusion of Exact Replication. Perspect Psychol Sci. 2014 Jan;9(1):59-71. doi: 10.1177/1745691613514450. PMID: 26173241.

[^osc-2015]: Open Science Collaboration. PSYCHOLOGY. Estimating the reproducibility of psychological science. Science. 2015 Aug 28;349(6251):aac4716. doi: 10.1126/science.aac4716. PMID: 26315443.

[^firestein-2016]: Firestein, Stuart, Failure: Why Science is So Successful. Oxford University Press, 2016

[^popper-1959]: K. R. Popper, The Logic of Scientific Discovery (Basic Books, Inc., 1959).

[^semver-2022]: Preston-Werner, Tom. "Semantic Versioning 2.0.0." Semantic Versioning, semver.org.
