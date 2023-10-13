# Privilege Escalation

## Linux Privilege Escalation

Kernel Exploits
SUID/SGID Binaries
Capabilities


## Windows Privilege Escalation

Named Pipes
DLL Injection
Privilege Escalation Tools


# Pivoting Techniques:

## Port Forwarding: Forward traffic from one compromised system to another through SSH, meterpreter, or other tools.

## Tunneling: Set up tunnels (e.g., SSH tunnel, VPN) to route traffic through compromised hosts to access internal network resources.

## Proxychains: Use proxychains to pivot through compromised hosts and access external services as if from the compromised host.

Advanced Techniques:

Data Exfiltration: Find ways to exfiltrate sensitive data from a compromised system, such as through DNS tunneling, covert channels, or encoding data within legitimate traffic.

Payload Obfuscation: Obfuscate payloads to evade detection by security tools, including encoding, encryption, and polymorphic shellcode.

Memory Exploitation: Explore memory exploitation techniques like heap spraying, Return-Oriented Programming (ROP), and Return-to-Libc.

Kernel Exploitation: Gain control over the kernel by exploiting vulnerabilities in the operating system.

DLL Injection: Inject malicious DLLs into legitimate processes to execute arbitrary code.

Named Pipe Exploitation: Exploit named pipes for privilege escalation or lateral movement within Windows systems.

Powershell Exploitation: Use PowerShell for various post-exploitation activities, such as lateral movement, privilege escalation, and data exfiltration.

WMI (Windows Management Instrumentation) Exploitation: Abuse WMI for lateral movement and remote code execution within Windows networks.

DLL Hijacking: Identify and exploit applications that load DLLs without specifying the full path, allowing you to load a malicious DLL.

Kerberos Ticket Attacks: Exploit Kerberos authentication vulnerabilities, such as Pass-the-Ticket (PtT) attacks and Golden Ticket attacks.

Cross-Site Request Forgery (CSRF) with Session Riding: Exploit CSRF vulnerabilities to perform actions on behalf of authenticated users.

XML-based Attacks: Explore various XML-based attacks, including XXE, XSLT Injection, and Entity Expansion attacks.

Cloud-Based Attacks: Learn about AWS, Azure, or GCP-specific attacks, including misconfigurations, privilege escalation, and data exfiltration.

Fuzzing: Use fuzzing techniques to discover vulnerabilities by injecting malformed data into applications or protocols.

Network Protocol Exploitation: Exploit vulnerabilities in network protocols, such as SMB, SNMP, or DNS, for privilege escalation or lateral movement.

WebSockets Exploitation: Investigate WebSocket security issues and potential vulnerabilities in real-time web applications.

Blockchain and Smart Contract Vulnerabilities: Explore security issues related to blockchain technology and smart contracts.