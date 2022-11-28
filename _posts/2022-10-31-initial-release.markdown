---
layout: post
title:  "Initial Release"
date:   2022-10-31 12:07:39 -0700
categories: release
---

# Initial Release of Context Annotation

We are pleased to make available the initial `1.0.0` release of Context Annotation. This release includes the following features:

*   **Trees** for each of the books of the Greek New Testament
*   **Turn** data for each time someone speaks
*   **Turn segment** data (i.e. pericope/episode/situation) for the top-level turns
*   **Move** data (typically realized by a sentence) for each turn or turn segment
*   Graphological **expression** data (either a whitespace-separated word or a punctuation mark) for each move
*   Three unique IDs for each expression
    *   OpenText: `@id`
    *   Clear Bible/Macula Greek: `@clearId`
    *   USFM: `@usfm`

## Work in Progress

Following this initial release, priorities for this dataset include the following:

*   Additional manual review of the trees is required to ensure any remaining errors are corrected
*   Turn segments for embedded turns are not yet available (e.g., segments for the Sermon on the Mount [Matthew 5-7], such as the Beatitudes, etc., do not exist in this release)
