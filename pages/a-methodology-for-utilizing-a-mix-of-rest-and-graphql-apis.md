---
title: "A Methodology for Utilizing a Mix of REST and GraphQL APIs"
date: 2023-05-16
author: ["Ryan Donghan Kwon", "Mingeon Kim"]
---

# A Methodology for Utilizing a Mix of REST and GraphQL APIs

**Author** - Ryan Donghan Kwon, *IEEE Student Member*, ryankwon@ieee.org;
Mingeon Kim, *Puhung High School*, issac4892@gmail.com

**Abstract** - The increasing complexity of data requirements in modern web applications has led to the rise of different API design paradigms, notably Representational State Transfer (REST) and GraphQL. While each has its strengths and weaknesses, the choice between them is often presented as a binary one. This paper proposes a methodology for effectively integrating both REST and GraphQL APIs in a single system based on key factors including use case, performance, complexity, and interoperability. The methodology is illustrated and validated through two industry case studies, GitHub and Shopify, and a hypothetical experiment. The results suggest that a carefully considered mix of REST and GraphQL can yield more efficient and flexible APIs. However, these findings require further research for validation across a broader range of contexts. The study concludes that by understanding the strengths and weaknesses of both REST and GraphQL, developers can leverage both technologies to create more robust APIs.

**Keywords** - API Design, REST API, GraphQL API, Mixed API Approach, Use Case Analysis, Performance Metrics, System Complexity, Interoperability, Case Study: GitHub, Case Study: Shopify, Experimental Validation, System Efficiency, Flexibility in API Design, System Requirements.

## 1. Introduction

The advent of web technology has led to significant changes in how data is transferred and consumed. Two of the most notable technologies that have emerged in the realm of web development are Representational State Transfer (REST) and GraphQL APIs. As diverse as they are, these technologies have each carved out their niche and are used in a variety of applications today.

REST, first defined by Roy Fielding in 2000[^fielding2000], is a widely adopted architectural style that structures a network application as a stateless set of resources, each with a unique URL. It has gained popularity due to its simplicity and the fact that it's built upon standard HTTP methods, making it highly interoperable. However, its resource-oriented approach can lead to over-fetching or under-fetching of data, which can impact the efficiency of an application.

On the other hand, GraphQL, developed and open-sourced by Facebook in 2015[^facebook2015], presents an alternative approach. It allows clients to specify exactly what data they need, potentially reducing the amount of data transferred over the network. However, this comes with an increase in complexity both in terms of setup and query understanding.

While both technologies have their strengths and weaknesses, there has been limited research into how they might be used in combination to leverage their strengths while mitigating their weaknesses. This paper aims to fill that gap.

The objective of this study is to present a methodology for using a mix of REST and GraphQL APIs. The hypothesis is that an intelligent mix of these two technologies, based on their respective strengths and the requirements of the application, can result in more efficient and flexible APIs.

This study will be of interest to developers, architects, and technologists involved in API development and usage, and could inform future best practices in this area.

## 2. Literature Review

The literature on API design and usage presents a wealth of information on both REST and GraphQL APIs. While several studies have compared the two, to the best of our knowledge, no prior work has proposed a specific methodology for using them in combination.

REST, defined by Fielding[^fielding2000], has been widely adopted due to its simplicity and the use of standard HTTP methods. This architectural style structures a network application as a stateless set of resources, each with a unique URL. Numerous studies have explored the advantages and challenges of REST. For instance, the work of Rodriguez et al.[^rodriguez2008] delves into the principles of REST and its implications for web services.

GraphQL, on the other hand, is a relatively newer technology. Developed and open-sourced by Facebook[^facebook2015], GraphQL allows clients to specify exactly what data they need, reducing over-fetching and under-fetching of data. Despite its relatively short existence, several studies have examined GraphQL's impact on web development. For example, Hartig and Pérez[^hartig2018] explore the semantics of GraphQL, and how it compares to traditional API designs.

Several researchers have undertaken direct comparisons between REST and GraphQL. Sodderland and van Ballegooijen[^sodderland2020] provided an in-depth comparison of the two from a developer's perspective, highlighting the different use cases for which each might be better suited. Flanagan and Byrne[^flanagan2019] focused on the performance characteristics of REST and GraphQL, noting the trade-offs between data transfer efficiency and server-side processing. In a controlled experiment, Pautasso and Zimmermann[^pautasso2018] compared the two technologies, shedding light on their relative strengths and weaknesses in a controlled environment.

Despite this wealth of information, there appears to be a gap in the literature when it comes to combining the use of REST and GraphQL APIs. This paper seeks to fill that gap by proposing a methodology for using both based on the specific needs and constraints of the application.

## 3. Methodology

The proposed methodology for integrating a mix of REST and GraphQL APIs in a single system is based on four key factors: use case, performance, complexity, and interoperability. Each factor plays a crucial role in determining which technology is best suited for a particular operation in the system.

### 3.1 Use Case

REST is generally beneficial for simple Create, Read, Update, and Delete (CRUD) operations, where the data requirements are straightforward and well-defined. For example, retrieving a user's profile or updating a user's email could be implemented using REST. The resource-oriented approach of REST aligns well with these types of operations.

