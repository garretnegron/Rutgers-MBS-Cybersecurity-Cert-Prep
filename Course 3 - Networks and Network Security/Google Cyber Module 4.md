# Module 4: Security Hardening

## OS Hardening

`Security Hardening` is the process of strengthening a system to reduce its vulnerability and attack surface.

***Operating System (OS)*** is the interface between computer hardware and the user.

`Patch Update` is a software and operating system update that addresses security vulnerabilities within a program or product.

`Baseline Configuration (baseline image)` is a documented set of specs within a system that is used as a basis for future builds, releases, and updates.

`Multi-factor Authentication (MFA)` is a security measure which requires a user to verify their identity in two or more ways to access a system or network.

### Brute Force Attacks

A **trial-and-error** process of discovering private information, most often passwords.

| Type | How it works |
|---|---|
| **Simple brute force** | Guesses username and password combinations until one works |
| **Dictionary attack** | Uses a list of **common passwords** and **stolen credentials** from past breaches |

- **Why "dictionary"?** Attackers originally guessed using real dictionary words, back
  before complex password rules were common.
- Doing it **manually** is slow and tedious, so attackers use **automated tools**.

> **Key idea:** Dictionary attacks work because people reuse passwords and pick common
> ones. A password leaked in one breach can unlock accounts on other sites.

### Virtual Machines (VMs)

**Software versions of physical computers** that run in an isolated environment on a
real machine (the **host**).

**Security benefits:**

- **Isolation:** malicious code runs inside the VM without affecting the host or network
- **Safe malware analysis:** investigate infected machines or run malware in a
  constrained environment
- **Revert or reset:** roll back to a previous state (**snapshot**), or delete the VM
  and replace it with a clean (**pristine**) image after testing
- **Mistake protection:** misused tools damage the VM, not your real system

**Other benefits:**

- Test and explore applications easily
- Switch between multiple VMs on one computer
- Streamlines many security tasks

⚠️ **Risk:** there's a small chance malware can **escape virtualization** and reach the
host machine (called a **VM escape**).

> **Data example:** Cloud servers like AWS EC2 instances are VMs. Data engineers spin
> them up to run Airflow, Spark, or databases, then shut them down or replace them
> from a clean image when done.

### Brute Force Prevention Measures

**1. Hashing & Salting**

- **Hashing:** turns data into a fixed, unique value. It's **one-way**: it can't be
  reversed to get the original password. Systems store the hash, not the password.
- **Salting:** adds **random characters to the password before hashing**, so two users
  with the same password get **different hashes**. This defeats precomputed hash lists
  (**rainbow tables**).

**2. MFA & 2FA**

- **MFA:** verify identity in **two or more** ways; **2FA:** exactly **two** ways.
- Factors combine different categories:
  - **Something you know:** password
  - **Something you have:** one-time password (OTP) sent to phone or email
  - **Something you are:** fingerprint, facial recognition

**3. CAPTCHA & reCAPTCHA**

- **CAPTCHA** = Completely Automated Public Turing test to tell Computers and Humans
  Apart: a simple test that proves you're human, blocking automated guessing.
- **reCAPTCHA:** Google's free CAPTCHA service for protecting websites from bots.

**4. Password Policies**

Standardize good password practices across an organization:
- Complexity requirements
- How often passwords must change
- Whether old passwords can be reused
- **Account lockout** after too many failed login attempts

## Network Security Hardening

### Tasks Performed

1. Firewall rules maintenance
2. Network log analysis
3. Patch updates
4. Server backups

`Network Log Analysis` is the process of examining network logs to ID events of interest.

`Port Filtering` is a firewall function that blocks or allows certain port numbers to limit unwanted communication.

### Key Takeaways: Network Security Devices & Tools

| Device / Tool | Advantages | Disadvantages |
|---|---|---|
| **Firewall** | Allows or blocks traffic based on a set of rules | Can only filter packets using information in the packet **header** |
| **Intrusion Detection System (IDS)** | Detects and **alerts** admins about possible intrusions, attacks, and malicious traffic | Only catches **known attacks** or obvious anomalies; new, sophisticated attacks may slip through. **Doesn't stop** traffic |
| **Intrusion Prevention System (IPS)** | Monitors for intrusions and anomalies and **takes action to stop** them | **Inline**: if it fails, the network-to-internet connection breaks. **False positives** can block legitimate traffic |
| **SIEM** (Security Information and Event Management) | **Collects and analyzes log data** from many machines into one central dashboard | Only **reports** possible issues; doesn't act to stop or prevent them |

**Quick way to remember:**

| Tool | Detects? | Stops? |
|---|---|---|
| Firewall | — | ✅ (by rules) |
| IDS | ✅ | ❌ |
| IPS | ✅ | ✅ |
| SIEM | ✅ (via logs) | ❌ |

## Cloud Security

### Cloud Security Considerations

Organizations choose the cloud for **easy, fast deployment**, **cost savings**, and
**scalability**, but it brings its own security challenges.

#### 1. Identity Access Management (IAM)

Processes and technologies for managing **digital identities** and authorizing what
each user can do with cloud resources.

- ⚠️ Common problem: **loosely configured user roles** let unauthorized users reach
  critical cloud operations.

#### 2. Configuration

Every cloud service needs **precise configuration** to stay secure and compliant.

- Especially critical during **cloud migrations**: every migrated process must be
  configured correctly.
- ⚠️ **Misconfigured cloud services are a frequent cause of breaches.**

#### 3. Attack Surface

Every added service or application brings its own risks and **expands the attack
surface**, which must be offset with more security measures.

- More services can mean more **entry points** for malware, unless the network is
  designed well.
- CSPs often default to secure options and get more scrutiny than typical
  on-premises networks.

#### 4. Zero-Day Attacks

A **zero-day** is an exploit that was **previously unknown**.

- CSPs usually learn of zero-days **before** traditional IT teams do.

- CSPs can **patch hypervisors** and **move workloads** to other VMs so customers
  aren't affected. Tools also exist for OS-level patching.

#### 5. Visibility & Tracking

- On-premises: admins can inspect every packet crossing the network.
- Cloud: visibility comes through **flow logs** and **packet mirroring**, but
  organizations **can't monitor traffic on the CSP's own servers**.
- CSPs pay for **third-party audits** to verify security and find vulnerabilities
  or compliance gaps.

#### 6. Things Change Fast in the Cloud

- CSPs update constantly, and updates can affect security (e.g., connection
  configurations may need changes).
- Organizations often need to **adapt their IT processes** to match the CSP.
- Every extra service adds complexity and needs **security personnel to monitor it**.

> **Data example:** A pipeline's service account should get only the permissions it
> needs (**least privilege**), e.g., read access to one S3 bucket, not admin access.
> A storage bucket accidentally set to **public** is one of the most common cloud
> misconfigurations behind real data leaks.