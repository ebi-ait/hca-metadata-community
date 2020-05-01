---
layout: default
title: 2019-12 Lung
parent: Community Calls
nav_order: 1
---

# December Community Call - Lung

*Presenters:* Martijn Nawijn, Lisa Sikkema

## Slides:
- [Overview of the HCA-Lung initiative - Martijn Nawijn](https://drive.google.com/open?id=1l4dpYCv92dML0ZFQVEqByeq00xm0npPZ)
- [Lung Data structure, analysis, pipelines, and metadata details - Lisa Sikkema](https://drive.google.com/open?id=1yEvCujuBUnWoLMU2NyR7NgLqmo-GNmBp)

## Video recording:
<iframe src="https://drive.google.com/file/d/1C9GS2V24vvDHr8BefJre1YHwBMQV6K3o/preview" width="640" height="480"></iframe>

## Summary of the December community call

### Key learnings

- Many groups working on lung across Europe and US, different aspects - development, disease, adult lung, mouse lung
- Some groups collect extended annotation towards location of the sample within the organ (Pascal Barbry)
- Fabian Theis’ lab - effort to understand variation - both normal and abnormal - by integration of many different datasets - based on the provided metadata
- The more metadata the better to identify batch effects

### Needs from the community
- Align metadata within the Lung community
- Integrate different data within the Lung community
- Determine what metadata is needed for the imaging data - FISH
- Documenting location of origin of the sample 
- Basic demographic data, clinical/smoking data, etc
- Use of ontologies to ensure interoperability
- Collect as much metadata as possible to enable batch effect correction
  
### Ideas for how to action
- Organ specialists to collaborate with ontology experts to review existing ontologies, suggest addition of new ones
- Collect additional metadata (clinical data) - this is helpful for batch correction
- Provide guidelines, document best practices for depicting the location of origin of sample
- Find out a way to link overview images of the sample to the data submission to the HCA
- Expand HCA metadata to support imaging experiments 

## Detailed notes

### Overview of the HCA-Lung initiative - Martijn Nawijn 
Slides - https://drive.google.com/open?id=1l4dpYCv92dML0ZFQVEqByeq00xm0npPZ

I’ll be presenting a general overview of the lung initiative and what we are doing not only in Europe.

I will explain what we are doing to try and integrate data from different sources. Hence the importance of the metadata.

Laura, if you could bring up the presentation, I have about 15 slides.

LC - If you could share the slides maybe it would be better so you have control of the slides.

I think this is a decent overview of the projects. 

I am from Groningen, in the Netherlands.

For the Human Lung Cell Atlas, we started with an epithelial cell study. Since we have grouped with some groups. We have coordinated quite good. There is LungMAP that has been going for a long time. In the US there is HubMAP. And there is now LungMAP 2.
Pascal Barbry in France got a CZI pilot award.

We have been quite ambitious looking at the white paper. Looking at what we promised in that paper we are not quite there yet, but we are getting closer.

Lung is an interesting organ to sample. You can collect samples from living donors.

There is extended annotation towards location of sample within the organ. There is a lot of groups that can contribute. We thought that we would need contribution from anyone who could contribute samples.

It is a community effort.

Papers: First in Nature in 2014, about 200 cells. The number of cells and papers has increased over the last few years. The number of donors is really important for an atlas effort.

For the human lung cell atlas we need to integrate all datasets so that they are in a database and you can search and compare them.

To compare your data to published data. Also to understand where your data fits.

There is lots of mouse studies as well in LungMAP. There was quite a lot of paediatric studies there as well. 

Stockholm University and Karolinska are working on lung development.

MRC consortium is also working in lung development

HubMAP (CCF and Lung Tissue Atlas) is working on adult lung, and so are CZI Seed Networks (US mainly but also in EU): Run by Sasha Misharin

Recently awarded EU 15 partner consortium that I am running. We are using techniques used in the other initiatives.

There is multiple consortia and data out there. We will need to put this together.

In January we will start with the EU effort. Since I am the coordinator I feel confident I can share.

It will take healthy live donors and samples from deceased.

It is going to be 5 living donors, but the number of cells and different tissues will be high.

When we get limited amount of tissue we will focus on one single spatial technique.

For spatial, we use two FISH based methodologies, one with 70 probes and one with 30-50 probes. We will do this in the big blocks of samples.

These are being used in the lung development program.

What kind of metadata you need for the imaging data is not clear just yet, and it’s being debated.

snRNA-Seq is also going to be done.

Will all this sequencing data and imaging data.

We want to submit to DCP. GDPR we need to align to. We need to prepare to integrate this data.

There is datasets that are already there. On top of that there are datasets coming, both from sequencing and imaging perspective. If we want to integrate them, we will need to get the right data from all the groups in order to be able to do that. There is no current consensus in the group as to what is the right metadata. The sooner we reach consensus the better.

We need input from the entire community. I appreciate the opportunity to come and discuss this early on.

Absolutely required metadata:

Location of origin (with respect to CCF): Might be easier in this EU consortium. But it might be more difficult if smaller groups also produce data.
Basic demographic data, clinical/smoking data, geographical and ethical (Under GDPR we can’t collect data on a nice to have. We need to collect data only because it’s useful)
chemistry


DKH - If you don’t use the same wording you might be limiting interoperability.
LC - We are using ontologies to try and allow interoperability
DKH - In kidney at least, there needs to go through tuning. Someone with biology of kidney to look into the ontologies in detail.
LC - It would be great to get feedback from yourself and other experts
Michela (Imperial College) - Do you have experts who can review the ontologies.
LC - We don’t have a consistent help. Maybe I could reach the community to get experts who could revise and comment the ontologies.
MCN - In the lung we are trying to organise meetings. Any other organ will need to organise such meetings.

CCF:

There was a paper last week from Aviv and Rahul.
They use CT to measure and standardise bronco tree, and how it compares in between different individuals. The HCA lung community will generate lots of hrCT data. 

The paper says that we need to be able to build a reference so that we can refer  to that reference. For now I would advice we need to be very specific as to where the sample was coming from as lung is a big organ.

Pascal Barbry went to great detail to describe were the samples were originated from. There is a limit to the resolution on what you can record when sampling.

We will have a meeting in Israel in March. You can let me know if you want to register.

Any questions? If not, it makes sense to transfer to Lisa now, so that she can talk about the metadata.

Kathy Reinold - I would encourage people to use the cell ontology. Although it's not perfect, it is a single place where we can strive to make it better. Broad Institute is working hard to limit the ontologies we reference -- and sometimes recommend a limited vocabulary but based on a "preferred" ontology

### Lung Data structure, analysis, pipelines, and metadata details - Lisa Sikkema

Slides https://drive.google.com/open?id=1yEvCujuBUnWoLMU2NyR7NgLqmo-GNmBp

Metadata and the Lung Cell Atlas:

I’m a PhD in Fabian Theis’ lab and I will be working on taking all the metadata that has been produced in this initiative and try and integrate it. Before I was in Dana Pe’er’s lab in New York.

I will now talk about how do we use the metadata from a computational side.

One of the main goals is to try and define and understand what normal tissue looks like. This includes knowing the variation. We also want to define and understand abnormal and its variation.

I have been busy mostly trying to get all the data together and process it in the same way. Different labs have been using different pipelines. There are organisational issues to share data. 

There are different methods that are being used for data integration, like batch correction methods.

To give an overview of when we use metadata:

To find datasets
To assess the quality (that’s not always extracted from matrices)
Identification and correction of batch effects (determine if there is batch effect present, for which you need to have the biological knowledge, and determine the source
Data analysis and interpretation (eg disease status)

LC - Is there any particular field that can be more useful identifying batch effects?
Any information can be useful depending on what you need, and the question you are asking. Platform, depth of sequencing, way samples are processed. It’s difficult to assess which ones would help most.

Importance of identifying batch effect:

For lung data, due to the amount of data I think it’s going to be easy to spot batch effects.

Cell State Annotation:
Provided by lab
Mapping to a consensus cell reference

LC - At the moment we are just collecting raw data. Is there any consensus on type of files that people are expecting to use or are using?

There is a few different ones, csv, loom, mtx. Those are the basic ones. Then there is the scanpy platform, that comes with a file that has annotations. Hd5id file? Works with scanpy

LC - We should look into that so that we can give people advice so that we get to shapes that can be interoperable.

Michaela - trying to collect much more data from Heart donors - blood counts etc can be difficult

KR - I would suggest that the cell or the sample can be healthy or diseased, but not the patient.  The patient can have a collection of diagnoses that may not be relevant to the cell.

KR - use DUO to track Data Usage rights
