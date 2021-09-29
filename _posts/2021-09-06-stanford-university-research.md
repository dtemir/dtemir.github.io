---
layout: post
title: Stanford University Summer Internship
category: experience
---

This summer, I had the once-in-a-lifetime opportunity to do research in one of the most exciting areas of bioengineering 
at a top research university. So I figured I'll share my findings and thoughts about it.

Just a quick takeaway: doing research is awesome and everyone should try to do some in the field they are excited about.

![A group photo with Rosetta Interns from around the US. June 2021, Chapel Hill, NC](../assets/img/group_photo_rosetta.jpg)
*rosetta interns, summer 2021 | UNC Chapel Hill*

## Table of contents:
* [Overview](#overview)
* [Rosetta](#rosetta)
* [RosettaCommons](#rosettacommons)
* [Protein Design](#protein-design)
* [Research](#research)
* [Outcomes](#outcomes)

## Overview

This summer I worked as a *research assistant* at **Stanford University, [Huang Lab](http://www.proteindesign.org/)**.
I conducted research in protein sequence design, expanding on the lab's **Deep Learning** project called the **[Protein Sequence Design Algorithm](https://github.com/ProteinDesignLab/protein_seq_des)**
and experimenting with it to build *internal hydrogen bonding networks[^1]*.

The result was a poster titled 
*[Building Hydrogen Bonding Networks with Protein Sequence Design Model](https://temir.dev/projects/rosetta-poster/poster)* and presented at **[Summer RosettaCON 2021](http://www.rosettadesigngroup.com/rosettacon/)**.

[![My poster titled Building Hydrogen Bonding Networks with Protein Sequence Design Model that covers my work on the project during the summer](../assets/img/rosetta_poster.png)](https://temir.dev/projects/rosetta-poster/poster)
*try clicking on the image*

## Rosetta

First, [Rosetta](https://new.rosettacommons.org/docs/latest/Home) is a cluster of software with algorithms for computational modeling and analysis of protein structures.[^2]
Today, it is used to do things like: 
* _de novo protein design_
* _enzyme design_
* _ligand docking_
* _structure prediction_

It first started in the Baker Lab of [Dr. David Baker](https://www.ipd.uw.edu/people/ipd-faculty-staff/david-baker/) at the University of Washington.

Today there is a Python wrapper/interface for it, called [PyRosetta](https://www.pyrosetta.org/).

The goals for Rosetta are to:
* learn more about macromolecular interactions
* design new proteins
* develop an efficient way to search conformation and sequence space[^3]
* find a more useful energy function[^4]


## RosettaCommons

![Rosetta Commons Logo](../assets/img/rosetta.png)

RosettaCommons is an organization of more than 50 universities and institutes around the world who use Rosetta in their research.[^5]
The Rosetta source code belongs to _all_ members of RosettaCommons, which means that they pull their efforts together to develop it.

RosettaCommons is also the organization that benefits from licensing the Rosetta software. 
By selling the software to big companies, they are able to host conferences, support labs, and pay interns like me.
However, they provide the software for free to people who want to use it in academic purposes.

The lab I worked at this summer is a part of RosettaCommons. 
Stanford University's Huang Lab is into de novo protein design, 
trying to create new design platforms with Machine Learning.

## Protein Design

Proteins are of immerse significance to humans. 
They are used for structure, function, and management of the body's various tissues and organs.

Designing proteins is a still new field in Bioengineering.
But there have been big steps in developing ways to build proteins from scratch.
All of them require evaluting the structures with already mentioned energy functions.

![A screenshot of a protein modeled in PyMol](../assets/img/ex4_results.png)
*a modeled version of an alpha-beta protein in PyMol*

## Research

So my research was about using the output of the Convolutional Neural Network developed by students at Stanford University and adjust it to bring specificity to the protein design process.
The way the **[Protein Sequence Design Algorithm](https://github.com/ProteinDesignLab/protein_seq_des)** uses its Convolutional Neural Network is by sampling a random residue on a protein, such as a single amino acid space from within a long sequenced protein, and predicting the possible types of amino acids for it. Once it has a distribution of possible amino acid types for that particular residue, it samples one of them to replace the residue with it.
This way, the algorithm iterates over the algorithm many times until the solution starts to converge.[^6]

![An image describing the algorithm process. The algorithm reads the environment around a particular residue (amino acid piece) and puts it into the Convolutional Neural Network that then produces a distribution of possible amino acids from which the algorithm samples to replace that residue](../assets/img/algorithm-process.png)
*the algorithm process*

My research was based on building an additional module, called [Resfile](https://github.com/ProteinDesignLab/protein_seq_des/tree/master/seq_des/util), to take a file like this

```
ALLAA # set a default command for all residues not listed below
START
34 ALLAAwc # allow all amino acids at residue #34
65 POLAR # allow only polar amino acids at residue #65
36 - 38 ALLAAxc # allow all amino acids except cysteine at residues #36 to #38 (including)
34 TPIKAA C # set the initial pose sequence postion at residue #34 to cysteine
55 - 58 NOTAA EHKNRQDST # disallow the listed amino acids at residues #55 to #58
20 NATRO # do not design the residue #20 at all
```

and produce a protein with all those constraints.

## Outcomes

The outcomes of my research were:

* Learning many things about Protein Design and Computational Biology
* Creating my first Research Poster
* Writing code that will be useful for the whole field

---
{: data-content="footnotes"}

[^1]: Hydrogen bond is a type of chemical interaction between two atoms that have positive and negative charges. Protein cores do not usually have hydrogen bonds because the amino acids inside tend to be hydrophobic, which means they do not carry charge. Internal hydrogen bonding networks are therefore unusual for proteins and show how much *specificity* the project I have worked on can bring to protein design.   
[^2]: By the official [RosettaCommons](https://www.rosettacommons.org/software) website.
[^3]: Conformation and sequence spaces are vast in protein design. Imagine a protein of 100 amino acids. Each amino acid can have one of 20 traditional identities. 100 to the power of 20 is the number of possible amino acid sequences. This is a vast number that is impossible to crack down with brute force.
[^4]: An energy function is a type of function that can tell us whether a protein structure is efficient. It takes into account many chemical theories to determine whether a structure is stable. It usually serves as a guide for us to see whether a structure is going to work, but it is inaccurate due to the limited knowledge base.
[^5]: By the official [RosettaCommons](https://www.rosettacommons.org/about) website.
[^6]: It might take hours for the algorithm to run on a moderately long sequence for 2,500 iterations that it usually requires for it to converge. I would prepare the design I want to run during the day, and submit the jobs for designs to the Stanford server before going to bed. That way I would get the results in the morning. 
