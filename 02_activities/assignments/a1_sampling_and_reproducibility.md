# ASSIGNMENT: Sampling and Reproducibility in Python

Read the blog post [Contact tracing can give a biased sample of COVID-19 cases](https://andrewwhitby.com/2020/11/24/contact-tracing-biased/) by Andrew Whitby to understand the context and motivation behind the simulation model we will be examining.

Examine the code in `whitby_covid_tracing.py`. Identify all stages at which sampling is occurring in the model. Describe in words the sampling procedure, referencing the functions used, sample size, sampling frame, any underlying distributions involved, and how these relate to the procedure outlined in the blog post.

Run the Python script file called whitby_covid_tracing.py as is and compare the results to the graphs in the original blog post. Does this code appear to reproduce the graphs from the original blog post?

Modify the number of repetitions in the simulation to 100 (from the original 1000). Run the script multiple times and observe the outputted graphs. Comment on the reproducibility of the results.

Alter the code so that it is reproducible. Describe the changes you made to the code and how they affected the reproducibility of the script file. The output does not need to match Whitby’s original blogpost/graphs, it just needs to produce the same output when run multiple times

# Author: Vikram Katju

```

Sampling occurs at two stages in this simulation. In the first stage, the sampling helps inform which individuals attending weddings or brunches get infected initially. The np.random.choice() function is used for the sampling in this stage. A dataframe comprising of 800 people attending  brunches and 200
 
people attending weddings is first created as per the blog post. 10 percent of these 1000 individuals are then randomly chosen to be infected by the simulation. This implies that the sample size in this first stage of sampling is approximately 100 (we expect to see minor deviations from 100 since a 

randomization function is being used here). Since all 1000 members of this community have attended either a brunch or a wedding, as per the blog post,  the sampling frame comprises all 1000 individuals in the community. Note that the np.random.choice() function, when used with the replace = False flag 

(sampling without replacement), which is used to randomly infect 10 percent of the 1000 individuals in the community, uses the binomial distribution. Here, this implies that each member of the community independently has a 10 percent chance of being infected. 

In the second stage the sampling determines which of the infected individuals are traced successfully. This stage of the sampling uses the np.random.rand function. The sampling frame at this stage of sampling comprises all the infected members in the community. The np.random.rand distribution uses the 

uniform distribution to decide whether each infected individual is successfully traced based on the 'trace success' probability of 0.20.


After running the whitby_covid_tracing.py file and comparing the obtained graphs to the graphs in the original blog posts one observes that the graphs are not the same. Specifically, while the distribution of the 'infections from weddings' variable appears to be approximately the same there is a significant 

difference in the distribution of the 'Traced to weddings' (observed proportion of infections traced to weddings) variable. 

Every time we run the script the obtained graphs are approximately the same with minor variations. This is because the graphs being obtained use randomly sampled data from the total dataset. To make the obtained graphs reproducable the random seed function (np.random.seed) should be used 

appropriately just before sampling as has been done in the submitted .ipynb file (whitby_covid_tracing_100.ipynb). Using the random.seed function ensures that the same data will be sampled every time the script is run thereby ensuring that the graphs being produced by the script will be identical every time.

(Please note that the file with my corrections is called whitby_covid_tracing_100.ipynb.)


```


## Criteria

|Criteria|Complete|Incomplete|
|--------|----|----|
|Altercation of the code|The code changes made, made it reproducible.|The code is still not reproducible.|
|Description of changes|The author explained the reasonings for the changes made well.|The author did not explain the reasonings for the changes made well.|

## Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `23:59 - 16/02/2025`
* The branch name for your repo should be: `assignment-1`
* What to submit for this assignment:
    * This markdown file (a1_sampling_and_reproducibility.md) should be populated.
    * The `whitby_covid_tracing.py` should be changed.
* What the pull request link should look like for this assignment: `https://github.com/<your_github_username>/sampling/pull/<pr_id>`
    * Open a private window in your browser. Copy and paste the link to your pull request into the address bar. Make sure you can see your pull request properly. This helps the technical facilitator and learning support staff review your submission easily.

Checklist:
- [ ] Create a branch called `assignment-1`.
- [ ] Ensure that the repository is public.
- [ ] Review [the PR description guidelines](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md#guidelines-for-pull-request-descriptions) and adhere to them.
- [ ] Verify that the link is accessible in a private browser window.

If you encounter any difficulties or have questions, please don't hesitate to reach out to our team via the help channel in Slack. Our Technical Facilitators and Learning Support staff are here to help you navigate any challenges.
