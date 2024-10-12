---
icon: check
---

# Detection Engineering best practices

Get a big report, hey this is what the threat actor is doing, hey lets write some detections to catch what the bad guys are doing Write a detection in Chronicle, hey figure out how to catch this activity, kick me a tactic, something that is not time sensitive and we ask all of the questions Take next week to figure out what i am doing and introduce me to the rest of team MXDR is a service that clients pay for, stanley runs the MXDR module We test detections with client data, and deploy to client environment Mandiant dropped a report on APT44 - grabbed the report, and asked what TTP's is APT44 using to get access to an enviorment. Based on the detection, we deployed to all of the clients. He will give me a TP that is actually being used, consume all I can about the threat actor, lets see the telemetry I have and the technique Telemetry is the data we get back from our endpoint or our servers, logging is that information or that data SIEM engineering is a garbage in garbage out perspective, we are handcuffed about the quality of data going into our SIEM ETL In Chronicle has a data model similar to Splunk Pentesting is a waste of time and money Too many tools and not enough operators Largely attached to MXDR|

Learn your text editor

Learn to hack a windows box

Learning something enough to solve a problem you have, go as deep as you need depending how much you work in a tool

Extreme volume and silence is not good in detection engineering, SOAR playbooks will automate the playbook you wrote during your detection. There are a couple different outcomes of a detection, true positive, benign, adverse, fp

Detections take many inputs, but a couple should be threat intelligence and incident response.

Put metrics in there place

You should have a deep understand of all the detections in your environment

The standard is this actually going to catch a bad person or show something that is considered abnormal in the environment?

Fine grain controls of metrics are dumb and not needed, it only gives a summary overview of where you are going.

Metrics are like a map, but they are not the actual terrain. Need enough time to tell your story, but also play the game.

Think about people who are only focuse on the numbers but not on the game

Seven categories of things to monitor there is endpoint email network identity, applications, sass, and OT

Have a good grasp on how my client deals with those seven categories you need good telemetry and that’s almost as important as catching the bad guy you have to inventory with assets you have

You also need to understand your threats, maintain a good threat and tell feed what is going on in the world threat reports

Understand where most of your tickets are coming from

Look for tooling the Preludes compromise identify vulnerabilities are running an old OS bad configuration in the network

This process is a long journey, revalidate environment for threats and vulnerabilities

Always go one step further into the details, do home labs, because home labs work the same way the cloud does.

Be tool agnostic

Never be in a situation where you cannot do something if you wanted to. It just may be more effective to have somebody else do it.

Do not specialize but plug holes.

Engineer to do security better

You have to understand what you are defending, and what you are defending from.

Know the left and right of your detections

A lot of things are easier when you run a validation yourself and you learn how to do the hacking yourself.

Chase the gap

Chronicle and Sentinel is the biggest players in the market, best positioned

Sentinel only plays nice with a Microsoft shop

Chronicle is the exact opposite

Logscale and SIAM products are from Crowd strike and Palo Alto's just came out, both are very strong eco system.

XDR VS SIEM is a manner of marketing

You need a place to store data, you need a place to get it into the storage efficiently, then you need to use it (search it), then you need a way to make it actionable in terms of rules engine and correlation.

A tool to perform that function will always exist

Building certain use cases

* What type of telemetry will support this
* Work with the appropriate people to get visibility, this is hard cause visibility costs money
* Logging ethicacy - Within this data source, what kind of event types do I care about in this log source. What events are actually enabled on the endpoints? Do you have the logs you need for event types. Are these logs parsed and usable?
* Then you can get to the use case building
* When it comes to writing the code: Writing it conceptually
* You either have a way of testing through red teaming / pen testing / BAS - When you have this, writing the rules then become easy. Do a ton of CTI research, blog posts, threat research, twitter to build the detection. There is a wealth of knowledge out there from github, in blogs, sometimes it is POC of the exploit, and you can figure out how it works and then try to detect it. Go through a loop on this to build the content. Do not rebuild the wheel, try to save the time. If nobody has, you will be looking through a lot of code. In our space we are not paid to reverse engineer, so time box it. VX underground - bookmark this website and do not download anything

Lets establish visibility first, what is our baseline from a global perspective. What exists that has the broadest coverage, and lets get it in.

Treat a SIEM like 107 different projects

Lets get coverage up and running

Do not forget about laws with data residency or compliance requirements

Localized tenants are happening, Chronicle is not itself available to deploy

Localize countries - Bring things in centrally to a homebase

This changes based on laws coming into play

Regional data lakes that spin off based on client, aggregate as much as possible. Upwards to a SOAR interface

Correlation is very important

Build out rules in the source tool, not everything has to be in the SIEM, use SIEM for correlation

localized market based threat modeling…

There is a ton to be gained on the basics, before jumping to new things

Threats change country to country

Franchising makes things different for a SIEM

Sec-Ops is a SAAS only siem

Schema and read / schema and write

Hybrid operate is the best

Solution delivery is hybrid operate

Service delivery pay bands is lower than traditional

Sharphound performs network enumeration

Look for what happens after you run the command line

Look at the command line - orrrr What is being launched from the rundll library anytime rundll should not be executed. Not one specific things. Generalize is good

EDR can decode base64

Run malware through virus total

Cyberchef

Malware bizarreIt shouIt sh

Hackers are individuals in a collective

They are TTP based, not attack group based.

For example, RansomHub is most likely comprised of different groups as it is new. This means different TTP’s are going to be used.

It is easier to be focused on ransomhub from a marketing perspective.

This is all the case unless an encrypter works a certain way from a threat group.

Attackers are opportunistic, they are trying to target anybody who they can get access to. Better to aim for anybody with X vulnerability than to aim for just one sector. It is more about how you can exploit a vulnerability than anything else.

Never reinvent the wheel

Unmanaged devices are the most common attack vectors

Look for the target device behavior of an attack (port scanning)

