---
title: "Solutions"
date: 2021-10-27T16:49:27+06:00
# meta keywords
keywords: ["Universal UI", "Universal Serialization", "Universal Culture"]
# meta description
description: "This is meta description"
# save as draft
draft: false
---

# Universal UI

Universal UI is the world first **Omni-Media** interactive content development platform.
This technology is enabled by *Content* and *Flow* APIs that allow dynamic contents to be designed 
for any arbitrary target media, and cross-platform compilation technology that allows the 
solution to be ported on any desired device.

{{< image src="images/solutions/universal-ui.png" caption="Universal UI at a Glance" height="300" width="500" position="center" command="fit" option="q100" class="img-fluid" webp="true" >}}


## UUI Framework

Universal UI framework consists of two major components:

* **Content DSL** -- A domain-specific language that can be used to compose layouts, graphical,
  and textual content for any device. Conceptually, it is very similar to HTML+CSS.
* **Flow API** -- An asynchronous reactive way of adding dynamic behavior to content and handing
  events. 

{{< image src="images/solutions/universal-ui-apis.png" caption="Content DSL and Flow API" height="300" width="" position="center" command="fit" option="q100" class="img-fluid" webp="true" >}}


## Comparison

Universal UI is the leads the industry in portability. 
Here how it fairs against competing technologies such as Google Flutter, React and Vue.js.

{{< image src="images/solutions/universal-ui-comparison.png" caption="Comparison" height="" width="800" position="center" command="fit" option="q100" class="img-fluid" webp="true" >}}

<hr/>

# Universal Serialization

Universal Serialization is the Universal UI for machine-to-machine interaction. Every interaction
your app make with servers, is supported and can be done using Universal Serialization.

{{< image src="images/solutions/universal-serialization-1.png" caption="Usage Of Universal Serialization" height="300" width="500" position="center" command="fit" option="q100" class="img-fluid" webp="true" >}}

Read and write data as object models, to and from virtually any target format. 
It supports Postgres database, JSON, YAML, XML, and KFoundations’s own K4 format. 
It can even convert URL query strings back and forth to objects.

Universal Serialization is supplemented with a SQL-like DSL that acts like ORM (Object Relational Mapping). 
It constructs relevant select, insert, update, and delete queries and send them to database server. 
Then, it uses that knowledge to transform the result-set returned from the server back into 
entity object models.

{{< image src="images/solutions/universal-serialization-2.png" caption="Universal Serialization at a Glance" height="300" width="500" position="center" command="fit" option="q100" class="img-fluid" webp="true" >}}

<hr/>

# Universal Culture

{{< image src="images/solutions/universal-culture-1.png" caption="Internationalization Using Universal Culture" height="300" width="500" position="center" command="fit" option="q100" class="img-fluid" webp="true" >}}

The core feature of Universal Culture is the introduction of advanced dictionaries that can 
formulate translation of parameterized strings, dates and numbers into any given target 
language. Moreover, these dictionaries are supported by Universal Serializations framework, 
which means that they can be supplied in any format including, K4, JSON, XML, YAML, or 
programmatically.

Specially in case of number, time and date formats, UC's advanced dictionaries can be supplied 
and used as libraries to be included and used alongside user-defined dictionaries.

These are example of what Universal Culture can localize.

```text
<Strings>
HELLO (en) -> Hello
      (fa) -> سلام
      (ja) -> こんにちは
<Numbers>
  (en) -> 123.456 
  (fa) -> ۱۲۳/۴۵۶
  (en/read) -> one thousand and two hundred thirty four
  (en/order)-> one thousand and two hundred thirty fourth
  (fa/read) -> هزار و دویست و سی و چهار
  (ja/read) -> 千二百三十四
<Julian Calendar>
  (en/short)  -> 11/02/81
  (en/long)   -> Monday, November 2, 1981 CE
  (en/longer) -> Monday, second of November, one thousand and nine hundred eighty one CE
  (ja/simple) -> 1981-11-2
  (ja/short)  -> 西1981年11月2日
  (ja/long)   -> 西暦1981年11月02日（月）
  (ja/longer) -> 月曜日 西暦千九百八十一年十一月二日
<Japanese Calendar>
  (ja/short)  -> 平5年11月2日
  (ja/long)   -> 平成5年11月02日（火）
  (ja/longer) -> 火曜日 平成五年十一月二日
<Jalali (Persian) Calendar>
  (fa/short)  -> ۷۷/۰۳/۱۲
  (fa/long)   -> چهار شنبه ۱۲ خرداد ۱۳۷۷ ه.ش.
  (fa/longer) -> چهار شنبه دوازدهم خرداد هزار و سیصد و هفتاد و هفت هجریِ شمسی
  (en/short)  -> 03/12/77
  (en/long)   -> Wednesday, Khordad 12, 1377 AH
  (en/longer) -> Wednesday, twelveth of Khordad, one thousand and tree hundred seventy seven AH
```
<hr/>

