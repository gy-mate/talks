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
layout: center
# zoom: 2
---

```mermaid

```

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

```py {1|2|3|4|2}
implementations = [
    "CPython",  # NOT Cython
    "PyPy"  # NOT PyPI
    "Python.NET"  # pythonnet
]
```

</v-clicks>

<!--
- [click:2] Cython is a superset of Python that supports calling C functions and types
- If you love recursion:
    - [click] A faster Python written in R(estricted)Python, a subset of Python
    - PyPy also has a tracing JIT compiler. PyPy was funded by the EU by 1 billion HUF and by the Mozilla Foundation by 100 million HUF
- [click] Embedding Python into .NET (NuGet package) & .NET into Python (PyPI package)
    - Funded by Microsoft

- [click] CPython is the reference implementation of Python
- 
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

    BDFL -.member of.-> core_devs

    Steering -->|head of / guides / vetoes membership of| core_devs
    Steering -->|accept / reject| PEPs
    Steering -.works with.-> PSF

    users -.basic member of.-> PSF
    users -.author.-> PEPs
    
    PSF -.legal entity of / funds.-> Python

    core_devs -->|author / sponsor| PEPs
    core_devs -->|develop| CPython
    core_devs -->|contributing members or fellows of| PSF
    core_devs -->|elect| Steering
    core_devs -->|sponsor| platforms
    
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
zoom: 2.5
---

```mermaid
flowchart TD                                                                  
    RustFest("RustFest")                                                      
    Servo("Servo Project")                                                    
    Core("Rust Core Team (11)")                                               
    Moderation("Moderation Team")                                             
    ProjectLeads("Project Leads (various teams)")                             
    WorkingGroups("Working Groups")                                           
    Users("Rustaceans (anyone)")                                              
    RFCs("Rust Feature Requests (RFCs)")                                      
                                                                                
    RustFest -.member of.-> WorkingGroups                                     
                                                                                
    Core -->|head of / guides| ProjectLeads                                   
    Core -->|approve / merge| RFCs                                            
    Core -->|oversee| Moderation                                              
    Core -.liaise with.-> Servo                                               
                                                                                
    Users -."contributor to".-> WorkingGroups                                   
    Users -."input provider to".-> RFCs                                         
                                                                                
    WorkingGroups -->|collaborate with| ProjectLeads                          
    WorkingGroups -->|generate| RFCs                                          
                                                                                
    ProjectLeads -->|implement| Rust                                          
    ProjectLeads -->|manage teams| WorkingGroups                              
    ProjectLeads -->|propose| RFCs                                            
                                                                                
    RFCs -->|shape| Rust                                                      
    Moderation -.ensures compliance for.-> WorkingGroups
```

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
layout: center
class: text-center
---

<PoweredBySlidev mt-10 />
