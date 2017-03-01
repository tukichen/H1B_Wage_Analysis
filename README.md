# H1B_Wage_Analysis
The new Trump administration has an huge impact on all aspects of life, including the H-1B reform. The High-Skilled Integrity and Fairness Act of 2017 proposed by Lofgren aims to eliminates H-1B jobs of lower pay and hope to bring these jobs to American workers.
While this and other immigration bills are controversial and not yet passed, they will sure change the job market to some extend, no matter you are an employer, foreign working applying for H-1B, or general American workers. Therefore, it would be interested to explore the current H-1B data and predict the impacts on industry and jobs if these H-1B reforms take place.

Here I explore the Labor Condition Application (LCA) disclosure data for foreign labor certification applications (H-1B visa petition) from 2009- 2016, which include Employer-specific case information such as job title, employer information, wage, and the prevailing wage for that level and location of job. 

### Analysis goals: 
I. Predict the potential impact of H-1B reform acts on H-1B jobs, and 
II.Explore time trends of H-1B wage change, by industry and job category, and identify which industries and job categories differ most in mean wages or time trend between H-1B workers and all American workers.

### Softwares used:   
Data management and cleaning  and exploratory analysis are done in python. 
Visualization, other summary analysis, clustering and longitudinal analysis will be performed using Shiny o f R to provide online access to users. 

### Data Description:
There are a total of 3,914,686 H1B petition from April 2009 to Oct 2016,  among which 2,656,343 cases were certified or certified but withdrawn (2,361,962 and 294,381, respectively).  
The top 5 states with most H-1B jobs certified were CA, NY, TX, NJ and IL (542, 288, 281, 213 and 150 thousands, respectively). 

According to Standard Occupational Classification (https://www.bls.gov/soc/) there are 23 major occupation groups, 97 minor occupation groups, and 461 broad groups.  


## I. Predict impacts of potential H-1B reform bills on H-1B jobs
Lofgren’s bill propose to prioritize market based allocation of visas to those companies willing to pay 200% of a wage calculated by survey, eliminate the category of lowest pay, and raise the salary level at which H-1B dependent employer are exempt from nondisplacement and recruitment attestation requirements to greater than $130,000.

1. Build an interactive Shiny app based on H-1B petition data from 2013-2016, to visualize how many certified H-1B jobs would have been denied, for one of the following conditions:

If the minimum salary for a H-1B dependent employer to hire an H-1B worker must be greater than x dollars (say $130,000), or
if the If the minimum salary to hire an H-1B worker must be greater than y% of the prevailing wage.

Users can select combinations of job categories, industries, companies,States (or metro areas like greater SF, NYC, Boston areas), and see summary statistics of H1B wage, number and % of H-1B workers approved in the past 3 years that would have been denied for conditions above. 
Users can also choose to list the top X job categories, industries, companies or States, to see summary information of H1B wage umber and % of H-1B workers affected.
	Plot bar charts of these top categories ,

Input any job title, search in H1B database for similar H-1B job titles, return the top X job categories, industries, companies or States which have most of these job titles, and display information in 2. 
Perform unsupervised learning such as hierarchical clustering to groups similar job categories, companies and industries in terms of total numbers and wages of H-1B workers.  Spatial clustering can be performed for geo locations.

After the system is set up, it would be easily modified to visualize impact of other upcoming H-1B reform actions.
*Data in the past 3 years are chosen because each H-1B authorization is valid for 3 years only.

## II. Explore change in H-1B wage over time, and identify which industries and job categories differ most in mean wages or time trend between H-1B workers and all American workers.

Merge the H-1B data from 2009 to 2016 with the Bureau of Labor Statistics' Occupational Employment Statistics survey data, to compare wages of H-1B worker sand all American workers over time, stratified by industry, job types and geo locations.

Build an interactive shiny app to do the following: 
Visualize Time trends of H-1B wage change, by job category, industry and/or geo location. Using loess curve to show mean H-1B wage and prevailing wage (with confidence bands) over time, with options to overlay a few job categories/ industries/ geo locations. Plot the mean prevailing wage with error bar over time for comparison.
Fit longitudinal mixed effects models to wage trend over time,  identify which job categories industries and differ most in (1) mean wages in 2016 or (2) time trend between H-1B workers and all American workers.
	For categories and industries identified with most differences, visualize changes using plots in (A).

H-1B jobs with much lower wages are at risk of elimination by new H-1B acts, while H-1B jobs with wage much higher than prevailing wage tend to be secured.   
We can see for which job categories, wage increase over time are much faster than overall wage increase of all jobs, suggesting a rapid growing area. For jobs which H-1B wages increase much faster (or slower) than prevailing wage of the same job type, further research can be performed to identify reasons. 
	
## Premilinary analysis:

Figure 1 includes 4 heat maps for the following information from 2009 - 2016: 
(a)  Median H-1B wage of 25 major occupation groups in the US by year; 
(b) The corresponding total H-1B jobs certified for 25 major occupation group ; 
(c) Median H-1B wage of minor occupation groups in Computer and Mathematics  of by year; 
(b) The corresponding total H-1B jobs certified for all Computer and Mathematics minor occupation groups.

Figure 1(a) suggests the 4 highest earning H-1B occupations are management, legal, healthcare practitioner and sales and related occupations. Figure 1(b) suggests the majority of H-1B workers have computer and mathematical occupations.
Further investigation into minor occupation groups of computer and mathematics in Figure 1(c) shows that computer and information research scientist and mathematicians are the highest paying H-1B jobs in this major group,  from Figure 1(d) most H-1B worker in this major group are software developers and programmers  or computer and information analysts.  

Figure 2 includes 4 heat maps for the following information from 2013 - 2016 to explore the impact of minimum H-1B wage requirement: 
(a)  Number of H-1B with wage < $100K in 25 major occupation groups; 
(b) The corresponding proportions with wage < $100K among H-1B jobs in those groups; 
(c) Number of H-1B with wage < $100K in Computer and Mathematics  of by year; 
(d) The corresponding proportions with wage < $100K among H-1B jobs in Computer and Mathematics minor occupation groups.

When we look at total H-1B job count with wage < $100K in Figure 2(a), not surprisingly we see Computer and Mathematics as the occupation affected most, because it is the largest H-1B job group in Figure 1(a) and wages are in the middle range (Figure 1(b)).  Similarly Figure 2(c) is consistent with Figure 1(c), showing the groups with most H-1B workers are also groups with most H-1B jobs below  < $100K wage threshold. Figures 2(b) and (d) show an opposite pattern of Figures 1(b) and 1(d), because the job groups with highest median wages are also the groups with fewer low wage H-1B workers and therefore not likely to e affected by the proposed H-1B Act. 

