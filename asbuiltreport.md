---
marp: true
theme: asbuiltreport
paginate: true
footer: asbuiltreport.com
title: AsBuiltReport - Document your datacenter with PowerShell
description: Community presentation for the AsBuiltReport open source project
lang: en-GB
---

<!--
HOW TO USE THIS DECK

1. Slides with a yellow "Your slide" bar are yours. Replace their content or delete them.
2. Every slide has a speaker script in a comment like this one. It shows in presenter view
   and is exported to speaker-script.txt by the build. Use it as a starting point and put
   it in your own words.
3. Timings in square brackets add up to about 20 minutes without the optional section.
4. See PRESENTER-GUIDE.md for building, presenting and making the talk your own.
-->

<!-- _class: lead -->
<!-- _paginate: false -->

<div class="brand">
<img src="assets/logos/asbuiltreport-mark-reversed.svg" alt="">
<h1>AsBuiltReport</h1>
</div>

## Document your datacenter with PowerShell

<span class="prompt">PS&gt;</span> `Your Name`, your meetup, date

<!--
[1 min]

Hi everyone, thanks for coming. Tonight I want to show you an open source project called AsBuiltReport.

If you have ever finished an infrastructure project and then lost days writing the as-built document, this talk is for you. By the end you will know what the project is, where it came from, and how to produce your first report in a few minutes.
-->

---

<!-- _class: slot -->

# About me

<div class="cols">
<div>

- Your name and role
- Where you work, or what you work on
- How long you have used PowerShell
- How you came across AsBuiltReport

</div>
<div>

Add a photo, your handle, or your blog address here.

</div>
</div>

<!--
[1 min] PRESENTER SLOT

Introduce yourself in three or four sentences. The most useful thing to share is how you found AsBuiltReport and what you were trying to solve. People remember a story far better than a job title.

Delete this slide if the host has already introduced you.
-->

---

# Nobody enjoys writing the as-built

<div class="cols-3">
<div class="card">

### It is slow

Screenshots, exports and copy and paste from consoles into Word, for every system, on every project.

</div>
<div class="card">

### It is inconsistent

Every engineer has a different template, a different level of detail and a different idea of finished.

</div>
<div class="card">

### It goes stale

The document is out of date the day after handover, so nobody trusts it when they need it.

</div>
</div>

<p class="lede">An as-built should describe what is running today, not what the design said months ago.</p>

<!--
[2 min]

Quick show of hands. Who here has had to write an as-built document? And who enjoyed it?

That is the problem. Writing these documents by hand is slow. You are copying values out of a console into a Word table, one screen at a time.

It is also inconsistent. Give the same environment to three engineers and you get three different documents.

And it goes stale. The moment someone changes a setting, the document is wrong. A lot of teams end up editing the design document and calling it an as-built, which is not the same thing. An as-built should describe what is really there today.
-->

---

# What is AsBuiltReport?

<div class="cols">
<div>

An **open source PowerShell framework** that connects to your infrastructure and writes the as-built document for you.

- Works with any platform that has a PowerShell module or REST API
- Output in **Word, HTML or text**
- Free to use under the MIT licence
- Installs from the PowerShell Gallery

</div>
<div>

<div class="stat">250,000+</div>

downloads from the PowerShell Gallery

<div class="stat">30</div>

modules, covering Microsoft, VMware, Veeam, NetApp, Nutanix, Pure Storage and more

</div>
</div>

<!--
[1.5 min]

So what is AsBuiltReport? It is an open source PowerShell framework that connects to your infrastructure, collects the configuration and writes the document for you.

It works with anything that has a PowerShell module or a REST API. You choose the output, Word, HTML or plain text. It is free, it is MIT licensed, and it installs from the PowerShell Gallery like any other module.

It has been downloaded more than a quarter of a million times, and there are around thirty modules covering vendors like Microsoft, VMware, Veeam, NetApp, Nutanix and Pure Storage.

NOTE FOR PRESENTER: check the current download count and module list on asbuiltreport.com before you present.
-->

---

# Where it came from

<div class="timeline">
<div><b>2017</b>Tim Carman, a consultant in Melbourne, starts a PowerShell script to document VMware vSphere and learn PowerShell along the way.</div>
<div><b>March 2018</b>First public talk at the Melbourne VMUG UserCon. The response is enough to keep going.</div>
<div><b>August 2018</b>Presented with Matt Allford at VMworld US to more than 500 people.</div>
<div><b>Since then</b>Rebuilt as a modular framework, open sourced, and extended by contributors around the world.</div>
</div>

