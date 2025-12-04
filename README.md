# ALICE3SimulationHandsOn
Hands on software for the ALICE3 simulation

https://indico.cern.ch/event/1605731/


## Instructions to get started

In order to get ready for the hands on you should have the most recent **O2Physics** and **ACTS** installed via *aliBuild*.

### O2Physics Installation Decision Tree

```
START: Do you have O2Physics installed?
│
├─ NO ──→ Do you have aliBuild installed?
│         │
│         ├─ NO ──→ Install prerequisites
│         │         │
│         │         ├─ Are you on macOS?
│         │         │   └─ YES ──→ Install: Xcode, Homebrew, then run:
│         │         │              brew install alisw/system-deps/o2-full-deps
│         │         │
│         │         ├─ Are you on Ubuntu/Debian?
│         │         │   └─ YES ──→ Install system dependencies:
│         │         │              sudo apt-get install curl libcurl4-openssl-dev python3-pip
│         │         │
│         │         └─ Are you on CentOS/RHEL/Alma?
│         │             └─ YES ──→ Install system dependencies:
│         │                        sudo yum install curl libcurl-devel python3-pip
│         │         │
│         │         └──→ Install aliBuild:
│         │              pip3 install alibuild --upgrade
│         │
│         └─ YES ──→ Is aliBuild up to date?
│                   │
│                   ├─ NO ──→ Update aliBuild:
│                   │         pip3 install alibuild --upgrade
│                   │
│                   └─ YES ──→ Create work directory and initialize:
│                              mkdir -p ~/alice && cd ~/alice
│                              aliBuild init O2Physics@master
│                              │
│                              └──→ Build O2Physics:
│                                   aliBuild build O2Physics --defaults o2
│                                   │
│                                   └──→ Install ACTS (see ACTS section)
│
└─ YES ──→ Is O2Physics up to date?
           │
           ├─ NO ──→ Update O2Physics:
           │         cd ~/alice/O2Physics (or your O2Physics path)
           │         git pull --rebase
           │         cd ~/alice
           │         aliBuild build O2Physics --defaults o2 --force-unknown-architecture
           │         │
           │         └──→ Load environment:
           │              alienv enter O2Physics/latest
           │
           └─ YES ──→ Load environment and verify:
                      alienv enter O2Physics/latest
                      o2-sim --version
                      │
                      └──→ Is ACTS installed?
                           │
                           ├─ NO ──→ Install ACTS:
                           │         aliBuild build ACTS --defaults o2
                           │
                           └─ YES ──→ READY FOR HANDS-ON! ✓

Troubleshooting:
├─ Build fails? ──→ Check: disk space, internet connection, system dependencies
├─ Environment issues? ──→ Run: alienv q (query installed packages)
└─ Still problems? ──→ Clean rebuild: aliBuild build O2Physics --defaults o2 -d
```

### Quick Start Commands

For those who already have prerequisites:

```bash
# Install aliBuild
pip3 install alibuild --upgrade

# Initialize and build O2Physics
mkdir -p ~/alice && cd ~/alice
aliBuild init O2Physics@master
aliBuild build O2Physics --defaults o2

# Build ACTS
aliBuild build ACTS --defaults o2

# Load environment
alienv enter O2Physics/latest
```

