---
title: Python development
author: Gyöngyösi Máté
exportFilename: Python-dev_FLOSS_Gyongyosi-Mate

theme: apple-basic
contextMenu: false
lineNumbers: true

layout: intro-image-right
image: /python-logo-only.png
# todo: uncomment the line below when ... is fixed
# backgroundSize: contain

glowSeed: 7
---

Gyöngyösi Máté

# The organization of Python development

<!--
- in connection with lesson 7 (collaborative development)
- BProf: started with Python
    - still the most convenient for me
- bumped into a bug report
-->

---
layout: image
image: /issue.png

transition: slide-up
---

---
layout: section

transition: slide-left
---

# Python history

---
layout: center

transition: slide-left
---

<img src="https://gvanrossum.github.io/images/DO6GvRhi.gif" width=400 height=400>

<!--
- invented by Guido van Rossum (xidoː vɑn rɔsʏm) (https://translate.google.com/?sl=nl&tl=en&text=Guido%20van%20Rossum&op=translate)
    - in 1991
    - at the Dutch MTA
- continued working on it part-time at Google (2005–2012) and Dropbox (2013–2019)
-->

---
# layout: iframe

transition: slide-up
---

<SlidevVideo controls autoplay autoreset="click">
  <source src="/programming-languages.mp4" type="video/mp4" />
</SlidevVideo>

<!--
- `0.9` @ 1991
- `2.0` @ 2000
- `3.0` @ 2008
    - made it popular
-->

---
layout: section

transition: slide-left
---

# Python governance

---
src: ./pages/Python.md

transition: slide-up
---

---
layout: section

transition: slide-left
---

# What is Python?

---
layout: iframe
url: https://docs.python.org/3/reference/index.html

transition: slide-left
---

---
layout: iframe
url: https://docs.python.org/3/library/index.html

transition: slide-down
---

---
src: ./pages/Python.md

transition: slide-up
---

---
layout: center
zoom: 2

transition: slide-down
---

<v-clicks>

```py{2|3|4|2}
implementations = [
    "CPython",  # NOT Cython
    "PyPy"  # NOT PyPI
    "Python.NET"  # pythonnet
]
```

</v-clicks>

<!--
- CPython is the reference implementation of Python
    - Cython is a superset of Python that supports calling C functions and types
- If you love recursion:
    - [click:2] A faster Python written in R(estricted)Python, a subset of Python
    - PyPy also has a tracing JIT compiler. PyPy was funded by the EU by 1 billion HUF and by the Mozilla Foundation by 100 million HUF
- [click] Embedding Python into .NET (NuGet package) & .NET into Python (PyPI package)
    - Funded by Microsoft
-->

---
src: ./pages/Python.md

transition: slide-left
---

---
transition: slide-left
---

# Release cycle

![](https://peps.python.org/_images/pep-0602-example-release-calendar.png)

<!--
- stages
    - 1.5 years of development
    - 5 years of updates
        - 2 years of bugfixes
        - 3 years of security updates
    - every release is LTS
- altogether: 6.5 years
- the illustration is for the transition period
    - ended with the current release (`3.13`)
- what this means...
-->

---
layout: iframe
url: https://devguide.python.org/versions/

transition: slide-down
---

---
src: ./pages/Python.md

transition: slide-left
---

---
layout: center
class: text-center

transition: slide-up
---

# Join the PSF today!

[python.org/users/membership](https://www.python.org/users/membership/)

<!--
- create an account
- virtually sign the Code of Conduct
-->

---
layout: section

transition: slide-left
---

# Rust governance

---
layout: center
zoom: 2

transition: slide-left
---

Organogram

```mermaid
flowchart TD
    council("Leadership Council (7)")
    teams("Teams")
    WGs("Working Groups")
    users("Rustaceans (anyone)")
    RFCs
    Foundation("Rust Foundation")
    corporations

    corporations -.members of.-> Foundation

    Foundation -.legal entity of / funds.-> Rust

    council -->|accept / reject| RFCs
    council -->|oversee| teams

    users -."author".-> RFCs

    WGs -->|author| RFCs

    RFCs -->|shape| Rust
    RFCs -.estabilish.-> WGs

    teams -->|sponsor| WGs
    teams -->|delegate one representative each| council
    teams -->|approve the creation of| WGs
```

<!--
- MIT license and the Apache 2.0 License
    - portions covered by BSD-like licenses
-->

---
layout: center
zoom: 2.5

transition: slide-up
---

RFC process

```mermaid
flowchart LR
    idea("An idea")
    fork("Fork *github.com/rust-lang/rfcs*")
    write("Write the RFC")
    PR("Submit a pull request")
    ID("Number assigned (PR #)")
    decision{"The Leadership Council decides"}
    yes("PR merged")
    no("PR closed")

    idea --> fork
    fork --> write
    write --> PR
    PR --> ID
    ID --> decision
    decision -- Accept --> yes
    decision -- Reject --> no
```

<!--
- *"As an alternative, we could adopt an even stricter RFC process than the one proposed here. If desired, we should likely look to Python’s PEP process for inspiration."*
-->

---
layout: section

transition: slide-left
---

# vs. Python

---
layout: center
zoom: 2.5

transition: slide-left
---

PEP process

```mermaid
flowchart LR
    idea("An idea")
    post("Post to *discuss.python.org*")
    chance{"Is there any chance of acceptance?"}
    reject(["Rejected"])
    core{"Are any of the authors core developers?"}
    find("Find a sponsor")
    write("Write the PEP")
    PR("Submit a pull request to *github.com/python/peps*")
    editors{"Review of the PEP editors"}
    ID("Number assigned")
    merge("PR merged")
    discuss("Discuss on *discuss.python.org*")
    typing{"Is the PEP about typing?"}
    typing_issue("Open an issue at *github.com/python/typing-council*")
    recommendation("The Typing Council makes a recommendation to the Steering Council")
    issue("Open an issue at *github.com/python/steering-council*")
    nomination{"Does a core developer nominate themselves as a PEP-Delegate?"}
    delegate("The Steering Council searches for a PEP-Delegate")
    found("A PEP-Delegate is found")
    not_found("No PEP-Delegate was found")
    defer("The PEP is Deferred")
    decision{"The PEP-Delegate decides"}
    approve("Approved")
    council_decision{"The Steering Council decides"}
    accept(["Accepted"])

    idea --> post
    post --> chance
    chance -- No --> reject
    chance -- Yes --> core
    core -- No --> find
    find --> write
    core -- Yes --> write
    write --> PR
    PR --> editors
    editors -- Request changes --> write
    editors -- Approve --> ID
    ID --> merge
    merge --> discuss
    discuss --> typing
    typing -- Yes --> typing_issue
    typing_issue --> recommendation
    recommendation --> issue
    typing -- No --> issue
    issue --> nomination
    nomination -- No --> delegate
    delegate --> found
    delegate --> not_found
    not_found --> defer
    defer --> nomination
    nomination -- Yes --> found
    found --> decision
    decision -- Reject --> reject
    decision -- Approve --> approve
    approve --> council_decision
    council_decision -- Reject --> reject
    council_decision -- Accept --> accept
```

<!--
- if you have a larger screen, set the video quality to maximum
- discussions are public (lesson 7: collaborative development)
-->

---
layout: iframe
url: https://peps.python.org/pep-0010/

transition: slide-up
---

<!--
- Apache-like (lesson 8: governance)
- ~polling
- for smaller decisions
-->

---
layout: section

transition: slide-left
---

# Looks are important!

<!--
- as said in lesson 7 (collaborative development): looks are important
- but this is mainly a problem for first-time contributors
-->

---
src: ./pages/PEPs.md
---

---
transition: slide-up
---

```py
from datetime import datetime
import json
import requests

peps_json = json.loads(requests.get("https://peps.python.org/api/peps.json").text)
peps = [value for key, value in peps_json.items()]
peps = sorted(peps, key=lambda pep: datetime.strptime(pep["created"], "%d-%b-%Y"))

retrospect = 5
print(f"The last {retrospect} PEPs are:")
for pep in peps[-retrospect:]:
    print(f"- PEP {pep["number"]} created on {pep["created"]}: {pep["title"]}")
```

<v-click>
```md {*}{lines: false}
The last 5 PEPs are:
- PEP 763 created on 24-Oct-2024: Limiting deletions on PyPI
- PEP 765 created on 15-Nov-2024: Disallow return/break/continue that exit a finally block
- PEP 766 created on 18-Nov-2024: Explicit Priority Choices Among Multiple Indexes
- PEP 767 created on 18-Nov-2024: Annotating Read-Only Attributes
- PEP 768 created on 25-Nov-2024: Safe external debugger interface for CPython
```
</v-click>

<!--
- ~7 lines
- can quickly see that the project is well alive
-->

---
src: ./pages/PEPs.md
---

---
layout: iframe
url: https://rust-lang.github.io/rfcs/

transition: slide-up
---

<!--
- RFC organization
- no API
- click on an RFC
    - no authors, date, TOC
- groups have several different names
- these make it harder to understand the dev process
-->

---
layout: section

transition: slide-up
---

# Summary

<!--
- a looser governance understandable from a smaller community
    - it's more like a meritoracy (lesson 8: governance)
- Python is huge
    - many checkpoints
    - but they are inclusive and clear
    - and take the weight off developers' shoulders
- both of them work well

- so thank you for your attention
-->

---
layout: statement

transition: slide-up
---

https://github.com/gy-mate/talks/tree/main/2024-12-10_BME_FLOSS_assignment

<!--
- questions (teachers / fellow students): I'm available on Teams
- the presentation source is available on this link
-->

---
zoom: 0.54

transition: slide-left
---

# References

- [1] C. F. Bolz-Tereick, ‘The First 15 Years of PyPy — a Personal Retrospective’. Accessed: Dec. 08, 2024. [Online]. Available: https://pypy.org/posts/2018/09/the-first-15-years-of-pypy-3412615975376972020.html
- [2] bstrie and B. Anderson, ‘0002-rfc-process’. Mar. 11, 2014. Accessed: Dec. 10, 2024. [Online]. Available: https://rust-lang.github.io/rfcs/0002-rfc-process.html
- [3] Cython developers, ‘About Cython’. Accessed: Dec. 08, 2024. [Online]. Available: https://cython.org/
- [4] Data Is Beautiful, Most Popular Programming Languages 1965 - 2022, (Dec. 12, 2022). Accessed: Dec. 10, 2024. [Online Video]. Available: https://www.youtube.com/watch?v=qQXXI5QFUfw
- [5] S. J. Turner et al., ‘3392-leadership-council’. Aug. 01, 2022. Accessed: Dec. 10, 2024. [Online]. Available: https://rust-lang.github.io/rfcs/3392-leadership-council.html
- [6] Ł. Langa, ‘PEP 602 – Annual Release Cycle for Python’. Jun. 04, 2019. Accessed: Dec. 10, 2024. [Online]. Available: https://peps.python.org/pep-0602/
- [7]. NET Foundation, ‘Python.NET documentation’. 2022. Accessed: Dec. 08, 2024. [Online]. Available: https://pythonnet.github.io/pythonnet/
- [8]. NET Foundation, .‘NET Foundation’. 2024. Accessed: Dec. 08, 2024. [Online]. Available: https://dotnetfoundation.org/
- [9] Python Software Foundation, ‘Experts index’. 2011. Accessed: Dec. 10, 2024. [Online]. Available: https://devguide.python.org/core-developers/experts/#
- [10] Python Software Foundation, ‘About the Python Software Foundation’. 2024. Accessed: Dec. 09, 2024. [Online]. Available: https://www.python.org/psf/about/
- [11] Python Software Foundation, ‘The Python Language Reference’. 2024. Accessed: Dec. 08, 2024. [Online]. Available: https://docs.python.org/3/reference/index.html
- [12] Python Software Foundation, ‘The Python Standard Library’. 2024. Accessed: Dec. 08, 2024. [Online]. Available: https://docs.python.org/3/library/index.html
- [13] Rust Team, ‘Governance’. Accessed: Dec. 10, 2024. [Online]. Available: https://www.rust-lang.org/governance
- [14] The PEP Editors, ‘PEP 0 – Index of Python Enhancement Proposals (PEPs)’. Jul. 13, 2000. Accessed: Dec. 10, 2024. [Online]. Available: https://peps.python.org
- [15] The PyPy Team, ‘PyPy’. 2024. Accessed: Dec. 08, 2024. [Online]. Available: https://pypy.org/
- [16] The Python core team and community, ‘PEP 13 – Python Language Governance’. Dec. 16, 2018. Accessed: Dec. 09, 2024. [Online]. Available: https://peps.python.org/pep-0013/
- [17] A. Turon, ‘1068-rust-governance’. Feb. 27, 2015. Accessed: Dec. 10, 2024. [Online]. Available: https://rust-lang.github.io/rfcs/1068-rust-governance.html
- [18] G. Van Rossum, ‘Personal Home Page’. Accessed: Dec. 08, 2024. [Online]. Available: https://gvanrossum.github.io
- [19] M. Von Löwis and B. Cannon, ‘PEP 11 – CPython platform support’. Jul. 07, 2002. Accessed: Dec. 10, 2024. [Online]. Available: https://peps.python.org/pep-0011/
- [20] B. Warsaw, ‘PEP 10 – Voting Guidelines’. Mar. 07, 2002. Accessed: Dec. 10, 2024. [Online]. Available: https://peps.python.org/pep-0010/
- [21] B. Warsaw, J. Hylton, D. Goodger, and A. Coghlan, ‘PEP 1 – PEP Purpose and Guidelines’. Jun. 13, 2000. Accessed: Dec. 09, 2024. [Online]. Available: https://peps.python.org/pep-0001/
- [22] Wikipedia contributors, ‘Guido van Rossum — Wikipedia, The Free Encyclopedia’. 2024. [Online]. Available: https://en.wikipedia.org/w/index.php?title=Guido_van_Rossum&oldid=1261004768
- [23] Wikipedia contributors, ‘Python (programming language) — Wikipedia, The Free Encyclopedia’. 2024. [Online]. Available: https://en.wikipedia.org/w/index.php?title=Python_(programming_language)&oldid=1261797535
- [24] Wikipedia contributors, ‘Python Software Foundation — Wikipedia, The Free Encyclopedia’. 2024. [Online]. Available: https://en.wikipedia.org/w/index.php?title=Python_Software_Foundation&oldid=1261952004
- [25] Wikipedia contributors, ‘Rust (programming language) — Wikipedia, The Free Encyclopedia’. 2024. [Online]. Available: https://en.wikipedia.org/w/index.php?title=Rust_(programming_language)&oldid=1261392251
- [26] XAMPPRocky, N. Matsakis, and valgrimm, ‘2856-project-groups’. May 21, 2015. Accessed: Dec. 10, 2024. [Online]. Available: https://rust-lang.github.io/rfcs/2856-project-groups.html

<!--
- I used these sources
-->

---
transition: slide-left
---

# Made with

| | |
|-|-|
| <img src="https://user-images.githubusercontent.com/57955862/229143220-d9c01168-1e38-4093-88d2-3a4ac251bb2b.png" width=50> | [`vscodium`](https://github.com/VSCodium/vscodium) |
| <img src="https://repository-images.githubusercontent.com/307260205/b6a8d716-9c7b-40ec-bc44-6422d8b741a0" width=40> | [`yt-dlp`](https://github.com/yt-dlp/yt-dlp) |
| <img src="https://cdn.icon-icons.com/icons2/3053/PNG/512/ffmpeg_macos_bigsur_icon_190192.png" width=50> | [`ffmpeg`](https://git.ffmpeg.org/ffmpeg.git) |
| <img src="https://cdn-1.webcatalog.io/catalog/mermaid-chart/mermaid-chart-icon-unplated.png?v=1721019852605" width=40> | [Mermaid](https://github.com/mermaid-js/mermaid) |
| <img src="https://www.zotero.org/support/_media/logo/zotero_1024x1024x32.png" width=50> | [Zotero](https://github.com/zotero/zotero) |

<PoweredBySlidev mt-6/>

<!--
- I used these open source tools to create the presentation
- yt-dlp was written in Python
- we talked about Zotero vs. EndNote in lesson 3 (legal)

- good luck with the exams
-->

---
layout: center
zoom: 2.5
---

```py {lines: true}
sys.exit()
```

<!--
- happy holidays!
-->
