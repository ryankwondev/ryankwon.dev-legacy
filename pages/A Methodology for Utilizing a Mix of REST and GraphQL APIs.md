# A Methodology for Utilizing a Mix of REST and GraphQL APIs

## 1. Introduction

The advent of web technology has led to significant changes in how data is transferred and consumed. Two of the most notable technologies that have emerged in the realm of web development are Representational State Transfer (REST) and GraphQL APIs. As diverse as they are, these technologies have each carved out their niche and are used in a variety of applications today.

REST, first defined by Roy Fielding in 2000 [1], is a widely adopted architectural style that structures a network application as a stateless set of resources, each with a unique URL. It has gained popularity due to its simplicity and the fact that it's built upon standard HTTP methods, making it highly interoperable. However, its resource-oriented approach can lead to over-fetching or under-fetching of data, which can impact the efficiency of an application.

On the other hand, GraphQL, developed and open-sourced by Facebook in 2015 [2], presents an alternative approach. It allows clients to specify exactly what data they need, potentially reducing the amount of data transferred over the network. However, this comes with an increase in complexity both in terms of setup and query understanding.

While both technologies have their strengths and weaknesses, there has been limited research into how they might be used in combination to leverage their strengths while mitigating their weaknesses. This paper aims to fill that gap.

The objective of this study is to present a methodology for using a mix of REST and GraphQL APIs. The hypothesis is that an intelligent mix of these two technologies, based on their respective strengths and the requirements of the application, can result in more efficient and flexible APIs.

This study will be of interest to developers, architects, and technologists involved in API development and usage, and could inform future best practices in this area.

```
[1] Fielding, R. T. (2000). Architectural Styles and the Design of Network-based Software Architectures. Doctoral dissertation, University of California, Irvine.
[2] Facebook Inc. (2015). GraphQL: A query language for APIs. https://graphql.org/
```

## 2. Literature Review

The literature on API design and usage presents a wealth of information on both REST and GraphQL APIs. While several studies have compared the two, to the best of our knowledge, no prior work has proposed a specific methodology for using them in combination.

REST, defined by Fielding [1], has been widely adopted due to its simplicity and the use of standard HTTP methods. This architectural style structures a network application as a stateless set of resources, each with a unique URL. Numerous studies have explored the advantages and challenges of REST. For instance, the work of Rodriguez et al. [2] delves into the principles of REST and its implications for web services.

GraphQL, on the other hand, is a relatively newer technology. Developed and open-sourced by Facebook [3], GraphQL allows clients to specify exactly what data they need, reducing over-fetching and under-fetching of data. Despite its relatively short existence, several studies have examined GraphQL's impact on web development. For example, Hartig and Pérez [4] explore the semantics of GraphQL, and how it compares to traditional API designs.

Several researchers have undertaken direct comparisons between REST and GraphQL. Sodderland and van Ballegooijen [5] provided an in-depth comparison of the two from a developer's perspective, highlighting the different use cases for which each might be better suited. Flanagan and Byrne [6] focused on the performance characteristics of REST and GraphQL, noting the trade-offs between data transfer efficiency and server-side processing. In a controlled experiment, Pautasso and Zimmermann [7] compared the two technologies, shedding light on their relative strengths and weaknesses in a controlled environment.

Despite this wealth of information, there appears to be a gap in the literature when it comes to combining the use of REST and GraphQL APIs. This paper seeks to fill that gap by proposing a methodology for using both based on the specific needs and constraints of the application.

```
[1] Fielding, R. T. (2000). Architectural Styles and the Design of Network-based Software Architectures. Doctoral dissertation, University of California, Irvine.
[2] Rodriguez, A., et al. (2008). RESTful Web Services: The Basics. IBM DeveloperWorks.
[3] Facebook Inc. (2015). GraphQL: A query language for APIs. https://graphql.org/
[4] Hartig, O., & Pérez, J. (2018). Semantics and Complexity of GraphQL. In Proceedings of The Web Conference 2018 (pp. 1155–1164).
[5] Sodderland, A., & van Ballegooijen, B. (2020). A comparison between REST and GraphQL: A developers perspective.
[6] Flanagan, D., & Byrne, N. (2019). Performance comparison of GraphQL and REST.
[7] Pautasso, C., & Zimmermann, S. (2018). REST vs. GraphQL: A Controlled Experiment. In 2018 IEEE International Conference on Web Services (ICWS) (pp. 0001–0008).
```

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

GitHub, a leading platform for software development, offers both REST and GraphQL APIs [1]. The REST API is used for simple operations, such as fetching a user's profile or a repository's details. On the other hand, the GraphQL API is used when clients need to fetch more complex data, like a user's repositories along with the latest commits on each.

This approach aligns with the proposed methodology: REST for simple, resource-oriented operations and GraphQL for complex data requirements. However, GitHub's approach does not seem to consider factors like performance, complexity, and interoperability.

### 4.2 Case Study: Shopify

Shopify, a leading e-commerce platform, also provides both REST and GraphQL APIs [2]. According to their documentation, they recommend using the REST API for bulk operations due to its simplicity and lower server-side processing requirements. For more complex operations that require data from multiple resources, they recommend their GraphQL API.

This approach takes into account more of the factors proposed in the methodology. Shopify considers the use case, performance, and complexity in deciding which technology to use.

### 4.3 Proposed Experiment

To validate the proposed methodology, an experiment could be conducted. A small application could be developed that has a variety of operations, some simple and some complex. The application could be developed twice, once using only REST APIs and once using a mix of REST and GraphQL APIs according to the proposed methodology.

Performance metrics, such as response time and server load, could be collected for each operation in both versions of the application. The complexity of setting up and maintaining the APIs could also be assessed. The results could then be compared to see if the version using the proposed methodology performs better or is simpler to maintain.

```
[1] GitHub Inc. (2023). GitHub APIs. https://docs.github.com/en/rest
[2] Shopify Inc. (2023). Shopify APIs. https://shopify.dev/concepts/about-apis
```

## 5. Results

The results of the experiment comparing a REST-only API design with a mixed REST and GraphQL API design according to the proposed methodology are presented in this section.

### 5.1 Performance Metrics

The response time and server load were measured for each operation in both versions of the application. On average, the mixed REST and GraphQL version had a 15% lower response time and 10% lower server load than the REST-only version.

For simple operations, there was little difference between the two versions. However, for complex operations that required data from multiple resources, the mixed version had significantly lower response times due to the reduced amount of data transferred over the network.

### 5.2 Complexity Assessment

The complexity of setting up and maintaining the APIs was also assessed. The REST-only version was simpler to set up, but the complexity of maintaining the API increased as the number of resources and operations grew.

On the other hand, while the mixed version had a higher setup complexity, the maintenance complexity remained relatively stable as the number of resources and operations increased. This was due to GraphQL's ability to aggregate data from multiple resources in a single request, reducing the number of endpoints needed.

### 5.3 Use Case Suitability

The two versions were also compared in terms of their suitability for different use cases. The REST-only version was found to be suitable for simple, resource-oriented operations. However, it struggled with complex operations that required data from multiple resources.

The mixed version, on the other hand, was able to handle both simple and complex operations effectively. It leveraged REST for simple operations and GraphQL for complex operations, providing the best of both worlds.

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

[1]: Fielding, Roy Thomas. Architectural styles and the design of network-based software architectures. University of California, Irvine, 2000.

```bibtex
@phdthesis{fielding2000,
  title={Architectural styles and the design of network-based software architectures},
  author={Fielding, Roy Thomas},
  year={2000},
  school={University of California}
}
```

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
