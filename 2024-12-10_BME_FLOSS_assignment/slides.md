---
title: Python development
author: Gyöngyösi Máté
exportFilename: Python-dev_FLOSS_Gyongyosi-Mate

theme: apple-basic
lineNumbers: true
contextMenu: false

layout: intro-image-right
image: /python-logo-only.png
# todo: uncomment the line below when ... is fixed
# backgroundSize: contain

glowSeed: 7
---

# The development process of Python

---
layout: center
---

<img src="https://gvanrossum.github.io/images/DO6GvRhi.gif" width=500 height=500>

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
- `3.0` @ 2008 (thanks to Google)
-->

---
layout: iframe
url: https://docs.python.org/3/reference/index.html

transition: slide-left
---

---
layout: iframe
url: https://docs.python.org/3/library/index.html

transition: slide-up
---

---
layout: center
zoom: 2

transition: fade
---

<v-clicks>

```py {2|3|4|2}
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
    - [click] A faster Python written in R(estricted)Python, a subset of Python
    - PyPy also has a tracing JIT compiler. PyPy was funded by the EU by 1 billion HUF and by the Mozilla Foundation by 100 million HUF
- [click] Embedding Python into .NET (NuGet package) & .NET into Python (PyPI package)
    - Funded by Microsoft
-->

---
layout: center
zoom: 2.5
---

```mermaid
flowchart TD
    PSF("Python Software Foundation (PSF; ~25)")
    BDFL("`*Benevolent Dictator for Life (BDFL; 1)*`")
    Steering("Python Steering Council (5)")
    core_devs("CPython core developers (118)")
    PEPs("Python Enhancement Proposals (PEPs; 380)")
    users("Pythonistas (anyone)")
    platforms
    corporations

    BDFL -.member of.-> core_devs

    Steering -->|head of / guides| core_devs
    Steering -->|can veto membership of| core_devs
    Steering -->|accept / reject| PEPs
    Steering -.works with.-> PSF
    Steering -->|nominates a release manager from| core_devs

    users -.basic member of.-> PSF
    users -.author.-> PEPs

    corporations -.sponsor.-> PSF
    
    PSF -.legal entity of / funds.-> Python

    core_devs -->|author / sponsor| PEPs
    core_devs -->|develop| CPython
    core_devs -->|contributing members or fellows of| PSF
    core_devs -->|elect| Steering
    core_devs -->|sponsor| platforms
    core_devs -.accept / reject (if delegated).-> PEPs
    
    CPython -->|reference implementation of| Python
    CPython -->|runs on| platforms
    
    PEPs -->|shape| Python
```

<!--
- PSF
    - supports / oversees everything
        - hosting
- BDFL-emeritus
-->

---
layout: center
zoom: 2
---

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

---
layout: center
zoom: 2.5
---

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
*"As an alternative, we could adopt an even stricter RFC process than the one proposed here. If desired, we should likely look to Python’s PEP process for inspiration."*
-->

---
layout: center
zoom: 2.5
---

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
    nomination{"Does a core developer nominate themselves as a PEP-Delgate?"}
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

---
class: text-center
---

# Made with

<img src="https://upload.wikimedia.org/wikipedia/commons/9/9a/Visual_Studio_Code_1.35_icon.svg" width=50> Visual Studio Code
<img src="https://repository-images.githubusercontent.com/307260205/b6a8d716-9c7b-40ec-bc44-6422d8b741a0" width=50> `yt-dlp`
<img src="https://cdn.icon-icons.com/icons2/3053/PNG/512/ffmpeg_macos_bigsur_icon_190192.png" width=65> `ffmpeg`
<img src="https://cdn-1.webcatalog.io/catalog/mermaid-chart/mermaid-chart-icon-unplated.png?v=1721019852605" width=50> Mermaid.js
<img src="https://www.zotero.org/support/_media/logo/zotero_1024x1024x32.png" width=60> Zotero

<PoweredBySlidev/>