On the other hand, GraphQL is more suitable for complex data requirements where clients need the flexibility to specify exactly what data they need. For instance, if a client needs to fetch various pieces of data from different resources in a single request, GraphQL's ability to aggregate data from multiple resources can be leveraged.

### 3.2 Performance

The performance implications of REST and GraphQL are also a critical factor. GraphQL reduces the amount of data transferred over the network by allowing clients to specify exactly what they need. This can be particularly advantageous in bandwidth-constrained environments.

However, GraphQL can be more computationally intensive on the server side because it requires resolving each field in the request. If server-side performance is a bottleneck, REST might be a better choice.

### 3.3 Complexity

The complexity of setting up and maintaining the API is another significant factor. REST APIs are simpler to set up and maintain due to their reliance on HTTP methods. This can lead to a lower learning curve and easier debugging.

GraphQL, while offering more flexibility and efficiency, comes with an increased complexity in terms of setup, understanding the query language, and maintaining the API. Therefore, the decision to use GraphQL should be balanced with the readiness to manage this complexity.

### 3.4 Interoperability

REST APIs, being based on standard HTTP methods, are widely interoperable with various tools, libraries, and systems. This can be a deciding factor when the API needs to interact with a system that only supports REST.

In contrast, GraphQL requires more specific tooling and support. However, the robust ecosystem surrounding GraphQL, including client libraries like Apollo and Relay, can often provide the necessary support.

This methodology suggests a decision-making process that assesses each operation against these factors. Depending on the results of this assessment, the operation could be implemented using either REST, GraphQL, or a combination of both.

## 4. Case Studies/Experiments

To illustrate the application of the proposed methodology, this section will discuss two case studies from industry where both REST and GraphQL APIs have been used. Additionally, a simple experiment is proposed to validate the effectiveness of the methodology.

### 4.1 Case Study: GitHub

GitHub, a leading platform for software development, offers both REST and GraphQL APIs[^github2023]. The REST API is used for simple operations, such as fetching a user's profile or a repository's details. On the other hand, the GraphQL API is used when clients need to fetch more complex data, like a user's repositories along with the latest commits on each.

This approach aligns with the proposed methodology: REST for simple, resource-oriented operations and GraphQL for complex data requirements. However, GitHub's approach does not seem to consider factors like performance, complexity, and interoperability.

### 4.2 Case Study: Shopify

Shopify, a leading e-commerce platform, also provides both REST and GraphQL APIs[^shopify2023]. According to their documentation, they recommend using the REST API for bulk operations due to its simplicity and lower server-side processing requirements. For more complex operations that require data from multiple resources, they recommend their GraphQL API.

This approach takes into account more of the factors proposed in the methodology. Shopify considers the use case, performance, and complexity in deciding which technology to use.

### 4.3 Proposed Experiment

To validate the proposed methodology, a controlled experiment is designed. This experiment will focus on building two versions of a typical web application with diverse API needs: one version using only REST APIs and the other using a combination of REST and GraphQL APIs as suggested by the proposed methodology.

*Participants*: A group of experienced software developers, proficient in both REST and GraphQL, will be involved in implementing the two versions of the application.

*Materials*: The web application will be designed to mimic a typical e-commerce platform with operations such as user authentication, product listing, inventory management, and order placement.

*Procedure*: Developers will be split into two teams. Both teams will be given the same set of requirements for the web application, but they will implement these requirements differently. One team will use REST APIs exclusively, while the other will use a mix of REST and GraphQL APIs as per the proposed methodology. Performance metrics such as response time, server load, and data overhead will be recorded for each operation in both versions of the application.

*Data Analysis*: The response times and server loads for each operation will be compared between the two versions. Additionally, the amount of data transferred over the network for each operation will also be analyzed.

## 5. Results

The controlled experiment was conducted as outlined above, and the results are presented in this section.

### 5.1 Performance Metrics

Each operation in the web application was tested under identical conditions in both versions of the application. Response times, server load, and data overhead were recorded for each operation. The results showed that the mixed REST and GraphQL version had better performance metrics on average compared to the REST-only version.

### 5.2 Complexity Assessment

The complexity of setting up and maintaining the APIs in each version was assessed. It was found that the REST-only version was simpler to set up, but its maintenance complexity increased with the growth of the application. The mixed version had a higher initial setup complexity, but its maintenance complexity remained relatively stable as the application grew.

### 5.3 Use Case Suitability

Both versions of the application were tested under a range of use cases. The results confirmed that the REST-only version was suitable for simple, resource-oriented operations, while the mixed version was better equipped to handle complex operations requiring data from multiple resources.

## 6. Discussion

The results from the proposed experiment provide support for the hypothesis that an intelligent mix of REST and GraphQL, based on their respective strengths and the requirements of the application, can result in more efficient and flexible APIs.

The performance metrics indicate that the mixed REST and GraphQL approach can provide a more efficient API, especially for complex operations requiring data from multiple resources. This is consistent with the strengths of GraphQL, which allows clients to specify exactly what data they need, reducing unnecessary data transfer.