# Universal More!

## Universal Web Client

Our ultimate goal is to bring the same fluid and efficient APIs to every platform. 
That couldn't be more true about the WebClient API. It works on all possible Scala 
targets including JVM, JavaScript and Android, having a tailored implementations for 
one each of these underneath. Integration of WebClient with Universal Serialization 
and StreamWriter APIs makes it the most fluent and versatile RESTful client out there.

Usage Example:

```scala
client.request(URL("http://...")) //: WebClient.RequestBuilder
  .withHeader("header", "value")  //: WebClient.RequestBuilder
  .get                            //: Future[WebClient.Response]
  .foreach(r => STD_OUT.writeAll(r.body))
```

## Universal Validation

We offer a novel and rich functional validation framework that ensures the data that is 
being passed around always fits its contract. It comes with a DSL to define the contracts, 
and applying them to data. Further more, when it is safe, it can convert data from one form to 
another. Validation errors thrown by the validation framework are compatible with both 
Universal Serialization and Universal Culture. They can be passed from server to client, and 
from client to end user, while being translated to human readable messages in user's language 
of choice.

Usage Example:

```scala
val passwordRule = AllOf(
  Property.ustringLength(InRange from 8 128),
  Contains.UPPERCASE,
  Contains.LOWERCASE,
  Contains.anyChar('%', '$', '%', '&', '^'),
  Not(Contains.anyString("123", "abc")))
```


## K4 Language

K4 is a machine- and human-readable marked up language that fixes lack of type-safety in JSON, 
and bulkiness of XML. Example:

```text
MultiDictionary[default="en-US"
  fallbacks={
    Fallback[from="zh-HANT" to="zh-HANS"]}
  domains={
    Domain[name="co.mscp.uref.webui" entries = {
      EntrySet[key="LOGIN_HINT" values={
        Entry[lang="en-US" value="Hint: Login to create fancy urls.”]}]}]}]
```


## LoTeX Language

LoTeX is a typesetting language  inspired by LaTeX, retaining the simplicity but fixing grammar 
ambiguity of Markdown. Example:

```text
This web application is a demonstration of various technologies in \b{KFoundation} software platform. KFoundation is an open-source project development and maintained by Mindscape Inc.
\list{
    \* Localization is provided by \b{Universal Culture} - one the mostcomplete and advanced localization toolsets.
    \* Interaction between client and web server, and between web server and database server is enabled by \b{Universal Serialization}.
\}
```

<hr/>

# KnoRBA Project

Recursively built on KnoRBA itself with its only other dependency being KFoundation POSIX Edition, 
it is an attempt to create a new unifying and universal operating system based on a new programming 
paradigm, called Agent-Based Computing (inspired by Minskey’s ideas, and comparable to Hewitt’s Actor).

KnoRBA is distributed and parallel in its very core. It can operate dynamically changing clusters 
of devices as a single fault-tolerant integrated system in a decentralized fashion. The resulting 
system can be a supercomputer, a car, or a smart home. Current prototype is made of a runtime 
environment (ARE) that does distributed process management and interprocess communication (IPC), 
as well as a C++ library for building KnoRBA Apps (KAP).

{{< image src="images/solutions/knorba.png" caption="KnoRBA Technology" height="600" width="810" position="center" command="fit" option="q100" class="img-fluid" webp="true" >}}
