---
layout: default
description: Course material for the University of Manitoba course MATH 4370-7370, Linear Algebra and Matrix Analysis
---

## University of Manitoba <br>MATH 4370-7370<br>Linear Algebra and Matrix Analysis<br>Course information

Here, you can find some information about the course. Note that most documents will be distributed using UMLearn.

- [Course outline](course-outline-2023.html)
- [Tentative schedule](tentative-schedule.html)
- [Information about projects](project-information.html)

### Assignments

- [Project assignment 1 (PA1)](/assets/pdf/MATH-4370-7370-F2023-PA1.pdf)
- [Project assignment 2 (PA2)](/assets/pdf/MATH-4370-7370-F2023-PA2.pdf)

Other assignments will be distributed using UMLearn.

### Slides

Note that it is likely that these slides include typos.

<ul>
{% for file in site.static_files %}
  {% if file.path contains 'SLIDES' %}
    {% if file.path contains 'MATH-4370' %}
      {% if file.path contains 'pdf' %}
          <li><a href="https://julien-arino.github.io/math-4370-7370/SLIDES/{{ file.basename }}.pdf">{{ file.basename }}</a></li>
      {% endif %}
      {% if file.path contains 'html' %}
          <li><a href="https://julien-arino.github.io/math-4370-7370/SLIDES/{{ file.basename }}.html">{{ file.basename }}</a></li>
      {% endif %}
    {% endif %}
  {% endif %}
{% endfor %}
</ul>