<p class="small" style="margin-top:28px">The document engine is <a href="https://github.com/iainbrighton/PScribo">PScribo</a> by Iain Brighton, which turns PowerShell objects into Word, HTML and text.</p>

<!--
[2 min]

A little history, because I think it matters that this came from a real engineer with a real problem.

In 2017 Tim Carman was a consultant in Melbourne, delivering two or three VMware projects a month, and writing an as-built for each one by hand. He also wanted to learn PowerShell. So he combined the two and started a script to document vSphere.

In March 2018 he gave his first ever talk about it at the Melbourne VMUG conference. In August that year he and Matt Allford presented it at VMworld in Las Vegas to more than five hundred people, and it became one of the most watched sessions of the conference.

After that it was rebuilt as a modular framework so that anyone could write a report for their own technology, and it was open sourced. Much of what exists today comes from community contributors, Jonathan Colon in particular.

One more credit. The engine that produces the documents is PScribo, written by Iain Brighton. AsBuiltReport would not exist without it.
-->

---

# How it works

<div class="flow">
<div class="box"><b>Your systems</b>vCenter, Azure, Active Directory, storage arrays, backup servers</div>
<div class="arrow">&gt;</div>
<div class="box"><b>Report module</b>One per product. Collects the data with the vendor's PowerShell module or API.</div>
<div class="arrow">&gt;</div>
<div class="box key"><b>AsBuiltReport.Core</b>The framework. Same commands, configuration and styling for every report.</div>
<div class="arrow">&gt;</div>
<div class="box"><b>Your document</b>Word, HTML or text, saved to a folder or sent by email</div>
</div>

- **Core module** gives you `New-AsBuiltReport` and the configuration commands
- **Report modules** are separate, so you only install the ones you need
- **Charts and diagrams** come from optional companion modules

<!--
[1.5 min]

Here is how the pieces fit together.

On the left are your systems. On the right is the document you want.

In the middle there are two parts. A report module knows how to talk to one product. There is one for vSphere, one for Active Directory, one for Veeam and so on. It uses the vendor's own PowerShell module or API to collect the data.

The Core module is the framework. It gives you the same commands, the same configuration files and the same styling for every report. Learn it once and every report works the same way.

Because the report modules are separate, you only install the ones you need.
-->

---

# Three commands to a finished report

```powershell
# 1. Install the framework and a report module
Install-Module AsBuiltReport.Microsoft.AD

# 2. Set it up once: your company details and report options
New-AsBuiltConfig
New-AsBuiltReportConfig -Report Microsoft.AD

# 3. Generate the report
New-AsBuiltReport -Report Microsoft.AD -Target dc01.example.com `
    -Credential (Get-Credential) -Format Word, HTML `
    -OutputFolderPath C:\Reports
```

<p class="small">Installing a report module brings in AsBuiltReport.Core automatically. Swap <code>Microsoft.AD</code> for the product you want to document.</p>

<!--
[2 min]

This is everything you need to type.

First, install a report module from the PowerShell Gallery. That pulls in the Core module for you.

Second, set it up. New-AsBuiltConfig asks for your name and company details. New-AsBuiltReportConfig creates a JSON file with the options for that report. You do this once and reuse it.

Third, run New-AsBuiltReport. You tell it which report, which system to connect to, your credentials, the formats you want and where to save them.

That is it. A few minutes later you have a document.

NOTE FOR PRESENTER: change the example to a product your audience uses. If you are doing a live demo, this is a good place to switch to the console.
-->

---

# What you get

<div class="report">
<div class="page">
<div class="t1">Microsoft Active Directory As Built Report</div>
<div class="t2">Example Company</div>
<p style="margin-top:120px;font-size:13px;color:#4A5B78">Author: Your Name<br>Date: 16 November 2026<br>Version: 1.0</p>
</div>
<div class="page">
<h4>1.2 Domain Controllers</h4>
<table>
<tr><th>Name</th><th>Site</th><th>Global Catalog</th><th>Operating System</th></tr>
<tr><td>DC01</td><td>Melbourne</td><td>Yes</td><td>Windows Server 2022</td></tr>
<tr><td>DC02</td><td>Sydney</td><td>Yes</td><td>Windows Server 2022</td></tr>
<tr class="warn"><td>DC03</td><td>Perth</td><td>No</td><td>Windows Server 2016</td></tr>
</table>
<h4>1.3 Health Checks</h4>
<table>
<tr><th>Check</th><th>Result</th></tr>
<tr class="ok"><td>Replication</td><td>No failures</td></tr>
<tr class="warn"><td>Operating system</td><td>1 controller on an older release</td></tr>
<tr class="crit"><td>Time source</td><td>Not configured on DC03</td></tr>
</table>
</div>
</div>

