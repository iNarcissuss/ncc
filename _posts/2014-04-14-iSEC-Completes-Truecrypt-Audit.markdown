---
layout: post
title:  "iSEC Completes TrueCrypt Audit"
date:   2014-04-14 10:00:00
post_author: Tom Ritter
categories: news
related: ["2013/12/23/iSEC-Engages-In-Truecrypt-Audit"]
download_name: Report
download_link: https://opencryptoaudit.org/reports
---

[Is TrueCrypt Audited Yet?](http://istruecryptauditedyet.com/) Yes, in part!

For nearly a decade, tens of millions of users have been trusting the open source encryption software, TrueCrypt. Over the past year, however, revelations about the capabilities of intelligence agencies have shaken the very foundations of much of the cryptography community. Owing to its popularity and widespread use, TrueCrypt has come under intense scrutiny with many openly asking if TrueCrypt could be trusted to function as claimed.

The Open Crypto Audit Project (OCAP) is a new organization that is attempting to answer questions of importance to the cryptography community, including those about trust in TrueCrypt. OCAP began a grassroots campaign to raise money to answer fundamental questions about TrueCrypt. These fundamental goals were identified. First, resolve questions regarding TrueCrypt's license status. Second, produce repeatable, deterministic builds. And third, conduct a public analysis of the code.

As [announced in December 2013](/news/2013/12/23/iSEC-Engages-In-Truecrypt-Audit.html), iSEC Partners (iSEC) worked with the Open Crypto Audit Project on the final goal -- conducting a methodical analysis of TrueCrypt through code review and penetration testing.

In January 2014, iSEC Partners kicked off the engagement to audit the following portions of TrueCrypt: the Windows kernel code, the bootloader, the filesystem driver, and the areas around this code. The scope was kept narrowly focused to avoid stretching resources too thin and ensure that the review conducted was thorough and robust.

The audit conducted by iSEC is now complete and the findings are available now. iSEC did not identify any issues considered "high severity" during this testing. iSEC found no evidence of backdoors or intentional flaws. Several weaknesses and common kernel vulnerabilities were identified, including kernel pointer disclosure, but none of them appeared to present immediate exploitation vectors. All identified findings appeared accidental. Overall, iSEC does think changes can be made to improve code quality and maintainability, and that the build process should be updated to rely on recent tools with trustworthy provenance. In sum, while TrueCrypt does not have the most polished programming style, there is nothing immediately dangerous to report.

Given TrueCrypt's popularity, the entire security industry benefits from knowing more about the software and how secure it is. iSEC believes in the importance of working with organizations like the Open Crypto Audit Project and the [Open Technology Fund](/2013/10/14/open-tech-fund-report-release.html) to support the development and security of technologies that promote trust and security throughout the Internet.

iSEC hopes both the TrueCrypt project and the larger Open Crypto Audit Project continue their work. The security community will benefit from continued review, new versions, and reproducible builds of the software in the future.

iSEC is grateful and honored to have been a part of the TrueCrypt security audit and feels that the analysis was both productive and important. iSEC's full report is now available to the public. It is unchanged save two items: correcting a few late-stage misspellings and redaction of the consultants' phone numbers. It is available at [https://opencryptoaudit.org/reports](https://opencryptoaudit.org/reports).


