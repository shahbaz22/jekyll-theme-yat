---
layout: post
title: Topic modeling with LLMs
subtitle: Use case for large surveys/consultations
excerpt_image: assets/images/clustering.png
tags: [topic modeling, LLMs]
top: 1
sidebar: []
---

### Introduction 

Public consultations are a cornerstone of policymaking, providing a platform for stakeholders to voice their opinions on critical issues. However, when these consultations include free-text fields, the sheer volume of responses can overwhelm even the most seasoned analysts. Government agencies routinely process hundreds of consultations annually, often requiring significant time and resources to extract actionable insights.

This is where AI, specifically topic modelling frameworks like BERTopic combined with large language models (LLMs), can drastically improve the process.

### The Challenge
For consultations with around 100,000 free-text responses across multiple questions, traditional analysis methods struggle to keep pace. Analysts often spend months manually categorising responses, costing taxpayers millions. For example, analysing a single consultation with this volume of responses has been known to take a team of around 30 analysts and consultants three months, costing approximately £400,000.

These challenges demand scalable, automated solutions that can efficiently identify key themes while retaining the nuanced understanding required for informed policymaking.

### The Solution: AI-Powered Consultation Analysis
By combining BERTopic, a robust topic modelling framework, with LLMs like GPT, it's possible to streamline the analysis process while preserving interpretability and accuracy. This approach transforms free-text responses into actionable insights and summary reports, significantly reducing the time and resources needed.

<p style="text-align: center;">
<img src="{{ site.baseurl }}/assets/images/bertopic.png" alt="Crepe">
  <figcaption style="text-align: center;"> Figure showing all the modular sub-models as part of Bertopic.</figcaption>

</p>


## **How It Works**

### **1. Embedding**
The cleaned text is transformed into high-dimensional **embeddings** using advanced models such as **SentenceTransformers** from the hugging face library of models. These embeddings capture the relationships between textual elements, enabling more nuanced understanding.

### **2 .Clustering**
The embeddings are clustered using algorithms like **HDBSCAN**, which groups similar responses together. This clustering process creates **distinct themes** that reflect the underlying structure of the data.

BERTopic’s modular nature allowed for the customisation of both the embedding and clustering stages, making it adaptable to the specific needs of the consultation analysis.

### **3. Data Cleaning**
Before topic modeling begins, it is critical to clean the raw textual data to ensure high-quality results. Using **BERTopic’s Vectorizer and Tokenizer**, responses were preprocessed to remove noise such as:

- Non-alphanumeric characters  
- Excessive white spaces  
- Common stop words such as: a, an, the

Initially, an embedding model was used to generate dense numerical embeddings that capture the text's semantic meaning. The **Tokenizer** and **Vectorizer** further refine this data by cleaning and transforming for topic modeling. These preprocessing steps collectively ensured accurate and coherent results.

### **4. Topic Extraction and Representation**
Once clusters are formed, BERTopic identifies the **most representative keywords** for each cluster. These keywords act as **labels for the themes**, offering interpretable insights into the dominant topics within the data.

This step ensures that policymakers can easily identify the key areas of interest in the consultation.

### **5. Summarisation with Large Language Models**
To provide concise summaries for each topic:

1. **Representative documents** from each cluster/topic are selected. In this example these docs are survey responses.   
2. These **representative responses** and **keywords** for each topic are combined into a **prompt**, then fed into a large language model which returns a JSON summary for each topic
3. The JSON topic summaries are then compiled into a **PDF report**.

This stage ensures that policymakers receive **actionable insights** directly derived from the raw data, packaged in an **easy-to-understand format**.

### **6. Deployment on Vertex AI and Google Colab Enterprise**
The entire pipeline was implemented and scaled using **Vertex AI**, a Google Cloud platform designed for deploying machine learning workflows. **Google Colab Enterprise** was used for experimentation and rapid prototyping, leveraging its powerful compute resources and seamless integration with Vertex AI.

This setup allowed for efficient handling of the large BBC public consultation dataset with over 100,000 free-text responses, ensuring **reliability, scalability, and cost-effectiveness** throughout the process.


<p style="text-align: center;">
<img src="{{ site.baseurl }}/assets/images/flow_chart_bert.webp" alt="Crepe">
  <figcaption style="text-align: center;"> Workflow for Survey Data Analysis and Report Generation. At each stage different sub-models have been used for example UMAP and HDBSAN where sub-model parameters have been chosen to maximise the number of cluster while minimising noise. This is because we are also interested in unpopular opinions (small cluster/topics) in the analysis of our surveys.</figcaption>

</p>



### Application Example: BBC Public Consultation
In a recent project, this AI-driven approach was applied to analyse the BBC’s ## **Application Example: BBC Public Consultation**

The consultation featured over **100,000 free-text responses** across eight questions. Using the **Consultation Analyser**:

- **Analysis time** is expected to be reduced from three months to **a few weeks**.  
- **Costs** are expected to be significantly lowered, cutting the typical **£400,000 expense** by a substantial margin to less than **£10,000**  
- **Policymakers** will receive detailed thematic reports generated directly from the raw data.  

## **Benefits of the Consultation Analyser**

- **Efficiency**: Automates the analysis of large datasets, reducing the need for extensive manual effort.  
- **Scalability**: Handles hundreds of thousands of responses across multiple fields effortlessly.  
- **Interpretability**: Offers clear visualisations and summaries, aiding policymakers in understanding public sentiment.  
- **Cost-Effectiveness**: Minimises the resources required, enabling governments to reallocate budgets to other critical areas.  
- **Cloud-Native**: By leveraging Vertex AI and Colab Enterprise, the solution scales seamlessly to meet computational demands.  

### Conclusion
AI-powered tools like the Consultation Analyser are transforming how governments and organisations handle public consultations. By leveraging frameworks like BERTopic, LLMs, and cloud-based platforms like Vertex AI, these tools can analyse vast amounts of free-text responses quickly, cost-effectively, and with high interpretability.

As governments seek to make data-driven decisions efficiently, integrating AI into public consultation analysis will become more common.

<!-- You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

## section 1

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

## section 2

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]: https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/

$ a \* b = c ^ b $

$ 2^{\frac{n-1}{3}} $

$ \int_a^b f(x)\,dx. $

```cpp
#include <iostream>
using namespace std;

int main() {
  cout << "Hello World!";
  return 0;
}
// prints 'Hi, Tom' to STDOUT.
```

```python
class Person:
  def __init__(self, name, age):
    self.name = name
    self.age = age

p1 = Person("John", 36)

print(p1.name)
print(p1.age)
``` -->
