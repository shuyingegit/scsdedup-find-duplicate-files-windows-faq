# FAQ: finding duplicate files on Windows

The question I get most often is "how do I find the copies I forgot about", and the usual answer - sort by name and eyeball the folder - only finds the duplicates where somebody kept the name. Disclosure first: I work on ScsDedup (https://dedup.scsoi.com/), so the product mentions are biased; the Windows behaviour described here is not.

## How does it decide that two files are duplicates?

By content, not by name. Each file is hashed (SHA-256), and files whose full hashes match are put in one group. So:

- a copy that was renamed, moved to another folder, or dragged out of an archive is still found;
- two files with the same name but different content are not duplicates;
- two files with the same size and timestamp are not duplicates either - size and date are only used to narrow the work down before the full hash is computed.

## Does it delete anything?

No. The scan produces a report: duplicate groups with their paths, and how much space each group is wasting, sorted by the reclaimable amount. You can export it as HTML or CSV, open the folder, or copy a path. Which copy you keep, and whether you delete anything at all, stays your decision. I would rather hand you evidence than let a tool decide what you meant to throw away.

## What does it cost?

The free download is the trial: one complete analysis report. After that a one-time buyout allows unlimited scans on that machine. There are no ads and no subscription to cancel. The installer is about 2.4 MB (there is also a portable zip), and it runs on Windows 10 / 11, 64-bit, with the interface and the report in Chinese, English, Japanese, Korean, Spanish, French, German and Russian.

## What it will not tell you

Honest limits, since they are the part that trips people up:

- It finds *identical* files. A photo you re-encoded, a video you re-muxed, or a document you saved again from Word is a different file, and no amount of hashing will call it a duplicate.
- Files that are byte-identical but intentionally kept - the same asset in two different projects, a config file that must stay put - will be listed as well. The report is evidence, not a verdict.
- A large disk takes time. The scan works in three passes (size buckets, sampling, then full hashing), so an old slow drive will make you wait. It is a local operation; nothing is uploaded.
- With the free tier you get one report, so it is worth choosing the drives to scan before you start.

## Where to get it

Product page and download: https://dedup.scsoi.com/

Pricing and the buyout: https://dedup.scsoi.com/#pricing