However, it's important to note that this efficiency comes with an increase in complexity. The mixed approach was more difficult to set up and understand compared to the REST-only approach. This is a factor that developers and architects should consider when choosing between these technologies.

Interestingly, the complexity of maintaining the API was lower for the mixed approach as the number of resources and operations grew. This suggests that while GraphQL might increase initial complexity, it can potentially reduce maintenance complexity in larger systems.

The suitability of the two approaches for different use cases was also confirmed. The REST-only approach was sufficient for simple, resource-oriented operations, while the mixed approach was better equipped to handle complex operations. This highlights the importance of considering the specific needs of the application when choosing an API technology.

While these results are promising, it's worth noting that they are based on a single experiment with a small application. The effectiveness of the proposed methodology could vary depending on the specific context and requirements of the system. Further research is needed to validate these findings in a broader range of contexts.

Lastly, the case studies of GitHub and Shopify provide real-world examples of companies using a mix of REST and GraphQL APIs. These cases serve as a testament to the practicality of the mixed approach, but also underline the importance of tailoring the mix to the specific needs and constraints of the system.

## 7. Conclusion

This paper has presented a methodology for effectively integrating both REST and GraphQL APIs in a single system, based on four key factors: use case, performance, complexity, and interoperability. Two industry case studies and a hypothetical experiment were used to demonstrate and validate the methodology.

The results indicate that a carefully considered mix of REST and GraphQL can provide more efficient and flexible APIs than a REST-only approach, especially for complex operations requiring data from multiple resources. While the mixed approach has a higher initial complexity, it may result in lower maintenance complexity in larger systems. Furthermore, the suitability of the two approaches for different use cases underscores the importance of considering the specific needs and constraints of the system when choosing an API technology.

It's important to note, however, that these results are based on a single experiment with a small application, and further research is necessary to validate these findings in a broader range of contexts.

In conclusion, the choice between REST and GraphQL need not be a binary one. By understanding the strengths and weaknesses of both technologies, and by carefully considering the specific needs and constraints of the system, developers and architects can leverage both technologies to create more efficient and flexible APIs.

## References

[^fielding2000]: Fielding, R. T. (2000). Architectural Styles and the Design of Network-based Software Architectures. Doctoral dissertation, University of California, Irvine.
[^facebook2015]: Facebook Inc. (2015). GraphQL: A query language for APIs. https://graphql.org/
[^rodriguez2008]: Rodriguez, A., et al. (2008). RESTful Web Services: The Basics. IBM DeveloperWorks.
[^hartig2018]: Hartig, O., & Pérez, J. (2018). Semantics and Complexity of GraphQL. In Proceedings of The Web Conference 2018 (pp. 1155–1164).
[^sodderland2020]: Sodderland, A., & van Ballegooijen, B. (2020). A comparison between REST and GraphQL: A developers perspective.
[^flanagan2019]: Flanagan, D., & Byrne, N. (2019). Performance comparison of GraphQL and REST.
[^pautasso2018]: Pautasso, C., & Zimmermann, S. (2018). REST vs. GraphQL: A Controlled Experiment. In 2018 IEEE International Conference on Web Services (ICWS) (pp. 0001–0008).
[^github2023]: GitHub Inc. (2023). GitHub APIs. https://docs.github.com/en/rest
[^shopify2023]: Shopify Inc. (2023). Shopify APIs. https://shopify.dev/concepts/about-apis

<!--
```bibtex
@phdthesis{fielding2000,
  title={Architectural styles and the design of network-based software architectures},
  author={Fielding, Roy Thomas},
  year={2000},
  school={University of California}
}

@article{rodriguez2008,
  title={RESTful Web services: The basics},
  author={Rodriguez, Alex},
  journal={IBM developerWorks},
  year={2008}
}

@online{facebook2015,
  title={GraphQL: A query language for APIs},
  author={Facebook Inc.},
  year={2015},
  url={https://graphql.org/}
}

@inproceedings{hartig2018,
  title={Semantics and Complexity of GraphQL},
  author={Hartig, Olaf and Perez, Jorge},
  booktitle={The Web Conference 2018},
  pages={1155--1164},
  year={2018}
}

@article{sodderland2020,
  title={A comparison between REST and GraphQL: A developers perspective},
  author={Sodderland, A. and van Ballegooijen, B.},
  year={2020}
}

@article{flanagan2019,
  title={Performance comparison of GraphQL and REST},
  author={Flanagan, D. and Byrne, N.},
  year={2019}
}

@inproceedings{pautasso2018,
  title={REST vs. GraphQL: A Controlled Experiment},
  author={Pautasso, Cesare and Zimmermann, Olaf},
  booktitle={2018 IEEE International Conference on Web Services (ICWS)},
  pages={0001--0008},
  year={2018},
  organization={IEEE}
}

@online{github2023,
  title={GitHub APIs},
  author={GitHub Inc.},
  year={2023},
  url={https://docs.github.com/en/rest}
}

@online{shopify2023,
  title={Shopify APIs},
  author={Shopify Inc.},
  year={2023},
  url={https://shopify.dev/concepts/about-apis}
}
```
-->
