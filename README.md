#### Why are you designing the solution in this way?

I tried a few different approaches to this problem, but ended up settling on a combination of keyword heuristics and computer vision modeling. This allowed me to leverage signal from both the text and the image to get reasonable looking results.

The steps I went through, at a high level were:
- analyze some images and descriptions
- build a set of hand-labeled examples for each category
- use those examples to find high-precision descriptionn keywords for each category
- train and evaluate a computer vision model using images derived from those keywords
- combine the keyword-based rules with the image model and make minor tweaks

See the attached notebook for more detailed steps.

#### What are the aspects that you considered when designing?

- scalability (should work more data)
- clarity (tried not to pick overly complicated techniques)
- accuracy (results should look reasonable)
- time (what can I accomplish in a few hours)

#### What are the cases your solution covers, how are they covered and why are they important? What are the cases your solution does not cover and what are the ways you can extend your current solution for them?

For items where the keywords match (~50% of the time), the accuracy seems fairly high (perhaps 80%). So that's important in the sense that we're making correct predictions for a bunch of data. On the other hand, the model accuracy is much lower. Some classes in particular the model does poorly on- for example, it is overly prone to identify things as being jewelry. Also, the way I handled the "other" case wouldn't extend to datasets where there were a lot of other items that weren't just glasses. In general some extensions here might be:
- getting a more robust training and evaluation dataset,
- investigating the keywords further and going further into NLP analysis,
- understanding the product requirements and how that affects the labels and precision requirements
