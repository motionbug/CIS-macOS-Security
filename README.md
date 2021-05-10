# CIS-macOS-Security Compliance Project

_**Current state of the scripts are:** "This project is "As is" please be free to give me any feedback_

```THE SCRIPTS ARE PROVIDED "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, 
INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY 
AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL 
I BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, 
OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF 
SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS 
INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN 
CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) 
ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF 
THE POSSIBILITY OF SUCH DAMAGE.
```

![GitHub](https://img.shields.io/github/license/mvdbent/CIS-macOS-Security)

## DESCRIPTION
This CIS Benchmark rule set is build to use with the macOS Security Compliance Project [here](https://github.com/usnistgov/macos_security)

## Info
While working with CIS Benchmarks PDF (guidelines for scripts and/or Configuration Profiles) I had the feeling there must be a better and faster way. The guys from the macOS Security Compliance Project did an amazing job to automate the guidence, needed scripts, configuration profiles, and remediation script. 

So i started to transform the CIS Benchmark PDF from Big Sur into a custom rules set to integrate with the macOS Security Compliance Project.

## Usage/Requirements
* The CIS Benchmark rules are tested on macOS Big Sur 11.* and the latest macOS Security Compliance Project release.
* Download the macOS Security Compliance Project to your device. 
* Copy the CIS-macOS-Security Custom folder into the macOS Security Compliance Project and overwrite the empty custom folder.
* You can also include the macOS Security Compliance Project into the CIS-macOS-Security folder but remember to git-ignore the macOS Security Compliance Project from the CIS-macOS-Security Compliance Project


### Generate a Baseline
The project provides the following baseline files, located in the /custom/baselines/ folder:

* CIS-Benchmark.yaml
* CIS-Benchmark-L1.yaml
* CIS-Benchmark-L2.yaml

If you want to create your own baseline or modify an existing baseline, the generate-baseline.py found in the scripts folder will generate a {baseline}.yaml file containing all the rules corresponding with the provided tag (baseline). This {baseline}.yaml is required to run the generate-guidance.py script.

Get a list of available tags and you will see the CIS-Benchmark tags as well
```bash
➜  CIS-macOS-Security git:(master) ./scripts/generate_baseline.py -l
```

* 800-171
* 800-53r4_high
* 800-53r4_low
* 800-53r4_moderate
* **CIS-Benchmark**
* **CIS-Benchmark-L1**
* **CIS-Benchmark-L2**
* cnssi-1253
* inherent
* manual
* n_a
* none
* permanent
* stig
* supplemental

**Generate a new baseline**

```bash
➜  CIS-macOS-Security git:(master) ./scripts/generate_baseline.py -k CIS-Benchmark-L1
➜  CIS-macOS-Security git:(master) ls -dn build/baselines/*
-rw-r--r--  1 501  20  6350 Jan 19 13:30 build/baselines/CIS-Benchmark-L1.yaml
```
The generated baseline will be saved into the `build/baselines/`

### Generate CIS Benchmark guidance

To generate the guidance files (AsciiDoc, HTML, PDF, Excel, mobileconfigs, and compliance script) run the `generate-guidance.py` script and point it to either one of the built-in baseline.yaml files or a custom CIS Benchmark baseline.yaml file in the `custom/baselines` folder or created by the `generate-baseline.py` script.

**AsciiDoc, HTML, and PDF**

```bash
./scripts/generate_guidance.py custom/baselines/CIS-Benchmark.yaml
```

**AsciiDoc, HTML, PDF, and Excel**

```bash
./scripts/generate_guidance.py custom/baselines/CIS-Benchmark.yaml -x
```
**AsciiDoc, HTML, PDF, Excel, and mobileconfigs**

```bash
./scripts/generate_guidance.py custom/baselines/CIS-Benchmark.yaml -x -p
```
**AsciiDoc, HTML, PDF, Excel, mobileconfigs, and compliance script**

```bash
./scripts/generate_guidance.py custom/baselines/CIS-Benchmark.yaml -x -p -s
```


```bash
./scripts/generate_guidance.py custom/baselines/CIS-Benchmark.yaml -l /Users/<user>/Git/CIS-macOS-Security/custom/Images/cis_banner.png -p -s -x
```

### Example 
<img src="https://github.com/mvdbent/CIS-macOS-Security/blob/main/example.png" width="770">