<p class="small" style="margin-top:14px">Illustration only. A cover page, table of contents, numbered sections and tables, with health check findings highlighted in the document.</p>

<!--
[1.5 min]

And this is the kind of thing you get. This slide is an illustration, not a real report, but the structure is accurate.

You get a cover page with your company details, a table of contents, numbered sections and properly formatted tables.

Notice the highlighted rows. Those are health checks. The report does not only list the configuration, it can flag things that deserve attention, such as an unsupported version or a missing setting.

NOTE FOR PRESENTER: if you can, replace this slide with a screenshot of a real report from your own lab, with anything sensitive removed. A real one is always more convincing.
-->

---

# Make it yours

<div class="cols">
<div>

- **Information level** per section, from a summary to full detail
- **Health checks** you can switch on or off individually
- **Styling** to match your company: fonts, colours, cover page, tables
- **Language** support in a growing number of reports
- **Email** the finished report to one or more people

</div>
<div>

```json
{
  "InfoLevel": {
    "Domain": 2,
    "DNS": 1,
    "CA": 0
  },
  "HealthCheck": {
    "Domain": {
      "Backup": true,
      "Security": true
    }
  }
}
```

</div>
</div>

<!--
[2 min]

Consistency is half the story. The other half is that you control what goes into the document.

Each section has an information level. Zero switches it off, one gives you a summary, and higher numbers add more detail. So the same module can produce a ten page overview for a manager or a two hundred page reference for the operations team.

Health checks can be switched on and off individually.

You can apply your own style, so the report comes out with your fonts, your colours and your cover page.

Some reports can be generated in other languages, and you can have the finished report emailed to you.

All of that lives in a JSON file, like the one on the right. Keep it in source control, and every report you run is produced the same way.

NOTE FOR PRESENTER: the JSON is a shortened example. Option names differ between report modules.
-->

---

# Where teams use it

<div class="cols">
<div class="card">

### Project handover

Hand the customer or the operations team an accurate document on the day the project finishes.

</div>
<div class="card">

### Change management

Run a report before and after a change and attach both to the change record.

</div>
</div>
<div class="cols" style="margin-top:24px">
<div class="card">

### Compliance audits

Produce point in time evidence of how systems are configured, on a schedule.

</div>
<div class="card">

### Disaster recovery

Keep a current record of the environment to support recovery planning and runbooks.

</div>
</div>

<!--
[1.5 min]

Where does this fit in day to day work? Four common places.

Project handover is the obvious one. You finish the build, run the report and hand over an accurate document.

Change management. Run it before and after a change and you have evidence of exactly what changed.

Audits. Schedule the report monthly and you have a point in time record of how each system was configured.

And disaster recovery. If you need to rebuild something, a current as-built is one of the first things you will want.

The common thread is that the document is cheap to produce, so you can produce it often.
-->

---

# What it gives you back

<div class="cols-3">
<div>

<div class="stat">Days</div>

of manual documentation reduced to minutes of run time

</div>
<div>

<div class="stat">One</div>

format and structure across every engineer, project and vendor

</div>
<div>

<div class="stat">Today</div>

not last quarter: rerun the report whenever the environment changes

</div>
</div>

<p class="lede" style="margin-top:36px">It will not write your design rationale for you. It records <mark>what is there</mark>, so you can spend your time on why.</p>

<!--
[1 min]

To sum up the benefits. It gives you time back, days of work become minutes. It gives you consistency, the same structure regardless of who ran it. And it gives you accuracy, because the content comes from the live system.

One honest caveat. It does not explain why the environment was designed the way it was. That still needs a person. What it does is take the tedious part away so you can spend your time on the part that needs you.
-->

---

<!-- _class: divider -->
<!-- _paginate: false -->

