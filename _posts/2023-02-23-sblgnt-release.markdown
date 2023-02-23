---
layout: post
title:  "SBLGNT Release"
date:   2023-02-23 12:45:00 -0700
categories: release
---

# Release of SBLGNT Context Annotation

We are pleased to make available the `1.1.0` release of the OpenText Context Annotation. This release includes the following features:

*   **New Trees** following the SBLGNT edition of the Greek New Testament, which was recently made available on a CC license

## Schema Changes

Rather than giving each element a `<c>` tag, we have now simply called each element according to its type. E.g.,
```xml
<!-- Each book of the New Testament comprises a text node -->
<text id="3John">
    <!-- Each text comprises at least one turn -->
  <turn depth="1" id="t.SBL.3John" chStart="1" vStart="1" chEnd="1" vEnd="15">
      <!-- Each turn is broken down into zero or more turn segments -->
      <seg id="s.SBL.3John.1.1-4" title="Address and Commendation">
          <!-- Each turn (or turn segment) comprises one or more moves -->
          <move id="m.SBL.3John.1.1" chStart="1" vStart="1" chEnd="1" vEnd="1">
              <!-- Each move includes any expressions realizing that move -->
              <token 
                clearId="n64001001001" 
                id="SBL.3John.1.1.1.1">Ὁ</token>
            ...
```

`@usfm` identifiers have been removed.

`@clearId` now follows the alphabetically sortable order of the IDs used in the [macula-greek](https://github.com/Clear-Bible/macula-greek) repository.

## Work in Progress

We are currently in the process of comparing the OpenText `turn` elements to the data contained in Clear Bible's [speaker-quotations](https://github.com/Clear-Bible/speaker-quotations) dataset. We will be making a new release of the OpenText Context Annotation once this comparison is complete. We may augment the speaker-quotations dataset with identification for speakers in nested speaker turns.
