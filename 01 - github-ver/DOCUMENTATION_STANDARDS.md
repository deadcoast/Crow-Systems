# CROW Documentation Standards

## Overview

This document defines the professional formatting standards for the CROW Drone Systems documentation suite. These standards ensure consistency, readability, and proper GitHub rendering across all technical documents.

## Document Suite Structure

### Core Document Types

- **Proof of Concept**: Technical feasibility demonstrations
- **Technical Documentation**: System specifications and implementation details  
- **Research**: Evidence-based analysis and findings
- **Mathematical Content**: Formulas and equations using MathJax
- **Code Documentation**: Python, JavaScript, and other programming languages

## Formatting Standards

### File Naming Convention

```
[Number] - [Descriptive Title].md
```

Examples:
- `1 - CROW Systems Overview.md`
- `2 - Problem Statement.md`
- `3 - Drone Spec.md`

### Heading Structure

```markdown
# Document Title (H1 - Single per file)
## Section Title (H2)
### Subsection Title (H3)
#### Detail Title (H4)
```

### Link Formatting

#### Internal Links (GitHub-friendly)
```markdown
[Link Text](relative/path/to/file.md)
[Link Text](01%20-%20github-ver/path/to/file.md)
```

#### Reference Links
```markdown
[Link Text][1]

[1]: https://example.com "Reference Title"
```

### Code Blocks

#### Language-specific formatting
````markdown
```python
def example_function():
    return "Hello World"
```
````

#### MathJax equations
````markdown
```math
E = mc^2
```
````

### Tables

Use GitHub-compatible table formatting:

```markdown
| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Data 1   | Data 2   | Data 3   |
```

### Mathematical Content

#### Inline Math
```markdown
The formula $E = mc^2$ demonstrates...
```

#### Block Math
```markdown
$$
\begin{align}
P(x) &= \frac{1}{\sigma\sqrt{2\pi}} e^{-\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^2}
\end{align}
$$
```

## Content Guidelines

### Technical Documentation

1. **Clear Structure**: Use consistent heading hierarchy
2. **Code Examples**: Include working code samples with explanations
3. **References**: Link to authoritative sources
4. **Diagrams**: Use Mermaid or ASCII art for visual elements

### Research Documents

1. **Evidence-Based**: Support claims with citations
2. **Methodology**: Clearly describe research methods
3. **Results**: Present findings objectively
4. **Conclusions**: Draw logical conclusions from evidence

### Mathematical Content

1. **Notation**: Use consistent mathematical notation
2. **Units**: Include proper units in calculations
3. **Derivations**: Show step-by-step mathematical derivations
4. **Validation**: Verify mathematical accuracy

## Quality Assurance

### Pre-commit Checklist

- [ ] File follows naming convention
- [ ] Single H1 heading per file
- [ ] All links are valid and properly formatted
- [ ] Code blocks have appropriate language tags
- [ ] Mathematical content is properly formatted
- [ ] Tables are properly aligned
- [ ] No trailing whitespace
- [ ] File ends with newline

### Linting Rules

The project uses markdownlint with the following key rules:

- **MD013**: Line length limit of 120 characters
- **MD022**: Blank lines around headings
- **MD025**: Single top-level heading per file
- **MD031**: Blank lines around code blocks
- **MD047**: Files must end with newline

## GitHub Integration

### Repository Structure

```
01 - github-ver/
├── 00 - Maps of Content/     # Navigation indexes
├── 01 - Crow_Systems/        # Core system documentation
├── 02 - Research/            # Research and analysis
├── 03 - Evidence Block/      # Evidence and validation
├── 04 - Claims/              # Technical claims and proofs
├── 05 - Post Prototype/      # Implementation protocols
└── 99 - META/                # Templates and utilities
```

### Navigation

Each section includes an index file that provides:
- Overview of section contents
- Links to all documents in the section
- Cross-references to related sections

## Maintenance

### Regular Tasks

1. **Link Validation**: Check that all internal links work
2. **Format Consistency**: Ensure consistent formatting across documents
3. **Content Updates**: Keep technical content current
4. **Reference Verification**: Validate external links and citations

### Version Control

- Use descriptive commit messages
- Tag major documentation releases
- Maintain changelog for significant updates

---

*This document is part of the CROW Drone Systems documentation suite.*
