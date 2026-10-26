[README.md](https://github.com/user-attachments/files/33990229/README.md)
# Diagnosing Underpowered Studies and P-Hacking

## Objective

I examined how small samples, multiple testing and the choice of statistic can lead to misleading conclusions about a job training program.

## Methodology

- Calculated the pilot study’s power using the known population effect and determined the sample size needed for 80% power.
- Reran the study with the required sample size.
- Applied Benjamini-Hochberg correction to the subgroup tests.
- Simulated repeated testing when every null hypothesis was true.
- Wrote my own Benjamini-Hochberg function and checked it against statsmodels.
- Compared Welch’s test, Yuen’s trimmed test and permutation tests of ordinary and trimmed means on heavy-tailed earnings data.

## Key Findings

The pilot had only **10.9% power** with **15 people per group**. Reaching 80% power required **222 people per group**; the larger study detected an effect with **p = 0.0012**. The pilot’s non-significant result did not establish that the program was ineffective.

After Benjamini-Hochberg correction, **0 of 20 subgroups** remained significant. Across **1,000 replications**, **65.8%** produced at least one false positive, close to the theoretical **64.2%**. My own correction function matched statsmodels and flagged **2 subgroups** when two effects were planted.

On heavy-tailed earnings data, Welch’s test (**p = 0.2650**) and the ordinary-mean permutation test (**p = 0.3496**) were non-significant. Yuen’s test (**p = 0.0066**) and the trimmed-mean permutation test (**p = 0.0056**) were significant. The results split by the statistic tested: trimming reduced the influence of extreme earners while changing the target from the overall mean to the trimmed mean.
