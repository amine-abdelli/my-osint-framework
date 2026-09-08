# Environment setup

## Option A — a ready-made OSINT VM

| Distribution | Focus | Status |
| --- | --- | --- |
| **Trace Labs OSINT VM** | Search and rescue, missing persons | Active — `tracelabs.org/initiatives/osint-vm` |
| **CSI Linux** | Digital forensics + OSINT, enterprise-grade | Active — `csilinux.com` |
| **Tsurugi Linux** | DFIR with a comprehensive OSINT suite | Active — `tsurugi-linux.org` |
| **Tails** | Amnesic live OS, maximum anonymity | Active |
| ~~Buscador~~ | Michael Bazzell's general OSINT VM | ⚠️ **Discontinued by IntelTechniques** |

## Option B — build your own

### Base

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y python3 python3-pip git curl wget \
    build-essential libssl-dev libffi-dev python3-dev golang-go
```

### Core OSINT tools

```bash
mkdir -p ~/osint-tools && cd ~/osint-tools

# Python-installable
pip3 install recon-ng maigret h8mail holehe waybackpy

# Git-based
git clone https://github.com/laramies/theHarvester && \
    cd theHarvester && pip3 install -r requirements.txt && cd ..

git clone https://github.com/sherlock-project/sherlock && \
    cd sherlock && pip3 install -r requirements.txt && cd ..

git clone https://github.com/smicallef/spiderfoot && \
    cd spiderfoot && pip3 install -r requirements.txt && cd ..

git clone https://github.com/s0md3v/Photon && \
    cd Photon && pip3 install -r requirements.txt && cd ..

# Go tools
go install -v github.com/owasp-amass/amass/v4/...@latest
go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest
go install -v github.com/projectdiscovery/httpx/cmd/httpx@latest
go install -v github.com/tomnomnom/waybackurls@latest

# PhoneInfoga — download the latest release binary from GitHub
```

### Evidence and archival

```bash
cargo install monolith            # self-contained HTML archives
sudo apt install -y cutycapt      # CLI screenshots
pip3 install waybackpy            # Wayback submission
```

### Utilities

```bash
sudo apt install -y nmap masscan whois dnsutils netcat   # network
sudo apt install -y curl wget httpie jq                  # web / JSON
sudo apt install -y exiftool ffmpeg                      # media / metadata
sudo apt install -y metagoofil                           # document metadata
```

### One-shot setup script

```bash
#!/bin/bash
set -e
sudo apt update && sudo apt upgrade -y
sudo apt install -y python3 python3-pip git curl wget \
    build-essential libssl-dev libffi-dev python3-dev \
    golang-go nmap masscan whois dnsutils exiftool cutycapt jq httpie ffmpeg

mkdir -p ~/osint-tools && cd ~/osint-tools
pip3 install recon-ng maigret h8mail holehe waybackpy

for repo in laramies/theHarvester sherlock-project/sherlock \
            smicallef/spiderfoot s0md3v/Photon; do
  name=$(basename "$repo")
  git clone "https://github.com/$repo" && \
    (cd "$name" && pip3 install -r requirements.txt)
done

go install -v github.com/owasp-amass/amass/v4/...@latest
go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest
go install -v github.com/projectdiscovery/httpx/cmd/httpx@latest
go install -v github.com/tomnomnom/waybackurls@latest

echo "OSINT setup complete — tools in ~/osint-tools/"
```

## API keys

Several tools are dramatically more useful with keys. Keep them in a config file **outside**
the repo, and use **separate keys** for OSINT work — never production or personal keys.

Commonly worth having: Shodan · Censys · HaveIBeenPwned · Hunter.io · AbuseIPDB ·
VirusTotal · SecurityTrails · Etherscan.

Suggested location: `~/.config/osint/api_keys.conf`, mode `600`, git-ignored.

## Case workspace

```bash
mkdir -p ~/OSINT_Cases
```

Structure per case: [`../01-methodology/evidence-preservation.md`](../01-methodology/evidence-preservation.md).
Templates: [`../05-templates/`](../05-templates/).

## Networking and OPSEC

Set up before the first query, not after — see
[`../01-methodology/opsec.md`](../01-methodology/opsec.md).

```
✅ VPN or Tor
✅ Dedicated browser profile(s)
✅ VM snapshot of the clean state, so you can roll back
✅ Encrypted volume for case data
```

## Sources

- Pnwcomputers, *OSINT Guide* — VM setup, install scripts
- i-intelligence, *OSINT Handbook 2018* — Virtual Machine, Secure OS
