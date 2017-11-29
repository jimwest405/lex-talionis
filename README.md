# lex-talionis
====================================
Repo for a new project that takes various actions based on security information.
----------------------------------------------------------------------------------

lex-talionis is latin for retaliation, but in this case the intention is to not perform any illegal retaliation and the system
be CFAA compliant.  Name is subject to change

The idea for the project is to have a vendor-agnostic API that can read from various security platforms such as NIDS, HIDS,
Syslog, monitoring systems, vulnerability systems, SIEMS, etc, perform different types of parallel actions based on that
information.

For example, a SOC issue known today is that many NIDS, Syslog, WAF, etc type engines can often generate many false-positives
and because it gets logged an Engineer gets deployed to investigate which and very often turns out to be a false-positive which
means potential money and time wasted and less productivity.

One of the actions of lex-talionis is to be able to reduce the false-positive activities by correlating multiple events however,
in a different manner than vendors such as Alienvault, OSSIM, etc do it.  In those systems, it requires the admin to know how and
what triggers are important to the organization in order for things to happen.  In lex-talionis, a core function of the system
would be to receive the event and in real-time query all other data sources within a certain time period for similar events.  If
found, the system would then put a potential positive rating on the event and list the number of places a similar event was 
identified so that the SOC can prioritize investigations and the need to investigate accordingly.

Another default function of lex-talionis would be a scanning and data gathering function regarding the offending attacker IP.  In this
particular function, any and all events triggered from a security device (NIDS, WAF, etc) would trigger a CFAA compliant data
gathering about the offending IP.  This information gathering would tie into sources such as WHOIS, DNS queries, scans.io data,
common crawl, geoIP, etc as well as perform some CFAA compliant scans to find out as much information as possible about the 
offending IP to help the SOC understand who the offender is (is it a customer or vendor?), where it came from, etc and records
the data in the database.  There are methods to provide allowed customer and vendor details in the system, but anything not matched
as allowed in lex-talionis will result in autoblocking rules in the event that the SOC enables this activity.  All of this activity
will be able to be disabled and modularized to enable some functions, but not others.

Another default function, will be to auto-remediate certain events.  For example, if scans.io or websight.io data returns a bad
banner of Apache 2.4, then lex-talionis will immediately remediate the configuration issue so that no engineering time is needed
and the SOC engineers can be more productive.  In the event that nessus ingested data reports a vulnerability fixed by a patch, 
lex-talionis should be able to auto-patch those issues unless disabled.  This will also be modular and configurable about which
actions the system is allowed to auto-perform.

Another default function will be to auto-resolve monitoring alerts.  An example might be where the monitor shows the web service up, but
the webserver is not being displayed.  An event that lex-talionis might take in this case would be to auto-bounce the web server to
resolve the issue again making the SOC and engineers more efficient.

Also, lex-talionis will also be able to take action based on vulnerability data.  For example, if a web application vulnerability
detects a SQL Injection vulnerability on a specific web page, we not only want to be able to flag it for remediation and attempt
to test and double check the vulnerability via lex-talionis, but also write signature on a WAF if one exists to help detect and/
or stop an attack from happening while remediation is occurring in Dev.  Again, fully configurable and modular.

The idea here is not to replace people, but to make them more efficient so that time isn't wasted on mundane activity and can focus
on being proactive as well as help smaller organizations become more secure who maybe can't afford the top end people to get
this done.  This device does NOT replace a SOC or the need for a security budget, but will hopefully enhance the capabilities and
efficiency of those people and budget.

So this is just a high level scoping of a project that has not started yet, but wanted to get the idea down before I forget it.  :)

If you are interested and would like to participate, have additional ideas, concerns, etc, please contact me with an issue
and I will be happy to get back to you.  If you would like a private conversation, please leave me a note on ow to do so in the
issue.

Thanks and happy researching.  

~z