# <span class="prompt">&gt;</span> Demo

## Your live demo, or your own story

Optional section. Add 10 to 15 minutes.

<!--
PRESENTER SLOT, OPTIONAL

This is where the talk becomes yours. Pick one:

1. A live demo. Generate a report against a lab and open the result. Have a finished report saved in case the demo fails. Never demo against production, and check the report for names and addresses you would not want on a projector.
2. A personal use case. Use the next slide to tell the story of how you use AsBuiltReport.
3. Both, if you have a longer slot.

If you are doing neither, delete this slide and the next one. The core talk still stands on its own.
-->

---

<!-- _class: slot -->

# How I use AsBuiltReport

<div class="cols">
<div>

### The situation

- What you needed to document
- How you did it before

### What changed

- Which report modules you use
- How long it takes now
- What surprised you

</div>
<div>

Add a screenshot of your report, a snippet of your configuration, or a before and after comparison.

</div>
</div>

<!--
[5 to 10 min] PRESENTER SLOT, OPTIONAL

Tell one specific story. A good structure is: the situation, what you tried, what happened, and what you would do differently.

Useful details for the audience: how long it took you to get a first report, which options you changed from the defaults, and anything that did not work as expected. Being honest about the rough edges makes the rest more believable.

Copy this slide if you need more than one.
-->

---

# It is a community project

<div class="cols">
<div>

AsBuiltReport is maintained by volunteers, and some report modules are behind the latest vendor releases. It grows when its users help.

- **Use it**, and report what you find
- **Improve a report** you rely on
- **Write a module** for a product that is missing, starting from the Plaster template
- **Fix the documentation** when something is unclear

</div>
<div>

<div class="card">

### Start here

Contributing guide
`asbuiltreport.com/dev-guide/contributing`

Discussion board
`github.com/orgs/AsBuiltReport/discussions`

</div>

</div>
</div>

<!--
[1.5 min]

One thing to be upfront about. This is a community project, maintained by volunteers in their own time. Some report modules are well maintained and some have fallen behind the latest vendor versions.

So the most useful thing I can ask of you is to get involved. That does not have to mean writing code. Running a report and logging an issue helps. Fixing a typo in the documentation helps.

If you know a product well and there is no report for it, there is a template that scaffolds a new module for you, and a developer guide that walks you through it.

There is also a discussion board on GitHub if you have questions or ideas.
-->

---

# Try it this week

```powershell
Install-Module AsBuiltReport.Core
Find-Module AsBuiltReport.*
```

<div class="cols" style="margin-top:8px">
<div>

- Website and quickstart: **asbuiltreport.com**
- Source code: **github.com/AsBuiltReport**
- Modules: **PowerShell Gallery**

</div>
<div>

1. Pick one system you look after
2. Run a report against a lab or test instance
3. Tell someone what you thought of it

</div>
</div>

<!--
[1 min]

If you take one thing away tonight, try it this week.

Install the Core module, then run Find-Module to see every report that is available. Pick one system you look after, run a report against a lab or a test instance, and see what comes out.

Everything is on asbuiltreport.com, including a quickstart guide that takes about ten minutes.

And if you like it, tell someone. That is how this project has grown from the start.
-->

---

<!-- _class: lead -->
<!-- _paginate: false -->

# Thank you

## Questions?

<span class="prompt">PS&gt;</span> `Your Name`, your contact details

<div class="qr-row">
<div class="qr"><img src="assets/qr/website.svg" alt="QR code for the AsBuiltReport website"><span>asbuiltreport.com</span></div>
<div class="qr"><img src="assets/qr/github.svg" alt="QR code for the AsBuiltReport GitHub organisation"><span>github.com/AsBuiltReport</span></div>
</div>

<!--
[Remaining time]

Thank you. I am happy to take questions.

The QR code on the left takes you to the website, and the one on the right to the project on GitHub. I will leave this slide up while we talk.

COMMON QUESTIONS
- Does it change anything? No. Reports only read configuration.
- Does it need internet access? Only to install the modules. You can save them for offline use.
- Which PowerShell version? Windows PowerShell 5.1 or PowerShell 7. Check each report module's README, as requirements differ.
- Can it document a product that has no module? Yes, if the product has a PowerShell module or an API, you can write a report module for it.
- Is it supported? It is community supported through GitHub issues and discussions.
-->
