--- 

layout: post 

title: Meltdown and Spectre 

description: Security Flaw 

image: assets/images/pic21.jpg 

--- 

In order to better understand these flaws we should first understand speculative execution. Speculative execution is basically an optimization technique where a system tries to predict which calculations to perform in order to complete a task. It tries to accomplish this by performing tasks that may or may not be required. Basically it does a work before it is known by the system if it is required for the task. If the work was not required then the system simply reverts the changes, that occurred in order to the work, and simply ignores the results. This is done to attain more concurrency for a task, provided the system has resources to spare. This basically wastes CPU cycles by performing unnecessary work but is able to perform chain of commands much faster when compared to the alternative, which is to perform them one after the other. [1]  

Although speculative execution is a good thing it does pose an issue for several modern processors including the Intel X86 microprocessors. These processors are hardcoded, for speculative execution, in such a way that they do not check for permissions (of a user, process or application) and can skip commands altogether. Due to this, programs can potentially steal protected information from kernal memory. [1] This kernal memory is generally supposed to be isolated from user programs but in this case (for speculative execution) the program can access information such as passwords or stored files. This is the main principle that both these vulnerabilities utilize. 

<b>Meltdown Vulnerability</b> 

Meltdown Vulnerability has a Common Vulnerabilities and Exposures ID of CVE-2017-5754 [2]. It basically breaks the isolation between user applications and the operating system, which allows an attacker to access important memory like passwords. Luckily there are software patches against Meltdown which should be applied immediately. [3] 
  
<b>Spectre Vulnerability</b> 

The Spectre Vulnerability is a composite of 2 issues that have Common Vulnerabilities and Exposures IDs of CVE-2017-5715 and CVE-2017-5753 [4].  Unlike Meltdown, Spectre breaks the isolation between different applications which in essence allows an attacker to trick another program, into leaking information. Oddly enough if the program is error free and follows recommended safety checks, then it is more prone to this vulnerability. My assumption is that the checks simply provide a larger surface area or more opportunities for the malicious program to trick the error-free victim program. [3] This is an extremely hard issue to exploit and fix but it is possible to prevent specific known Spectre exploits through software patches [3].  

As can be seen, these issues mainly concern entities that rely on cloud infrastructures or offer cloud services like Amazon or Google and it may or may not affect regular users. 

Following are a few FAQ related to these vulnerabilities. Further details can be found [3] here: [3] 

Am I affected by the bug? 
Most certainly, yes. 

Can I detect if someone has exploited Meltdown or Spectre against me? 
Probably not. The exploitation does not leave any traces in traditional log files. 

Can my antivirus detect or block this attack? 
While possible in theory, this is unlikely in practice. Unlike usual malware, Meltdown and Spectre are hard to distinguish from regular benign applications. However, your antivirus may detect malware which uses the attacks by comparing binaries after they become known. 

Is there a workaround/fix? 
There are patches against Meltdown for Linux ( KPTI (formerly KAISER)), Windows, and OS X. There is also work to harden software against future exploitation of Spectre, respectively to patch software after exploitation through Spectre . 

Which systems are affected by Meltdown? 
Desktop, Laptop, and Cloud computers may be affected by Meltdown. More technically, every Intel processor which implements out-of-order execution is potentially affected, which is effectively every processor since 1995 (except Intel Itanium and Intel Atom before 2013). At the moment, it is unclear whether ARM and AMD processors are also affected by Meltdown. 

Which systems are affected by Spectre? 
Almost every system is affected by Spectre: Desktops, Laptops, Cloud Servers, as well as Smartphones. More specifically, all modern processors capable of keeping many instructions in flight are potentially vulnerable. In particular, Intel, AMD, and ARM processors. 

Which cloud providers are affected by Meltdown? 
Cloud providers which use Intel CPUs and Xen PV as virtualization without having patches applied. Furthermore, cloud providers without real hardware virtualization, relying on containers that share one kernel, such as Docker, LXC, or OpenVZ are affected. 

<br  /><b>References</b> 
<br  />[1] Tom McKay and Alex Cranz. "What We Know So Far About Meltdown and Spectre, the Devastating Vulnerabilities in Modern CPUs"; retrieved from https://gizmodo.com/what-we-know-so-far-about-meltdown-and-spectre-the-dev-1821759062 
<br  />[2] CVE-2017-5754 retrieved from http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=2017-5754 
<br  />[3] Meltdown and Spectre. Retrieved from https://meltdownattack.com/#faq-affected 
<br  />[4] CVE-2017-5753 retrieved from http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=2017-5753 