#### Detection Engineering:

* Broad detections should be created to avoid myopic or narrow scopes. Broadening scope helps with risk-based alerting and identifying zero-day threats.
* Consider building larger detections instead of multiple smaller ones for better role management (e.g., combining detections for scheduled tasks, suspicious locations, and temp locations).
* Focus on building detections by technique (e.g., persistence mechanisms, PSExec), rather than narrow, single detections.
* The balance between merging rules and avoiding monolithic detections is crucial for effective rule management.

What assets do we have? What are the top threat groups? What are the threat models in our infrastructure? Are there known vulnerabilities in our environment exploited by these groups? Do we have log visibility? How can I cover this in many ways, how would an attacker evade this? Is something already in place? How are we lacking visibility? 7 categories of logs - Endpoints, Email, Network, Identity, SAAS, OT

1. Get a good grasp on how your client deals with these categories: need good telemetry Need a good understanding of asset inventory
2. Understand threats Maintain a threat intel feed of what is going on in the world, have threat reports Where are my tickets coming from?
3. Look for tooling that preludes compromise Identify vulns Are they running old OS, etc Bad configuration in the network? It is a long journey, then you go back to re evaluation

Creating effective alerts requires a strategic and thoughtful approach. Here are key considerations and the frame of mind you should adopt when crafting alerts:

#### 1. **Risk-Based Thinking**

Prioritize alerts based on risk and impact. Focus on potential threats that could cause significant harm to your organization.

* **Ask Yourself:** What are the most critical assets and data in my organization? What threats could severely impact these assets?

#### 2. **Context Awareness**

Include as much context as possible in your alerts. This helps reduce false positives and makes the alerts more actionable.

* **Ask Yourself:** What additional information can I include to help analysts understand the alert quickly? (e.g., user behavior, time of day, historical data)

#### 3. **Specificity and Relevance**

Create alerts that are specific and relevant to your environment. Avoid generic alerts that could apply to any system.

* **Ask Yourself:** Does this alert apply specifically to my organization's infrastructure, software, and threat landscape?

#### 4. **Behavioral Patterns**

Focus on detecting abnormal behavior patterns rather than just signature-based detections.

* **Ask Yourself:** What does normal behavior look like for this system or user? How can I detect deviations from this norm?

#### 5. **Usefulness and Actionability**

Ensure that each alert provides enough information for analysts to take immediate and appropriate action.

* **Ask Yourself:** If I receive this alert, will I have enough information to respond effectively? What steps should be taken next?

#### 6. **Reducing Noise**

Strive to reduce the number of false positives and irrelevant alerts. This helps prevent alert fatigue and ensures that critical alerts are not overlooked.

* **Ask Yourself:** Can I refine the criteria to reduce noise? Are there any known benign activities that I can safely exclude?

#### 7. **Regular Review and Tuning**

Alerts should not be static. Regularly review and tune them based on feedback and changing threat landscapes.

* **Ask Yourself:** How often should I review and adjust my alerts? What feedback am I getting from my security team?

#### 8. **Compliance and Policies**

Ensure alerts align with regulatory compliance requirements and organizational security policies.

* **Ask Yourself:** Do these alerts help me meet compliance requirements? Are they aligned with my organization's security policies and standards?

#### 9. **Collaboration and Feedback**

Involve your security team in the alert creation process and encourage feedback for continuous improvement.

* **Ask Yourself:** Have I consulted with my team to get their input on alert effectiveness? Am I open to modifying alerts based on their feedback?

#### 10. **Automation and Integration**

Leverage automation and integrate alerts with your broader security operations workflow to streamline responses.

* **Ask Yourself:** How can I automate responses to certain alerts? How do these alerts fit into my overall security operations and incident response plans?

#### Mindset Summary:

1. **Risk-Oriented:** Focus on high-impact threats.
2. **Contextual:** Provide detailed, actionable information.
3. **Specific:** Tailor alerts to your environment.
4. **Behavioral:** Look for deviations from the norm.
5. **Actionable:** Ensure alerts lead to clear, feasible actions.
6. **Refined:** Continuously improve and reduce noise.
7. **Compliant:** Align with policies and regulations.
8. **Collaborative:** Incorporate feedback and teamwork.
9. **Automated:** Streamline and integrate alert management.

#### Example of an Effective Alert:

**Ineffective Alert:**

* "New process started on host."

**Effective Alert:**

* "Suspicious process 'powershell.exe' started by non-privileged user 'jdoe' outside of normal working hours (3 AM) on critical server 'Server01'. Previous activity includes failed login attempts and unusual network connections."

**Why It's Effective:**

* **Risk-Oriented:** Focuses on a critical server.
* **Contextual:** Provides detailed information about the process, user, and timing.
* **Specific:** Tailored to unusual behavior and critical assets.
* **Behavioral:** Highlights abnormal activity patterns.
* **Actionable:** Contains enough information for immediate investigation and response.

By adopting this strategic mindset, you can create alerts that are meaningful, reduce noise, and effectively guide your security team's actions.

## Philosophy

Rule development can be hotly debated and there are many ideas for what makes a detection rule _good_. We hear about arguments between _Indicators of Compromise_ vs. _Indicators of Attack_ and _signatures_ vs. _rules_. Instead of boring ourselves with those re-hashed discussions, we want to share our approach for rule writing and our expectations of this repository.

#### The Zen of Security Rules

