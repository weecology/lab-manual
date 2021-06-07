---
title: "Submitting a manuscript"
linkTitle: "Manuscript submission"
weight: 2
---

Congrats! You're getting ready to submit a manuscript for review at a journal. This guide will walk you through the various steps in the process, however, it assumes you've already decided what journal to submit to. Right now, there is no wiki page on that, so talk with Ethan or Morgan or one of the postdocs/staff for advice.

## Manuscript Formatting

Go to the journal's website, and they should have a section called "For Authors", "Author Instructions", "Guide to Authors" or something along those lines. They should have detailed guidelines for citation style, section order, cover letter requirements, submission website link, etc. They will also, hopefully in the same location, have a description of the focus of the journal, which your manuscript should fall within. 

The journal may have document templates (most commonly for Microsoft Word or LaTeX). If you are working in LaTeX, you may want to consider [Overleaf](https://www.overleaf.com/), which has some built-in templates for journals. If you are working in Rmarkdown, the [`rticles`](https://github.com/rstudio/rticles) package also has some common templates.

Using a citation manager that can format references using Citation Style Language (CSL) is highly recommended. Many styles can be found or modified from existing ones at [Zotero's CSL list](https://www.zotero.org/styles). Many Rmarkdown outputs accept CSL files to format references.

## Recommending reviewers & editors

Journals typically ask you to recommend 3 or more people who could potentially review your manuscript. Those people may or may not end up being reviewers, and they might not even be asked, but providing a good list will help increase the chance that the review process starts quickly and that you get good feedback from relevant reviewers.

It's probably most important to recommend scientists who have similar philosophies to yours (e.g., if the paper has a macroecological approach, don't choose someone who thinks fieldwork is the only way to do ecology).

Don't recommend anyone who could have a conflict of interest. The idea is that people who would be biased by personal or institutional relationships to the authors should review the paper. Typically this is considered to include anyone at your current institution and anyone who's been a (close) coauthor on a paper with any of the current manuscript's coauthors in the last 5 - 10 years or so. You should ask coauthors to check the list of reviewer recommendations to conflicts before submitting. 

Some journals will also ask for editor recommendations. There should be a page on the journal's website with the editorial board, choose 1 - 2 associate editors that seem most appropriate, based on the manuscript topic.

Some journals will also allow you to designate reviewers with "conflicts" or something similar. This is not a list of people who have a conflict of interest as described above. It is an opportunity to designate people that you don't want to review the paper because they are predisposed to review it negatively (e.g., they are directly competing with you in the research space, or have known objections to certain topics/approaches). We basically never list people, but if you are concerned about someone chat with your advisor.

## Cover letter

All cover letters consist of: 
- a business header (either the name of Editor in Chief & their professional address or your name and professional address) (if you forget this part it is not a problem and choosing one header or the other won't raise any eyebrows though to the editor is more traditional)
- a description consisting of the manuscript title, authors, and what 'type' of article it is being submitted as for consideration (e.g., Report, Methods, Ideas and Concepts, Article, this varies from journal to journal and some journals do not have different types of article)
- a brief description of the manuscript (typically 1 paragraph). For many journals, this description should convey either implicitly or explicitly why this article is of interest to the specific readership of this journal. If going to a general ecology journal like Ecology/Ecology Letters/AmNat then this description should focus on the aspects of your work that a general readership would find interesting. If going to GEB then focus on the general interest and global nature of the study. etc etc. If you are going for one of the journals whose mission is to publish what they think is the most influential research (Science, Nature, PLoS Biology, PNAS, eLife) then you need to emphasize the novelty and importance of the work and more than 1 paragraph may be acceptable (see the Riemer example below).
- Any assurances or statements the journal requires (i.e. the work is the authors' own, it is not submitted elsewhere, etc).

Your letter should not be longer than 1 page, including the header material and your 'signature' at the bottom (don't need to literally sign it).

Here are some examples of cover letters

- [Cover letter](https://github.com/sdtaylor/phenology_dataset_study/blob/master/manuscript/cover_letter.txt) for [Taylor et al. 2018](https://doi.org/10.1002/ecy.2568)
- [Cover letter](https://github.com/weecology/lab-wiki/blob/master/Riemer-cover-letter.pdf) for [Riemer et al. 2018]( https://doi.org/10.7554/eLife.27166)

## Data and Code Archiving

Recommendation: Archive your code on [Zenodo](https://zenodo.org/) using the [GitHub-Zenodo integration](https://guides.github.com/activities/citable-code/). Archive any data that hasn't already been archived and that you have permission to archive (typically based on the license allowing "redistribution" or based on permission from the data collector) on either Zenodo (by archiving it along with the code) or separately on [Dryad](https://datadryad.org/) (linking to the relevant code through Dryad). Have your code download the already-archived data from the archival source instead of archiving it again. If the journal has open data/code badges, indicate that you want to use them.

Discussion: Most journals now require the sharing of the code and data used for analyses in a paper. Even in cases where it isn't required this is good for science through supporting reproducibility and building on existing work. Availability of data and code also increases use and citation of papers. There are a variety of locations to archive data. In ecology, general purpose repositories are the norm for most data. Zenodo and Dryad are both non-profits focused on the good of science with good sustainability models. They are also both common locations for archiving so choosing them will avoid any confusion about whether or not the data is properly archived. "Archive" implies that the data/code will be available in the long-term through guarantees to maintain the infrastructure hosting the data/code and not allowing the person depositing the data/code to remove it. The ability to remove code from GitHub means that GitHub is not considered archival.

## Funding sources

Recommendation: Follow journal and funder guidelines for acknowledging funding sources.

Discussion: Funding agencies require that when their funds are used for research that this funding is acknowledged. Journals have two general approaches to doing this: 1) listing the funding in the Acknowledgements section; 2) having a separate component of the submission process where funding sources are acknowledged. Funding agencies often have specific requirements as well. Check with your advisor & collaborators in the sources that funded the work (you may not always be aware of the different sources) and also make sure to acknowledge any support that was made directly to you (e.g., individual fellowships). Check the funders requirements for for acknowledging their funding or follow an example of a previous paper from the lab with the same funding source.

## Open/Transparent Review

Recommendation: Participate in open/transparent review.

It is increasingly common for journals to post reviews and author responses to those reviews online with a paper if it is accepted for publication in the journal. Some journals are also exploring posting reviews even for manuscripts that aren't accepted. The goal is to increase the transparency of the overall scientific process and provide accountability for journals and authors if they have had an important issue pointed out to them that they haven't addressed. Reviewers are typically given the option to remain anonymous. Generally speaking we think open, but anonymous, review history is a positive development and recommend opting in even if it is not required, but this is still a developing area and individual lead authors are welcome to not opt-in (or opt-out if allowed) if they wish after consulting with coauthors. 

## Submission

Your formatted manuscript and cover letter will get uploaded to the journal's author submission website. There will also be some web forms where they will ask for reviewer/editor suggestions, probably make you enter co-author info (that is already on your cover sheet, but try not to think about the redundancy in the process). Click submit and now you wait for the response, which is often in the 1-2 month, but sometimes closer to 3 months.

## Preprints

Recommendation: Submit preprint to bioRxiv at time of first submission to a journal and update the preprint whenever you submit a revision of the manuscript (either as part of ongoing review or to a new journal after rejection). Check the journals preprint policy (in either the instructions to authors or on [Sherpa Romeo](https://v2.sherpa.ac.uk/romeo/)) just to make sure they are allowed (though preprints are now allowed basically everywhere) and get sign off from coauthors to post a preprint.

Discussion: All major journals in ecology that we are aware of now allow posting preprints prior to submission (in part due to [Weecology efforts](https://jabberwocky.weecology.org/?s=preprint&submit=Search)). They are good for science and professionally beneficial to both early career and established scientists (e.g., [Desjardins-Proulx et al. 2013](https://doi.org/10.1371/journal.pbio.1001563), [Vale 2015](https://doi.org/10.1073/pnas.1511912112)). Benefits to putting up preprints include the possibility that more people will see your work, it will be able to influence the field sooner (as it can takes months or years for papers to be published), it can start to accumulated citations (currently used as a form of academic credit), and you could get valuable feedback to improve the manuscript. Some of this depends on how actively you promote the preprint by sharing on social media, disseminating to other scientists, etc. Journals also identify preprints of interest and could reach out to you about publishing with them. 

In addition, all of our grants include statements that we will submit preprints, so if you decide you do not want to submit a preprint or a coauthor does not want to agree to this please talk to the relevant PI of any grants that have supported you.

There are a variety of preprint servers, but we almost universally use [bioRxiv](http://biorxiv.org/). It has become the standard location in the field and is run by a non-profit organization. Some journals only allow preprints posted to non-profit pre-print servers making it a good choice and it is a good player in ensuring science is available to all.

We typically submit the initial preprint at the same time as the initial submission of the manuscript to the journal. This will probably take 1-2 hours. To keep the preprint up to date and ensure that it satisfies funder mandates for open archiving it should be updated whenever the manuscript is resubmitted (either as part of a revision or to a new journal).

## Sharing work on social media

(info to be included: tone/style; tagging institutions, co-authors, funders; figures and alt-text; links to preprint and code/data)

## Dealing with reviews
When you get your reviews back, the next step is to figure out how to handle them. Typically reviewers will have major and minor criticisms. Your task is to sort through those criticisms and figure out a plan for addressing them. Reviewers are only human and they are not infallible. Their criticisms will fall into one of three categories: useful, neutral, and wrong. You are not required to do everything a reviewers tells you to do. Ethan and Morgan's philosophy (which we got from our advisor) is that if it doesn't harm the research/manuscript you do whatever a reviewer requests (i.e. everything in the neutral/good categories). If you think what the reviewer has suggested is majorly problematic, then we generally advise not doing it. In your response to the reviewers you can explain why you disagree with their suggestion/criticism. You want to choose judiciously when to stand your grand in the review process. Discussion with your co-authors/advisers is warranted.

When you resubmit your manuscript, you will also submit a detailed response to the reviewers. To construct this, cut and paste the reviews into a new document. Into this document you will write your response to each individual issue the reviewer brings up. Often reviewers will construct their reviews so that each paragraph is focused on a separate distinct issue, if not, you can break their paragraphs accordingly. Keep all of their comments in the document so it is clear you did not edit out any of their concerns. We find that a good starting place for your revision is sitting down with the document and thinking about how you would/should respond to each of these items and start writing in ideas/responses. Then you can use your responses as a template for making the changes in your manuscript.

Examples of Response to Reviewers:

- [Response to reviewers](https://github.com/weecology/lab-wiki/blob/master/PLoS-Response.pdf) for [Yenni et al. 2019]( https://doi.org/10.1371/journal.pbio.3000125)

## Response to editor
When you resubmit you will also submit a cover letter to the editor. This is distinct from the detailed response to reviewers. The cover letter will consist of 2 main parts:
- a statement similar to the first one in your cover letter stating the name of the manuscript and the authors and that you have revised your manuscript and are resubmitting it.
- a paragraph overviewing the changes you made in response to the reviews - in this paragraph you only really need to discuss what seem like the major concerns - especially if the editor highlighted them in their decision letter.

Examples of Resubmission letters:

- [Resubmission cover letter](https://github.com/weecology/lab-wiki/blob/master/PLoS-Revision-Cover-Letter.pdf) for [Yenni et al. 2019]( https://doi.org/10.1371/journal.pbio.3000125)

## Address for correspondence

Use your official university address, which is currently:

Department of Wildlife Ecology and Conservation  
110 Newins-Ziegler Hall  
PO Box 110430  
Gainesville, FL 32611-0430

Phone: (352) 846-0643  
Fax: (352) 392-6984  

## Managing co-authors

Do not forget your co-authors through this process. You do not have to go through this on your own. They can help you brainstorm how to deal with difficult issues, help run analyses to deal with concerns, help draft language for the response letter or implement revisions to the manuscript. 

Hopefully you have a good relationship with your co-authors and they are actively engaged, however often co-authors are more peripheral to a project (e.g., had a limited role in the analyses/manuscript). It can be easy to forget them as you manage all the moving parts of the review process. Professionally, however, you need to make sure they are OK with the manuscript during all the phases of this process. To do this we recommend following the [Collaborative Writing Guide](https://github.com/weecology/lab-wiki/wiki/Collaborative-writing). Regardless, you must ALWAYS have all co-authors sign off on the final version of the manuscript before submitting. 

#### *(Other potential topics)*