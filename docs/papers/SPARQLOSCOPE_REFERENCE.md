# SPARQLoscope Paper Reference

## Citation

Bast, H., Kalmbach, J., Textor-Falconi, R., & Ullinger, C. (2025). **Sparqloscope: A Generic Benchmark for the Comprehensive and Concise Performance Evaluation of SPARQL Engines**. In *The Semantic Web – ISWC 2025*, Lecture Notes in Computer Science, vol 16141, pp. 22-40. Springer, Cham.

## Links

- **Paper PDF:** https://ad-publications.cs.uni-freiburg.de/ISWC_sparqloscope_BKTU_2025.pdf
- **DOI:** https://doi.org/10.1007/978-3-032-09530-5_2
- **GitHub Repository:** https://github.com/ad-freiburg/sparqloscope
- **Evaluation Results:** https://qlever.dev/evaluation-paper/

## Key Information

### Authors (Conflict of Interest Note)

All four authors are from the University of Freiburg and are contributors to the QLever project:
- Hannah Bast - QLever creator and lead
- Johannes Kalmbach - QLever core contributor
- Robin Textor-Falconi - QLever contributor
- Christoph Ullinger - QLever contributor

### Benchmark Design

SPARQLoscope generates approximately **100 queries** per knowledge graph, organized into the following categories:

#### Query Categories (from `query-templates.yaml`)

| Category | Variants | Description |
|----------|----------|-------------|
| JOIN | 6 | Two-pattern, three-pattern (star/chain), extreme (25+ predicates) |
| OPTIONAL JOIN | 8 | Left-outer join with various predicate sizes |
| MINUS JOIN | 8 | Set difference operations |
| EXISTS JOIN | 8 | Existential filtering with binding propagation |
| UNION | 4+ | Two-branch unions with various constraints |
| MULTICOLUMN JOIN | 2 | Multi-column join patterns |
| GROUP BY | 8 | COUNT, MIN, MAX, SAMPLE, GROUP_CONCAT, etc. |
| DISTINCT | 3 | COUNT DISTINCT variants |
| Transitive Closure | 4 | Property path reachability |
| String Filters | 8 | CONTAINS, REGEX, prefix matching |
| Numeric Filters | 3 | Range filters at various percentiles |
| String Functions | 5 | STRLEN, STRBEFORE, STRAFTER, etc. |
| Numeric Functions | 7 | ABS, CEIL, FLOOR, ROUND, arithmetic |
| Date Functions | 3 | YEAR, MONTH, DAY extraction |
| Result Export | 5 | Scaling from 10 to 10M tuples |
| Statistics | 5 | Baseline triple/entity counts |

### Engines Evaluated

1. QLever (C++)
2. Virtuoso (C)
3. MillenniumDB (C++)
4. GraphDB (Java)
5. Blazegraph (Java)
6. Apache Jena (Java)

### Datasets Used

1. **DBLP** - ~500 million triples, academic bibliographic data
2. **Wikidata Truthy** - ~8 billion triples, encyclopedic knowledge

### Methodology Notes

- Queries test features **in isolation**, not in combination
- Queries are generated from templates with placeholders filled from actual dataset
- Results intended for **individual query analysis**, not aggregate statistics
- Cold cache methodology (cache cleared between queries)

## Critique Points

See `QLEVER_PERFORMANCE_ANALYSIS.md` for detailed analysis of:
- Same-author conflict of interest
- Isolation testing vs. real-world combined queries
- Dataset generalization limitations
- Missing concurrent workload testing