We incorporate the [Zen of Security Rules](https://zenofsecurity.io/rules) into all of our rule development and planning. We strive to follow these principles to ensure practical rule design for resiliency at scale.

### Approach

Our goal is to improve detection within Elastic Security, while combating alert fatigue. When we create a rule, we often approach it from this perspective. To make sure a rule is a complete and a good candidate for Detection Rules, consider asking these questions:

* Does this rule improve our detection or visibility?
* Does it strike a good balance between true positives, false positives, and false negatives?
* How difficult is it for an attacker to evade the rule?
* Is the rule written with [Elastic Common Schema (ECS)](https://www.elastic.co/guide/en/ecs/current/ecs-reference.html) in mind? Is the logic data source-agnostic or does it depend on specific beats or agents?

#### Behavioral rules

Based on our approach, we tend to prefer rules that are more _behavioral_ in nature. Behavioral rules are rules that focus on the attacker technique, and less on a specific tool or indicator. This might mean more research and effort is needed to figure out how a technique works. By taking this approach, we do a better job detecting and stopping the attacks of today and tomorrow, instead of the attacks of yesterday.

#### Signatures and indicators

Even though we gravitate towards behavioral or technique-based rules, we don't want to automatically disqualify a rule just because it uses indicators of a specific actor or tool. Though those are typically more brittle, they tend to have less noise, because they are specifically written to detect exactly one thing. Sometimes tools are used across multiple actors or red teams, and a signature could go a long way.

One example would be a detection for the common open source tool [mimikatz](http://github.com/gentilkiwi/mimikatz), which is used by many red teams and in real world incidents. It dumps credentials by requesting read access to the `lsass.exe` process and decrypts passwords from memory. This technique is often too low-level for some tools. One way to detect it would be to look for special flags in the command line or inside the file itself, such as `sekurlsa::logonpasswords` or `sekurlsa::wdigest`. Those indicator-based detections are less effective these days, because `mimikatz` mostly runs in memory, so there's no command line or even a file to observe.

A better approach is to focus on the technique: remotely reading memory for `lsass.exe`. Defenders now have tools and solutions that can detect a process requesting memory access to `lsass.exe` and block or defend the behavior natively. One tool, Microsoft Sysmon, has Event ID 10: [ProcessAccess](https://docs.microsoft.com/en-us/sysinternals/downloads/sysmon#event-id-10-processaccess) which can detect the access request to `lsass.exe`. From there, the logic needs to tune out legitimate software that requests access or tune out specific flags from the process access request. Then, you get a detection that doesn't just find `mimikatz`, but can also detect other tools like ProcDump.exe requesting memory access to `lsass.exe`.

### Review questions

There are a few ways that we strive to improve our detection rates and performance when writing rules. We ask a handful of questions while developing or reviewing rules. When contributing, consider this questionnaire:

#### Does the rule detect what it's supposed to?

This probably seems like an obvious question, but is a crucial and regular part of any review for a new rule. Sometimes we work backwards from a specific indicator to a general rule. But when we get there, how do we know that we're detecting other instances of the technique?

Another good reason for asking this question: others may have experience with this type of data. Someone else may be aware of false positives which original author didn't anticipate.

Maybe you're looking for suspicious privilege escalation on Windows by looking for services that spawn with `cmd /c ...` in the command line. This is behavior metasploit does when calling `getsystem`. You might write a rule like this: `process.parent.name: services.exe and process.child.name: cmd.exe`, and it would detect what you expected. But what _else_ did it detect? There are [failure actions](https://docs.microsoft.com/en-us/windows/win32/api/winsvc/ns-winsvc-service\_failure\_actionsw) for services that can run arbitrary commands when a service fails.

Knowing this, there are a few good options to take:

* Try switching to registry events to look for the `binPath` key
* Look for Windows Event Logs for [Event ID 4697](https://www.ultimatewindowssecurity.com/securitylog/encyclopedia/event.aspx?eventid=4697) to detect service creations
* Leave the logic in there. Maybe you're more worried about failure actions also being used maliciously and don't want to risk the false negatives by making the rule more precise

Regardless of the approach you took, document any caveats in the rule's description, false positive notes, or investigation notes. This information helps users to both understand what the rule is trying to detect and will also give good information when triaging an alert.

#### Does a rule have trivial evasions?

We don't want our rules to be trivial to evade. When looking for evasions in a rule, try putting on the hat of the adversary and ask yourself: _How could I perform this action while going undetected by this rule?_

One way that we've seen evasions before is when matching the command line for process events. Those rules can be trivial to evade. For instance, consider the command `wmic process call create whoami.exe`.

If you search for the substring `process call create`, then all an attacker has to do is add a few more spaces: `process  call   create`. Voilà! Undetected.

Maybe the next iteration of the rule tried to avoid whitespace evasions and then opted for `* process *` and `* call *` and `* create *`. But the rule is still easy to evade by quoting the individual args with the command `wmic "process" "call" "create" "whoami.exe"`.

The **ideal** way to write the rule would be to use a parsed command line and not rely on wildcards or regular expressions. Thankfully, [Elastic Common Schema (ECS)](https://www.elastic.co/guide/en/ecs/current/index.html) has the [`process.args`](https://www.elastic.co/guide/en/ecs/current/ecs-process.html#\_process\_field\_details) field which contains exactly this. Then the KQL for the rule is simple: `process.args:(process and call and create)`.

#### The Zen of Security Rules

The Zen of Python does a perfect job succinctly capturing guiding principles for developing via 19 aphorisms. This is the Zen of writing security rules, aimed at fostering high-quality, high-efficacy rules as simply as possible.

1. **Almost all points from the Zen of Python are applicable to security rules - start there**
   * Begin with the principles from the Zen of Python as they provide a solid foundation for rule development.
2. **Favor inclusion-by-exception over exclusion-by-exception, or else endure perpetual whack-a-mole**
   * Include only what is necessary and exclude the rest to avoid endless adjustments and patching.
3. **Have a propensity towards performance; expensive rules must justify the cost**
   * Focus on creating efficient rules. If a rule is resource-intensive, it must offer significant security benefits.
4. **Resist temptation to over or under-scoping; balance is key**
   * Avoid making rules too broad or too narrow; aim for a balanced scope that effectively captures threats without overwhelming the system.
5. **Generic patterns can minimize brittleness, but at the cost of performance**
   * Using general patterns can make rules more robust but might impact performance. Balance is crucial.
6. **Correlation is powerful, but overly comprehensive rules can lead to brittleness and trivial bypasses**
   * While correlating multiple data points is effective, overly complex rules can become fragile and easier to bypass.
7. **Detect behaviors over IOCs, except when necessary**
   * Focus on identifying malicious behaviors rather than just indicators of compromise (IOCs), unless IOCs are the best option.
8. **If a rule is too complex to understand, the alert is even worse**
   * Complexity in rules makes understanding and responding to alerts more difficult. Keep rules understandable.
9. **Just like code, readability is important for avoiding errors**
   * Clear and readable rules reduce the likelihood of mistakes and make maintenance easier.
10. **Detection logic formatting should emphasize logical precedence and grouping**
    * Structure detection logic to clearly show the order and grouping of operations, enhancing clarity and effectiveness.
11. **Detection logic should be resilient, but when it can’t, use multiple rules**
    * Design rules to handle variations, and if that’s not possible, use several rules to cover different scenarios.
12. **Consistency in rule structure leads to predictability and fewer errors**
    * Maintain a consistent structure in your rules to promote reliability and minimize errors.
13. **If you can detect it, you can test it**
    * Ensure that any detectable condition can also be tested to verify rule effectiveness.
14. **Always version your rules**
    * Keep track of rule versions to manage changes and understand rule history.
15. **Maintenance cost of a rule should not outweigh the value of the rule**
    * Ensure that the effort required to maintain a rule is justified by its security value.
16. **There will ALWAYS be surprises from FPs and FNs**
    * False positives (FPs) and false negatives (FNs) are inevitable. Plan for unexpected outcomes.
17. **Minimizing FPs sometimes outweighs eliminating FNs, due to the costs of alert fatigue**
    * Reducing false positives can be more critical than eliminating false negatives to avoid overwhelming the team with unnecessary alerts.
18. **Less is more; don’t write rules for the sake of writing rules**
    * Focus on creating effective rules rather than increasing the rule count.
19. **There is no “correct” quantity of total rules, but there can be too many and too few**
    * Aim for the right balance in the number of rules. Both extremes can be detrimental.
20. **When necessary, break the rules, so you don’t break the rules**
    * Be flexible and willing to deviate from guidelines when strictly following them would cause more harm than good.
21. **Production environments vary wildly, so minimize assumptions**
    * Assume minimal specifics about the production environment to ensure rules are broadly applicable.
22. **Adopt a detections-as-code or similar software-driven process for managing rules early**
    * Use a systematic, software-driven approach to manage and update security rules efficiently.

These statements are about the complexities and realities of maintaining security. Let's break them down:

1. **Security efficacy has diminishing value, at some point, as rule quantity grows**
   * Adding more security rules initially improves security but eventually leads to diminishing returns, where additional rules do not significantly enhance protection and might even complicate management.
2. **Rule count is not an absolute measure of successful coverage**
   * The number of security rules does not necessarily indicate how well you are protected. Quality and relevance of rules matter more than sheer quantity.
3. **Coverage is not an absolute measure of security**
   * Even if you have extensive coverage (i.e., many security measures in place), it doesn't guarantee complete security. Gaps and unforeseen vulnerabilities can still exist.
4. **Alert count has an inverse relationship with their manageability**
   * The more security alerts generated, the harder it is to manage them effectively. High volumes of alerts can overwhelm security teams and lead to missed threats.
5. **Threats are not static**
   * Security threats are constantly evolving, meaning that what was secure yesterday might not be secure today. Vigilance and adaptation are necessary.
6. **Security posture is temporal and so only instantaneously representative**
   * A system's security status is only accurate at a specific moment in time. Continuous monitoring and updating are essential because new threats can emerge at any time.

In simpler terms:

1. Adding too many security rules can become counterproductive.
2. The number of rules doesn’t equal good security.
3. Even extensive security measures can miss something.
4. Too many alerts can make it hard to spot real threats.
5. Threats keep changing, so security must adapt.
6. Security status changes constantly, so it needs ongoing attention.

#### 1. Balance efficiency with enough specificity to minimize false positives

The ultimate goal of any Splunk query is to search and present data in order to answer some question(s). There are many right ways to search in Splunk, but there are often far fewer best ways (yes, multiple bests, see next sentence). Before formulating a search query, a couple considerations should be weighed and prioritized, such as accuracy, efficiency, clarity, integrity, and duration. It is easy to get spoiled by simply doing wildcard searches, but also just as easy to unnecessarily bog down a search with superfluous key value mappings. An over reliance of either can lead to problems.

**Accuracy** - are there multiple sources which can answer the question? If so, which is more reliable and authoritative? More importantly, how important is it to reduce or eliminate false positives from your results? There is a heavy inverse correlation between accuracy and efficiency.

**Clarity** - filtering down to the most relevant information needed to answer the question is only half of the battle –you still need to interpret it. It may be fine to view the results as raw data if there are only one or two results of non-complex data, but when there are rows of deeply structured data, taking the time to present it in the most appropriate manner will go a long way.

**Duration** - the length required for the query to complete. Is this a search that will be run often, and so delays are additive and add to total inefficiency; is there an urgent need to answer something ASAP; is a longer duration eating up resources on other running functions on the search head? Sometimes it is necessary to break a search into smaller sub-searches or to target smaller sets of data and then pivot from there.

**Efficiency** - closely tied to duration, an inefficient query will lead to unnecessary delays, excessive resource consumption, and could even affect the integrity of the data (pay close attention to implicit limitations of results on certain commands!). Paying attention to efficiency is especially important if there are per-user limitations on number of searches, memory usage, or other constraints.Too many explicitly defined wildcard placeholders could become very expensive, and the [atomicity](https://en.wikipedia.org/wiki/Linearizability) of a formulated query should always be considered.

**Integrity** - will you be manipulating any data as part of your search? If so, understand the risks to compromising the integrity of your results in doing so. The more pivots made on returned data, the more susceptible to loss of integrity the search becomes.

#### 2. Make it readable

Write queries in a consistent and clear manner. Sometimes it is better to have a query take up many additional lines for 3. the sake of better readability. Breaking into newlines on pipes is the defacto standard for readability purposes, as 4. can be seen below.

```sql
event_simpleName IN (SyntheticProcessRollup2, ProcessRollup2) ImageFileName="*Windows\\\System32\\\\regsvr32.exe" CommandLine="*/i:http*" AND ParentCommandLine="*scrobj.dll*"
| rex field=CommandLine "/i:(?<sct_file_tmp>\S+)"
| eval sct_file=replace(sct_file_tmp, ":", "[:]")
| eval ParentProcess=ImageFileName
| eval ParentCLI=CommandLine
| eval ParentUser=UserName
| rename TargetProcessId_decimal AS ParentProcessId_decimal
| join ParentProcessId_decimal
	[search event_simpleName IN (SyntheticProcessRollup, ProcessRollup2)
	| eval ChildProcess=ImageFileName
	| eval ChildCLI=CommandLine
	| eval ChildUser=UserName]
| table _time ParentUser ParentCLI ChildProcess ChildCLI sct_file
view raw2.Make-it-readable.py hosted with ❤ by GitHub

```

SQL

#### 3. Make it extensible

Queries should be written in such a way that other people can modify it for their own adaptations or to update or expand a current one. Some ways to accomplish this would be using obvious variable names, readability, or even leaving in inexpensive functionality or variables which can be used for other purposes.

#### 4. Make it modular

Modularity will lead to extensibility, maintainability, and resiliency. This will also increase efficiency as code reuse will be much simpler.

#### 5. Make it feasible

If the query is written for the purpose of manual sifting and analysis, then 50k results is not very reasonable. However, if it is for stateful preservation, [alerts](http://docs.splunk.com/Documentation/Splunk/7.1.1/Alert/Aboutalerts), or [lookups](http://docs.splunk.com/Documentation/Splunk/7.1.1/Knowledge/Aboutlookupsandfieldactions), then that is more acceptable. Incorporating pivots on the information with subsearches and filtering or even, if necessary, breaking it up in to multiple different queries will make managing the results a surmountable task.

#### 6. Make it resilient

The data can change and so can the SPL itself (or even custom commands if used), so writing queries that are less effected by potential changes is important, especially if the effects of the changes are not obvious, which could lead to a loss of integrity in the results. (This is where testing is also important)

#### 7. Make it consistent

Having a style guide may seem like overkill, but if your operation is highly dependent on maintaining a repository of queries, it can go a long way. Naming conventions, spacing, line breaks, use of quotations, ordering, and style are some of the things to standardize to help with consistency.

#### 8. Make it identifiable

Something as simple as:

```sql
 | eval queryID=wxp-110

```

SQL

This ID can then be printed out with the results if needed or purely used as a means to categorize and quickly identify. Naming conventions should be obvious or recognizable (wxp = Windows XP, query 110), or even mappable to the repository itself.

#### 9. Make it noob friendly

This is obviously highly dependent on your usage and organizational structure, however, it never hurts to keep queries as simple as can be, since there is always the chance that someone else will need to maintain or interpret them. Bonus\* less time needing to train people on their purpose!

#### 10. RTFM!

I am a huge proponent of RTFM (F!=field, btw) for both myself and others. Splunk has put a lot of effort into meticulous documentation, which is clearly reflected in the detailed and thorough documentation. With regards to writing SPL queries, the [search reference](http://docs.splunk.com/Documentation/Splunk/7.1.1/SearchReference/WhatsInThisManual) is your absolute best friend!

#### 11. Know your data

The first two things that I tell anyone to do that is new to Splunk is to familiarize yourself with the syntax of SPL (#10) and just as importantly, to get to know how the data is structured. The simplest way to do this is to do a wildcard search (\*) and start reviewing the raw results under the events tab. The data will usually be structure in XML or JSON. Initially, it will be less important to know which data was structured from [indexing](http://docs.splunk.com/Documentation/Splunk/7.1.1/Indexer/Howindexingworks), [field extractions](http://docs.splunk.com/Documentation/Splunk/7.1.1/Knowledge/ExtractfieldsinteractivelywithIFX), or other [transforms](http://docs.splunk.com/Documentation/SplunkCloud/latest/Knowledge/Configureadvancedextractionswithfieldtransforms), but may become important with more advanced searches.

#### 12.Test it

Do not ever merge a query into production ops, bless off on it, trust it, or whatever it is you do to give it legitimacy without first testing and confirmation of positive results. Regardless of how simple the query is, you can never guarantee that some other confounding issue isn’t occurring. If it is a matter of missing the applicable data, well then, Try Harder! There are many great products out there to help with this at scale, such as Red Canary’s [atomic red team](https://github.com/redcanaryco/atomic-red-team) or Mitre’s [caldera](https://github.com/mitre/caldera).

#### 13. Build it out piecemeal

It can get stressful spending a lot of time on a query, only for it to not return the correct or any results, regardless of tweaking. The best way to build complex queries is to build them in pieces, testing as you go along. This is especially convenient because you can point to available data for the sake of testing to ensure positive results, and then change it as it is built out.

```sql
# ensure you have data for the computer
host=ComputerA

# ensure you have data being parsed from that computer to the CommandLine field
host=ComputerA CommandLine=*

# search for all occurences of python in command line activity for the computer
host=ComputerA CommandLine="*python*"

...

#search for all systems where powershell spawned a python program in which 3 or more parameters are passed
host=* ParentProcess="powershell.exe" process="python.exe"
| rex field=CommandLine "(\s-{1,2})(?<flags>\S+)" max_match=0
| stats count values(flags) by host
| where count>3
| sort 0 host

```

SQL

#### 14. Implement version control

The necessity of this is really dependent on the amount of queries and modifications, though it makes sense even for small quantities. This can be accomplished as simply as baking a version into the query itself, such as from #8 with revisions tacked on with periods (wxp-110.3) or even in its own field: | eval version=3 Even better than that would be to maintain them in a database or repository such as GitHub, which gives the added benefit of stateful change representations. It is also possible to save searches directly in Splunk, the version control is less intuitive in this way.

#### 15. Maintain multiple versions of the same thing

This doesn’t just apply to older versions of the same query, but queries which may search the same thing but present it in a different manner, search a different data set, or search a different time window.

#### 16. Don’t reinvent the wheel

It is all too easy to blow a full 12 hour shift perfecting a query, which may not even end up working at all. While it is important to have these search queries catered to your specific need, it is not always necessary to MacGyver it alone. There are lots of great resources available to borrow ideas or techniques from, such as the Splunk blogs and forums, or you can even work with a co-worker.

#### 17. Don’t depend on the wheel

Counter to #16, you do not want to become over reliant on searching for help, as this could lead to running queries which may not be working as you think they are. This could also potentially compromise the integrity of the results. Worse yet, it could be an inefficient way of doing something which has caught on and persisted through the forums.

#### 18. Share it

If you have written a gem or come up with a novel approach to something, share it back with the community. Even if the data set is different, there may still be much which can be gleaned from it. It also helps to drive conversations which benefit the community as a whole.

#### 19. Save it

This is such an obvious one, but in spite of that, I still constantly find myself rewriting queries that I had previously written over and over again…

#### 20. REGEX!

I don’t know why I have this all the way down at #20, because this is easily one of the most powerful and important concepts for which to be able to pivot on results with. There are several commands where regex is able to be leveraged, but the two most significant are [regex](https://docs.splunk.com/Documentation/Splunk/7.1.1/SearchReference/Regex) and [rex](https://docs.splunk.com/Documentation/Splunk/7.1.1/SearchReference/Rex).

Regex does exactly what it says –allows you to filter on respective fields (or \_raw) using regex, which in Splunk is a [slimmed down version](https://docs.splunk.com/Documentation/Splunk/7.1.1/Knowledge/AboutSplunkregularexpressions) of PCRE. The rex command is much more powerful, in that it allows you to create fields based on the parsed data, which can then be used to pivot your searches on. You can even build it as a [multivalued](https://docs.splunk.com/Documentation/Splunk/7.1.1/Search/Parsemultivaluefields) field if more than one match occurs. An example of the rex command (and potentially more than one value) can be seen in the example from #13.

#### 21. Know when its better to go beyond just using a search with SPL

Finally, we made it all the way to #21! Sometimes, depending on circumstance, function, and operational usage, manual searching with SPL queries is just not the best answer. Splunk has a lot of other functionality which can accomplish many of the same things, with less manual requirements. Alerts, scheduled reports, dashboards, and any of a number of apps built within or against the API allow for almost limitless capability. If you are struggling to maintain or achieve some of the topics annotated here, it may mean it is time to explore some of these alternative options.

#### Final Thoughts

This is certainly not an all inclusive list, as there are many more practices which can apply here. Ultimately, it depends on the specific deployment, implementation, and usage of Splunk which should dictate exactly how you create and maintain search queries. This was also not meant to go too deep in the weeds on generating advanced queries (though that may come in the future), but rather a high level approach to maintaining quality and standards. There are many other people who are far more experienced and with much greater Splunk-fu out there, so if you have any input or insight, please feel free to reach out.

_originally posted on a previous blog of mine_

### Detection Analyst, Cybersecurity (Active)

\-Learning how to understand what a hacker does, and the attacker life cycle is crucial to understanding how to be a good detection engineer. We want to be able to distinguish normal user behavior vs an attackers behavior.

\-Limit false alarms by connecting behaviors, like the Cyber Kill Chain. A normal user might use "whoami", but an attacker may use it with other command line process's that declare it malicious.

\-Learn how to read tool documentation very well!

A detection engineer needs to understand the underlying infrastructure of where the logs are being collected, just like a mechanic knows how a car works

Analytic stories are better than 1 to 1 detections, attack chaining

Use the Palntir ADS

* The Defenders dilemma o This is not true
* We have a first move advantage as Defenders, we set up the board, we control the rules, we create the circumstances in which the threat actors are supposed to do their work.
* We set the pace, style and tone of the entire engagement. Before the threat actors begin their attack.
* The Defenders dilemma hurts security
* Wrong promise, bad decisions, wasted resources, demoralized defenders, bad security outcomes.
* Attacks are not point in time
* Attacks are points over time
* A phish or an exploit is only a foothold
* We can detect at almost every stage
* Investigate to cover all stages
* Interdict before they reach the final stage
* Since there are multiple points at any phase of the attack, we have the advantage, because there are multiple points where we can interdict, and force the threat actors to waste their time. If we have robust Detections in place.
* Attackers have to get it right through their entire attack (defense evasion) Defenders only need to detect them once. Before we can get on their trail, and prevent them from causing damage.
* This is now the attackers dilemma
* What can we do to stack the odds in our behavior?
* Nail the basics, eat your cyber veggies. Essentially basic security controls. Software updates, multi-factor authentication, good application security, awareness, networking monitoring.
* This is our equivalent to setting up the board.
* The pyramid of pain - practice offensive defense Resilient systems are much more difficult to manipulate
* https://bit.ly/PyramidOfPain Represents one type of IOC that can be used to detect bad guys are the network. The bottom represents very volatile sources of 10C's Proactive threat hunting TTP's are at the top of the environment (Behaviors), does not have to be MITRE
* We track threat actors by their behaviors, that they are known to exhibit. This then forces the Attacker to retrain and do things different, waste time.
* Resilient means defenders networks are more resistant to threat actor poking
* The goal is to make the attackers incur costs by making it harder for the attacker to operate, we pay for things, why shouldn't they?
* There is no such thing as cheating for the blue team.
* Deception tech makes it quite easy to lie and cheat at scale. Attackers have needs, goals, and habits, take advantage of them (Honeypot) There is also more deception technologies that are being used. Look for places in your organization where we can cheat. Every time you get a phish, put in fake credentials. Alert when somebody tries to use them. Introduce uncertainty on the threat actor part, because they waste a lot of time, give us more time to notice things.

Shaping behavior

A disadvantage mindset starts us off the wrong foot, leads to burnout and bad security outcomes.

For best defense, exploit the many opportunities we have based on our first move advantage.

Both sides influence the others behavior, it is up to us to drive attackers into behaviors which are beneficial to us.

* detections with a fp less than 50%, result in a collective 80% precision
* Respects our SLA's and helps out the SOC team to do what they need to do.
* Output that is easy to read, they do not need to find correlated alerts.
* Analyst SLA is improving

1. Go through soluble security essentials and see your inventory
2. Look across the blind spots, bring data into it
3. CIM / Assets and Identities framework Security is always evolving, need to set check points along the way to see if we are doing things accurately.

* You cannot consistently build and keep detections fresh and relevant.
* String or story of behaviors that we can build a story around
* Risk score is confidence \* impact / 100
* Version detection coming soon in ES
* They usually start out building using the ESCU content, then modify them to their own. That would be more advanced level.
* Build a program that honors the SOC analyst
* To get the value out of RBA, you need to enable as many detections as you can.
* 100-300 detections
* Run various time ranges on the risk index, because attacks run over a day, week, month
* Identify the champion of RBA in your organization. That champion to rally some people together to see if it is feasible.
* Put together an advisory committee, this gets the ball rolling and gets people bought in. Go to the RBA slack channel Monthly office hours
* ES 8.0 - Building a RIR without using SPL. Automatically merge related notables for the same entity. Entity risk score algorithm, much more robust.

Detections do not need to be perfect

* Be engaged with the community, run ideas past people.
* Create multi dimensional risk scores using eval statements
* If it is allowed, risk score is higher than if it is blocked.
* Create a macro so you can apply to multiple search's.
* We can reduce risk score, or multiply by zero for validation or something.
* Manual risk score takes precedence over adaptive risk analysis score.
* Outpost security slack channel
* Apply weighted score to techniques
* Use cases with multiple TTP's take the max weight
* These things are specific to our environment
* Use case scoring, PIl involved, FP rate, detection confidence, use case weight
* Use case weight + MITRE ATTACK
* https://github.com/matt-snyder-stuff/.conf2024
* Alert velocity
* Weigh risk by volume - using a case statement
* (Usecase. weight+mitreweight) \*volume
* Mercy rule for risk score, nothing should have commas.
* Learning from the past, track alert disposition. Dynamically adjust risk scores
* Weigh risk score by disposition. Apply real time risk reduction or increases.
* Want to keep risk scores fresh and up to date
* All these things are being refreshed in the environment
* https://wakelet.com
* Start something, start small, test, get creative
* Splunks new scoring algorithm
* We currently add scores by just adding events together.
* Source type and mitre variety
* New entity risk score breakdown
* What TTP's are we most concerned about as an organization? What adversaries do we care about? What components are most specific to our environment?
* Apply these things to the Risk Incident Rule and Risk Rule
* Build a QA rule for this if you want to implement it? Take a risk score from the signature, plugin macro adjusting score by fp dynamically based on volume and fp rate
* SIEMS do not look far back in time
* Most IOC's are only discovered after somebody has been discovered. Sometimes after 18 months. So we have to look back two years.
* How long have they been here?
* Low and slow attackers, these are the advanced APT's.
* How can we identify a threat over a long time range without expensive search's.
* Two years at minimum for most of us.
* Move data up or down using summary indexing.
* Summary indexing is a scheduled search that collects its results into a new index
* Review summary indexing at previous conference talks
* Preprocessing before doing ML
* Satoshi Kawasaki .conf19
* Instead of having 100,000 logs for ip x talking to y, you have one ip event that will say this ip takes to this address for 100,000 logs
* Summary indexing pulls data from data model
* Use summary indexing to build and deploy machine learning models without using a giant dataset.
* How to continually update models? Feature engineering, of all the fields, what is the most important.
* To have a model, you need an interesting relationship between two fields.
* MLis not as solid as insider knowledge
* I do not care about description field in windows logs
* Unusual traffic by \_time)
* IP internal to new unusual Dest IP external
* Source IP to new unusual Dest IP internal (lateral movement)
* We do not have to completely depend on external threat feeds
* Have we looked into summary indexing to use ML?
* Do not have to accelerate your data, it is faster than a stats search
* Lame creations GitHub and youtube
* CIM covers the 80/20 rule
* Lockheed has over 300 index's
* They use summary index's to open up time scales, they use it for anomalies and historical reviews for the investigation team.
* Make detections to run against the summary index's
* Map the data sources to the summary index, so these detections do not need to change.
* Reduce the need for join and append
* Resilient to change, reducing impact of software changes,
* Detections are based on category, not software.
* Create a scheduled report
* Running a search on the data model that pulls from the summary index
* Use index time instead of time for proper data collection
* A well planned data architecture in Splunk, reduces rework and enhances ability to adapt to changes.
* Think about data from a categorical perspective
* Leverage data models and summary index's
* Write search's and detections against those index's
* Be aware of the different layers
* Really difficult to use git with Splunk
* Comment blocks at the bottom of code
* You can write search's against the comment block when it is standardized : Everything gets a change log
* Study threats, how are people getting compromised
* Build datasets, then from these datasets they build detections.
* How do you know your detections work against Attack x in your environment
* You need detection engineering because you have custom needs for your environment
* Detection lifecycle

1. Requirements
2. Design
3. Development
4. Monitoring
5. Continuous testing

Detection development vs Detection maintenance

Continuous testing

What are the highest value detections so we are not wasting resources

Requirements

* Threat modeling
* Adversary simulation
* Threat intelligence

Ways and motivations to build detections

Design and development

* Data availability
* Detection strategy - behavior, anomaly, ioc
* Resilience - How would you bypass this? Always ask this question. How would they perform obfuscation? What is the weakness of the detection?

Types of testing

* True positive test
* False positive test
* Peer review

Monitoring - KPI's

* Precision
* Noisiness
* Recall
* Durability - only to detect a vulnerability on a system for two weeks, then a patch is released.
* Data source coverage

Continuous testing is very important

We need to review our Detections to make sure they are valuable, this makes sure we are being efficient with our resources. Peer review

Understand the threat coverage of your existing tools

Invest time and effort to detect threats which cannot be detected from your existing tools

Improve resilience by detecting threats in multiple ways

Invest time to optimize the detection engineering cycle

Quick note - community resources is the most important thing for ideas

Here’s a more organized summary of your use case development runbook:

Research detections online, and ways to obfuscate

Build a live wire

1. **Alignment**: Check if the use case ties back to the client’s missions and values.
2. **Relevance**: Ensure the use case makes sense and is relevant.
3. **MITRE / Magma Mapping**: Identify how adversaries execute the attack and the detection methods used. Map the use case to MITRE TTPs. Add to Magma
4. **Existing Use Cases**: Check if there’s an existing use case or gap remediation ticket.
5. **Palantir ADS**: Build out a Palantir ADS if applicable.
6. **Log Inventory**: Review available logs to see if they cover the use case.
7. **Detection Research**: Understand the detection process from alert to resolution.
8. **Detection Development**: Build the detection using Magma and check for existing Sigma rules.
9. **Peer Review**: Conduct a peer review of the detection.
10. **Obfuscation Considerations**: Analyze how an attacker might evade detection and document findings.
11. Is there an Attack Script for this detection for validation?
12. **Documentation**: Document the use case in Fortinet, SOAR, and update build tasks notes.
13. **Use Case Mapping**: Map use cases to threat actor groups, MITRE TTPs, and identify gaps based on threat models.
14. Continuous validation
15. Does EDR cover? Check if we have gap remediation tickets open for this as well.

**Additional Notes:**

* Build an attacker timeline.
* Explore alternative detection methods and whether the use case covers multiple techniques.
* Consider how the receiving host perceives the attack.
* Review threat hunts, CTI vulnerability prioritizations, and current hacker activities.
* Check if current assets could be exploited and ensure CTI prioritizations are considered.
* Assess if any existing detections are in place or if actions are being blocked based on CTI.
* Identify prevalent attacking groups and review incident history in the environment.
* Conduct MITRE research on threat actors and do additional research as needed.

Let me know if you need further adjustments or additional details!

Detection FYI / Snapattack (How can I be efficent in my building process) 80/20

Command line param / hash / broad

Map technique, capability abstraction, review atomic red team scripts

* How do you build use cases that do not get evaded? For example the use of Psexec on the command line?
* What is your view on the group of detections?
* How do you know when alerts are not coming in through the EDR? And how to be better than the EDR?
* Get maturity paper from Stanley
* After going through the process of understanding log sources, vulnerabilities, etc. When you actually start building a detection, what is your process?
* How to work with CTI / TH on use cases. What is the ideal process flow?

MXDR has a foundational content package

* Make the rule more technique focused, and squishing them together
* Drop the rule you are working on in the spreadsheet

Detection Engineering should be a fly on the wall for all conversations. SOC is an input, threat intel is an input (Threat model, we need coverage for this this and this), ASM(Red teaming), see slide 7 in the DE PPT. Incident Response is one of the best repositories for Detections (Think live wire, it map, timeline) follow the attack path. DE gets along with everybody else. You want to end up and facilitate a conversation with as many people as you can. Come hang out with weekly syncs for other teams, hang out there. Most people do not think this is relative to detection engineering, so then they can get a feel for than doing it. It is always your life to figure out the next thing you are writing detections for. DE is actually refined threat hunting. Marine spraying, vs Sniper taking real shots.

Does Sutter have in house applications (SAAS), cloud telemetry, containers, almost zero monitoring of wl on your machine, vast majority does not happening on the endpoint, get to other things, where is the work stored, get there.

Get to the place where real work happens, endpoint is the lowest denomenator (not the only thing). Do not compete the with endpoint, what is the endpoint not looking at. There are pieces of things that are non-endpoint that you can do work on. PSExec is super endpoint focused. Leverage the endpoint to do more than the endpoint cannot do. You look for anomalies, not evil, you look for things that are weird. You do not know all the evil things in the world. Acceptable Use could be a wholenother list you can use. Anomalous activity. My value is not just be in catching bad guys, but just make sure you have good hygiene and good things. Also do these things too, not just fix the problems that you already have.

Prevent your client from doing stupid things. (Exceptions to MFA accounts). Hey I know we did XYZ do you think we could spin a detection

How can we get a better picture of the current environment of Sutter, Crown Jewels, top applications to protect, top websites to protect, what are things tools we currently do not have coverage for. Do we receive logs for those tools.

What are the list of servers we have in our environment? WHat are their hostnames? Sit in on other team calls and hear out what is happening. What are other teams seeing in the wild? Take initiative... What are other teams doing? What is their perspective on things? When a command line process is executing, what is happening at the network layer? What is happening besides what is seen on the endpoint. Many times other teams are not even thinking about the detection engineers. The detection team should be in all conversations. Each call ask them if they have seen anything interesting.

Take initiative.

Be so good they cannot ignore you, do you, be you. But swing for the fences.

SOC feedback loop

Metrics catalog into Splunk

Having some sort of assets and identities table in any SIEM is insanely important to risk and prisonization of assets
