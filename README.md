# Digital Validation in Research

### The Science of Repeatability


## Motivation

The challenge of reproducing the computation involved in a research finding was first described in the early 1990s[^claerbout-1992] when distribution of source code and data was in its infancy. Since then, dissemination has become easier, but validating complex computer programs and verifying their agreement with a paper has become more difficult.

In some ways, the complexity of code, and amount of computing power used, has made it more likely that a finding is only discernable by asking a computer. So the modern computer has begun to resemble any other instrument: The findings themselves depend on it. A bug may convince both researchers and readers of something that's not real, in other words.

This phenomenon has occurred even with a simple computation with high stakes, in the case of the economics paper "Growth in a Time of Debt" in which an Excel error invalidated the conclusions and had implications for austerity policies around the world[^herndon-2014]. More recently, a bug was found in a paper on psychedelic drugs that was subsequently retracted[^herzog-2022]. It's difficult to know how common this is, but the idea that many computations are not practically possible without the use of a computer is trivially true.

It's for this reason that digital reproducibility can be understood as part of a spectrum[^peng-2011]. This emphasizes the fact that a reproduction could be impeded immediately without data or complete methods, or further along after investing in rerunning an experiment, and creates a hierarchy with generalizability at the top. And it ensures that no impediment is left out. Because replication is a philosophical principle, and a physical process, any factor that prevents replication is, effectively, similar.

Digital replication is also important to the working scientist because publishing and funding norms are changing. Many already require data and code sharing and signs suggest the trend is going upwards. Funders such as NIH[^nih-2022] and NSF[^nsf-2022] have emphasized reproducibility, and data sharing. Recent work suggests statistical analysis plans may be necessary on top of preregistration, whenever possible[^gelman-2019]. The Journal of the American Statistical Association now has eight[^jasa-2022] reproducibility editors who "enforce the requirement that the data and code that support the claims in an article are made available."[^baker-2016] Replication research in 2021 continues to find problems in with analytical, and direct replication[^errington-2021].

## The Spectrum of Verifiability

This quality that communicates results is not necessarily traditional code quality. Even the most indecipherable, but working, code is better than nothing[^barnes-2010]. The essential quality is whether or not the code runs and produces the results from the paper. This challenge goes by many names, and papers-with-code lie on a spectrum starting from nothing, no code or data, to complete digital replication, and, if the code is evidence for the conclusion, on up through scientific generalizability.

At its core, re-running code on another machine is a problem of determinism. Digital reproducibility, or the ability for outside researchers to regenerate results and the lower bar of _repeatability_[^ioannidis-2008] the ability to run the code regardless of conclusions are about starting conditions that entirely determine, through a predictable process, the result. There may be multiple pathways (or _execution paths_) that a program can take with different input, but those can be thought of as one in a set of deterministic processes subject to the same rules.

Repeatability hinges on control of starting conditions, called "state," and an execution environment, the hardware and software, which is deterministic. If a set of initial conditions lead to identical execution on other machines, the result is repeatable.

Digital repeatability is no different from an experiment. If the methodology has been described well, and the results valid, simply producing the same result is an achievement, and an achievement at the heart of science.


