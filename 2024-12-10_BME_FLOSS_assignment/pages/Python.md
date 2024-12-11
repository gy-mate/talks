---
layout: center
zoom: 2.5
---

Organogram

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
1.
    - BDFL
        - josagos zsarnok (lesson 8: governance)
        - often delegates
        - now: emeritus & hierarchikus zsarnoksag & konszenzus alapu demokracia
    - what is Python?
2.
    - mintamegvalositasa: CPython
    - there are also other implementations
3.
    - core devs
    - PEPs: we'll get to them later
    - Steering Council
    - release managers
4.
    - PSF
        - supports / oversees everything
            - hosting
        - legal entity
        - Zero-Clause BSD license with an addition
            - public domain-like
-->