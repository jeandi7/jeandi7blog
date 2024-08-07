+++
title = 'Zanzibar SpiceDB-like reader in less than 350 lines of golang'
date = 2024-07-08T23:24:28+02:00
tags = ["computer science"]
+++

#

I wanted to offer in Golang the example of a small handwritten reader.
(This is an exercise I often do when learning a new language)

Since I've been working with SpiceDB for a while, the purpose of this example is to provide sample code that implements a subset of the SpiceDB grammar.

SpiceDB is Google Zanzibar like and is available under the permissive Apache License 2.0. 

Google Zanzibar Authorization System is a scalable service for managing fine-grained access control using Relationship-Based Access Control (ReBAC).
(See https://github.com/jeandi7/prologzanzibar)

The program does nothing more than respond if the text submitted to it is correct with regard to the grammar.

No semantic analysis for now.

So i give myself the following BNF LL(1) grammar:


```
// Zanzibar restricted BNF grammar
// SpiceDB like
// Only relations are declared (not permissions)

<Zschema> ::= <Zdef>*
<Zdef> ::= "definition" <Zname> "{" <Zbody> "}"
<Zname> ::= <identifier>
<Zbody> ::= <Zrelation>*
<Zrelation> ::= "relation" <Zname> ":" <Zname> ("|" <ZName)*
<Zname> ::= <identifier>
<identifier> ::= [a-zA-Z_][a-zA-Z0-9_]*

```

# Zanzibar SpiceDB-like Reader

Implementation is made with lexical analysis and syntaxic analysis

![reader](./images/zreader1.gif)


# Example

go run  zreader.go -fschema "./zschema.zed"

I keep the .zed extension for the reading of a file that allows me to keep the spicedb coloring thanks to the Visio Authzed-language-support plug-in.

The file zschema.zed to read :
![file](./images/zschema.png)

response: parsed schema OK: [{monsujet []} {monsujet2 [{marelation [monsujet]}]} {maressource [{marelation [monsujet monsujet2]} {marelation2 [monsujet monsujet2 monsujet3]}]}]

I also provide a small automated test in the zinterpreter_test.go with 7 different schemas to read.

# 

The complete golang reader on https://github.com/jeandi7/zreader1

# 
About Zanzibar : https://storage.googleapis.com/pub-tools-public-publication-data/pdf/0749e1e54ded70f54e1f646cd440a5a523c69164.pdf

About SpiceB : https://authzed.com/blog/spicedb-is-open-source-zanzibar#everybody-is-doing-zanzibar-how-is-spicedb-different