The level of verifiability of a paper-with-code-repository lies on a spectrum that, approximately, starts with repeatability. Initiatives like [CODECHECK](https://codecheck.org.uk/) have very similar, but purposefully lower, bar the can still be difficult to achieve: "check[ing that] the code runs and generates the expected number of output files."[^eglen-2019] This could be called "Runnability."

And all levels rest on the very lowest level, "completeness,"  meaning _enough_ information has been provided, whether or not that information is correct, compatible with a computer system, or leads to a valid conclusion. Completeness, or "preproducibility"[^stark-2018] is essential, and is common barrier even among open science publications[^wicherts-2006]. It's estimated that only about 9% of papers include publication of "full primary raw data"[^alsheikh-ali-2011], and the availability of data decreases rapidly with age[^vines-2014]. Despite this, there are dangers to withholding materials, and apparent benefits for those who share. Withholding materials decreases, as one would expect, replication[^baker-2-2016], and sharing it is associated with a higher citation rate[^piwowar-2013].

_Verification on a Spectrum_

The range of verifiability that starts with completeness is, roughly, ordered with less complete agreement with the original study at one end of a spectrum and complete agreement at the other. Whether or not a particular computational verification should be on the spectrum with real science depends on how it supports its paper, and if there was any other way of knowing the results other than consulting a computer.

There is undoubtedly a range in these variables as well. In some cases, the code may be producing summary statistics that could be checked manually by scanning down a small table of values. In other cases, sophisticated statistical methods are used, stochastic processes, large amounts of data, and many lines of code. Even in small calculations like the averages of debt and GDP in countries can be mistaken[^herndon-2014], and a bug may invalidate -- and has invalidated[^herzog-2022] -- findings entirely.

Philosophically, considering the computer a scientific instrument puts it in the same category as any other measurement tool that may be right or wrong. Verification, or falsifiability, being out of reach for any such piece of equipment is equivalent from that standpoint, and, rhetorically speaking, a paper with unverifiable claims for any reason has the same problem. It's also been suggested that lack of lower level materials are a sign of problems at higher ones[^wicherts-2011].

Whether or not, or how often a computer is the device giving results without anything (algebraic proof, manual computation etc) to verify it, is an open question. The effort to verify even a short piece of code, or produce a small stochastic process, through other means would generally be immense. And formal verification of software and hardware is incredibly rare with only a few applications such as compilers ever achieving the distinction[^acm-award].


* _Digital Runnability_: Analysis runs to completion and output superficially supports that it ran as intended.
* _Digital Repeatability_: Analysis generates results, which are comparable, but may differ from the published result.
* _Digital Reproducibility_: Analysis runs and output is the same as the published result.
* _Digital Reimplementation_: Analysis runs after being rewritten without common libraries and code that could perpetuate errors in the original. Analogous to Scientific Generalizability.
* _Scientific Conceptual Replicability_: Different methods confirm the published result.
* _Scientific Reproducibility_: Same methodology on the same statistical population confirm the published result. Also known as direct, or exact replication.
* _Scientific Replicability_: Same methodology with a different statistical population confirm the published result.
* _Scientific Generalizability_: Different analysis on a different statistical population confirms the published result.

Note: The definition that goes with the word for some of these terms varies by discipline[^nas-2019].

There is some debate in the literature about whether conceptual replication deserves to be higher[^crandall-2016] or lower[^chambers-2019] than exact replication. There's debate about the value of exact replication since, for instance, populations change over time[^stroebe-2014]. And whether irreproducibility is a problem[^osc-2015] or unavoidable[^firestein-2016]. However, all of these authors agree irreproducibility is _some kind of error_, whether necessary, forgivable, or regrettable. Karl Popper's opinion, that science and reproduction are inextricably linked, is deferred to throughout:

"Indeed the scientifically significant physical effect may be defined as that which can be regularly reproduced by anyone who carries out the appropriate experiment in the way prescribed."[^popper-1959]


### Variables that affect digital repeatability

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
* Input (in the computational sense, meaning study data, and all parameters)

Control, or accounting for, every one of these variables is difficult other than in [containerized](#containers) environments, but they all do vary, and change over time.

In practical terms, only a few of these account for the majority of preventable repeatability problems:

* Operating system
* Source code version. (The contents of the source code that is being run.)
* Programming language version
* Library versions
* Standalone software
* Input

Configuration is also a potent variable but, in general, no configuration should be used that isn't explicitly included in a repository for reproduction, whereas it is usually _necessary_ to use libraries, for instance.

Configuration usually affects execution because it's accidentally included, not because it's a natural part of publishing code. Configuration, almost by definition, will not be identical on another machine. _No published software should depend on personal settings, or unknown environment variables._

Another important note is that availability of these resources may change over time. In general, versions of programming languages, libraries, and applications are identical (one copy of Python 3.6 is identical to another) and remain available in perpetuity with rare exceptions. Data at a particular URL, however, may change in place, or become unavailable.

Unversioned libraries, or resources downloaded from the most recent commit of the main branch of a repository instead of a versioned release is expected to change radically over time. As a general rule, all resources should be pinned to a particular versioned release that will continue to be available, and identical, in the future.

The solution to controlling all of these variables on readers' machines and achieving repeatability is conceptually straightforward:

1. Testing variation that _can't be controlled_ such as operating system. Testing the code on several operating systems and accounting for the difference, either with notes, or changes to the code that make it run similarly on the other systems.
2. Specifying, or controlling variation that _can be controlled_, such as language and library versions, data versions et cetera. Library, language, and standalone application developers will naturally try to make their work run identically on all supported operating systems, so versions is the only variable left for the author to control. Specifying versions, preferably through a build file and lock file that will control them exactly for dependencies, and dependencies-of-dependencies will prevent many problems. At the very least, these versions should be listed in the documentation.


## References

[^claerbout-1992]: Claerbout, Jon F., and Martin Karrenbach. "Electronic Documents Give Reproducible Research a New Meaning." SEG Technical Program Expanded Abstracts 1992, Society of Exploration Geophysicists, Jan. 1992, https://doi.org/10.1190/1.1822162.

[^baker-2016]: Baker, M. Why scientists must share their research code. Nature (2016). https://doi.org/10.1038/nature.2016.20504

[^errington-2021]: Timothy M Errington, Maya Mathur, Courtney K Soderberg, Alexandria Denis, Nicole Perfito, Elizabeth Iorns, Brian A Nosek (2021) Investigating the replicability of preclinical cancer biology eLife 10:e71601. https://doi.org/10.7554/eLife.71601

[^barnes-2010]: Barnes, N. Publish your computer code: it is good enough. Nature 467, 753 (2010). https://doi.org/10.1038/467753a

[^ioannidis-2008]: Ioannidis JP, Allison DB, Ball CA, Coulibaly I, Cui X, Culhane AC, Falchi M, Furlanello C, Game L, Jurman G, Mangion J, Mehta T, Nitzberg M, Page GP, Petretto E, van Noort V. Repeatability of published microarray gene expression analyses. Nat Genet. 2009 Feb;41(2):149-55. doi: 10.1038/ng.295. Epub 2008 Jan 28. PMID: 19174838.

[^eglen-2019]: Eglen, S., & Nüst, D. (2019). CODECHECK: An open-science initiative to facilitate the sharing of computer programs and results presented in scientific publications. Septentrio Conference Series, (1). https://doi.org/10.7557/5.4910

[^stark-2018]: Stark PB. Before reproducibility must come preproducibility. Nature. 2018 May;557(7707):613. doi: 10.1038/d41586-018-05256-0. PMID: 29795524.

[^wicherts-2006]: Wicherts, Jelte & Borsboom, Denny & Kats, Judith & Molenaar, Dylan. (2006). The poor availability of psychological research data for reanalysis. The American psychologist. 61. 726-8. 10.1037/0003-066X.61.7.726.

[^alsheikh-ali-2011]: Alsheikh-Ali, Alawi A et al. “Public availability of published research data in high-impact journals.” PloS one vol. 6,9 (2011): e24357. doi:10.1371/journal.pone.0024357

[^vines-2014]: Vines, Timothy H et al. “The availability of research data declines rapidly with article age.” Current biology : CB vol. 24,1 (2014): 94-97. doi:10.1016/j.cub.2013.11.014

[^baker-2-2016]: Baker, M. 1,500 scientists lift the lid on reproducibility. Nature 533, 452–454 (2016). https://doi.org/10.1038/533452a

[^piwowar-2013]: Piwowar HA, Vision TJ. Data reuse and the open data citation advantage. PeerJ. 2013 Oct 1;1:e175. doi: 10.7717/peerj.175. PMID: 24109559; PMCID: PMC3792178.

[^herndon-2014]: Herndon, Thomas, et al. “Does High Public Debt Consistently Stifle Economic Growth? A Critique of Reinhart and Rogoff.” Cambridge Journal of Economics, vol. 38, no. 2, 2014, pp. 257–79. JSTOR, http://www.jstor.org/stable/24694929.

[^herzog-2022]: Herzog, R., Mediano, P.A.M., Rosas, F.E. et al. Retraction Note: A mechanistic model of the neural entropy increase elicited by psychedelic drugs. Sci Rep 12, 15500 (2022). https://doi.org/10.1038/s41598-022-20093-y

[^peng-2011]: Peng, Roger D. "Reproducible Research in Computational Science." Science, vol. 334, no. 6060, American Association for the Advancement of Science (AAAS), Dec. 2011, pp. 1226–27. https://doi.org/10.1126/science.1213847.

[^jasa-2022]: "Journal of the American Statistical Association." Taylor & Francis, https://www.tandfonline.com/action/journalInformation?show=editorialBoard&journalCode=uasa20.

[^gelman-2019]: Gelman, Andrew and E. Loken. "The garden of forking paths : Why multiple comparisons can be a problem , even when there is no 'fishing expedition' or 'p-hacking' and the research hypothesis was posited ahead of time." (2019).

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

[^chambers-2019]: Chambers, C., The Seven Deadly Sins of Psychology: A Manifesto for Reforming the Culture of Scientific Practice (Princeton University Press, 2019) pp. 25-27, 64-73

[^stroebe-2014]: Stroebe W, Strack F. The Alleged Crisis and the Illusion of Exact Replication. Perspect Psychol Sci. 2014 Jan;9(1):59-71. doi: 10.1177/1745691613514450. PMID: 26173241.

[^osc-2015]: Open Science Collaboration. PSYCHOLOGY. Estimating the reproducibility of psychological science. Science. 2015 Aug 28;349(6251):aac4716. doi: 10.1126/science.aac4716. PMID: 26315443.

[^firestein-2016]: Firestein, S., Failure: Why Science is So Successful (Oxford University Press, 2016)

[^acm-award]: Software System Award Goes to Three for Pioneering Open Source Initiatives. awards.acm.org/software-system. Accessed 26 Sept. 2022.

[^popper-1959]: K. R. Popper, The Logic of Scientific Discovery (Basic Books, Inc., 1959).
