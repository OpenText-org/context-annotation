---
layout: page
title: About
permalink: /about/
---

## OpenText Context Annotation

This repository contains hierarchical (i.e., tree format) context annotations derived from [OpenText](http://www.opentext.org) 2.0 data (forthcoming). 

## What are context trees?
In OpenText's functional-linguistic model, *context* is represented by discourses. More specifically, each discourse includes at least one `turn` node (at least one speaker must take a turn, or else there would be no discourse) and zero or more turn stages (these mostly correspond to traditional pericopes, but see caveats below regarding projection data). The graphological expressions (i.e., tokens) are included for human-readability and to anchor this contextual representation to the correct tokens.

## Viewing the trees
The XML files for each book of the New Testament can be downloaded and opened directly in any XML or text editor.

In order to view a rendered display of the context trees, ensure the `context.css` file is in the same directory as the XML file you are trying to view, and open the XML file in your internet browser (e.g., Safari or Chrome).

## Node types
- `text` nodes represent texts. Currently, these are only the books of the New Testament.
- `c` nodes represent contextual units. There are three types of contextual unit:
	- `turn` units represent each time someone speaks
	- `seg` units represent turn segments, and these include a title for reference.
	- `move`
- `e` nodes represent graphological expressions (I.e., whitespace-separated tokens). 
	- We include three identifiers on expression nodes. 
		- An easily-readable `@id` (similar to an OSIS identifier) attribute includes the base-text version (e.g., `N1904` for the Nestle 1904 text). The format is `[base-text-version].[book].[chapter].[verse].[word]`
		- `@clearId` matches the ids in [macula-greek](https://github.com/Clear-Bible/macula-greek), and is alphabetically sortable. The format is documented on the macula-greek repository.
		- `@usfm` follows the USFM/Paratext format, and is (in theory) more universal. See [USFM documentation](https://ubsicap.github.io/usfm/) for details.
	- In addition, option `@before` and `@after` attributes encode any associated punctuation.

{% highlight xml %}
<!-- Each book of the New Testament comprises a text node -->
<text id="Gal">
    <!-- Each text comprises at least one turn -->
    <c unit="turn">
        <!-- Each turn is broken down into zero or more turn segments -->
        <c unit="seg" title="Introductory Greeting and Doxology">
            <!-- Each turn (or turn segment) comprises one or more moves -->
            <c unit="move" id="N1904.Gal.1.1.1-2.10">
                <!-- Each move includes any expressions that realize that move -->
                <e id="N1904.Gal.1.1.1">Παῦλος</e>
                <e after="," id="N1904.Gal.1.1.2">ἀπόστολος</e>
                ...
{% endhighlight %}

## Projection data
Because projected speech realizes a distinct order of discourse from its projecting matrix (view [example rendering](https://dissertation.ryderwishart.com/situations) by turn segment), projected speech is enclosed in a distinct turn element.

In other words, a turn nested within a turn represented a new, embedded order of discourse. In the New Testament, there are up to 4 levels of discourse. 

In the future, we hope to release turn-segment annotations for all nested discourses. Currently, there are only turn segments for top-level turns (e.g., the narrator of a text).

Orders of discourse are noted in the comment elements in this example:

{% highlight xml %}
<text id="Mark">  
	<!-- First-order discourse: "Mark", the narrator, speaks -->
    <c unit="turn">  
        <c unit="seg" title="The Ministry of John the Baptist">  
            <c unit="move" id="N1904.Mark.1.1.1-7">  
                <e id="N1904.Mark.1.1.1">Ἀρχὴ</e>  
                <e id="N1904.Mark.1.1.2">τοῦ</e>  
                <e id="N1904.Mark.1.1.3">εὐαγγελίου</e>  
                <e id="N1904.Mark.1.1.4">Ἰησοῦ</e>  
                <e id="N1904.Mark.1.1.5">Χριστοῦ</e>  
                <e before="(" id="N1904.Mark.1.1.6">Υἱοῦ</e>  
                <e after=")." id="N1904.Mark.1.1.7">Θεοῦ</e>  
            </c>  
            <c unit="move" id="N1904.Mark.1.2.1-4.13">  
                <e id="N1904.Mark.1.2.1">Καθὼς</e>  
                <e id="N1904.Mark.1.2.2">γέγραπται</e>  
                <e id="N1904.Mark.1.2.3">ἐν</e>  
                <e id="N1904.Mark.1.2.4">τῷ</e>  
                <e id="N1904.Mark.1.2.5">Ἠσαΐᾳ</e>  
                <e id="N1904.Mark.1.2.6">τῷ</e>  
                <e id="N1904.Mark.1.2.7">προφήτῃ</e>  
                <!-- Second-order discourse: "Isaiah the prophet" speaks -->
                <c unit="turn">  
                    <c unit="move" id="N1904.Mark.1.2.8-3.14">  
                        <e id="N1904.Mark.1.2.8">Ἰδοὺ</e>  
                        <e id="N1904.Mark.1.2.9">ἀποστέλλω</e>  
                        <e id="N1904.Mark.1.2.10">τὸν</e>  
                        <e id="N1904.Mark.1.2.11">ἄγγελόν</e>  
                        <e id="N1904.Mark.1.2.12">μου</e>  
                        <e id="N1904.Mark.1.2.13">πρὸ</e>  
                        <e id="N1904.Mark.1.2.14">προσώπου</e>  
                        <e after="," id="N1904.Mark.1.2.15">σου</e>  
                        <e id="N1904.Mark.1.2.16">ὃς</e>  
                        <e id="N1904.Mark.1.2.17">κατασκευάσει</e>  
                        <e id="N1904.Mark.1.2.18">τὴν</e>  
                        <e id="N1904.Mark.1.2.19">ὁδόν</e>  
                        <e after="·" id="N1904.Mark.1.2.20">σου</e>  
                        <e id="N1904.Mark.1.3.1">φωνὴ</e>  
                        <e id="N1904.Mark.1.3.2">βοῶντος</e>  
                        <e id="N1904.Mark.1.3.3">ἐν</e>  
                        <e id="N1904.Mark.1.3.4">τῇ</e>  
                        <e id="N1904.Mark.1.3.5">ἐρήμῳ</e>  
                        <!-- Third-order discourse: "The voice in the wilderness" speaks -->
                        <c unit="turn">  
                            <c unit="move" id="N1904.Mark.1.3.6-14">  
                                <e id="N1904.Mark.1.3.6">Ἑτοιμάσατε</e>  
                                <e id="N1904.Mark.1.3.7">τὴν</e>  
                                <e id="N1904.Mark.1.3.8">ὁδὸν</e>  
                                <e after="," id="N1904.Mark.1.3.9">Κυρίου</e>  
                                <e id="N1904.Mark.1.3.10">εὐθείας</e>  
                                <e id="N1904.Mark.1.3.12">τὰς</e>  
                                <e id="N1904.Mark.1.3.13">τρίβους</e>  
                                <e after="," id="N1904.Mark.1.3.14">αὐτοῦ</e>  
                                <e id="N1904.Mark.1.3.11">ποιεῖτε</e>  
                            </c>  
                        </c>  
                    </c>  
                </c>  
            </c>  
        </c>  
    </c>  
</text>
{% endhighlight %}

## Versioning

Each version has three dot-separated numbers, e.g. 1.2.3. The first number is the major version, the second number is the minor version, and the third number is the patch version.

The *major version* is incremented when there are significant or breaking changes to the schema or data. A breaking data change would include the removal of a file.

The *minor version* is incremented when there are additions or non-breaking changes to the schema.

The *patch version* is incremented when there are changes to the data only. Data change examples might include the addition or removal of elements, addition or removal of words or punctuation, changes in the order of elements, or changes in attribute values (but not attribute formats).

## Contributing

The projection data has been manually reviewed at least once, but some errors likely remain.

If you catch any errors, please create an issue on this repository and add the `data-error` tag. Alternatively, you can email this repository's contributors.

## About OpenText

Creators of the first openly-licensed syntactic analysis of the Greek New Testament, OpenText exists to advance research in linguistics and Greek New Testament studies through innovative functional-linguistic analyses, datasets, and resources.

The OpenText project is affiliated with the [Center for Biblical Linguistics Translation and Exegesis](https://cblte.org).
