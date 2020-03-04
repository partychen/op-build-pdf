
## Handoff Repo Structure

## Publishing
```
Q: fileA contains a link to another topicB. This link is changed now.  No localizable text is changed. Will the fileA be republished (without loc handoff/handback) automatically?

A: YES
```

```
Q: FileA has a reference to ArtB. We don’t localize the art, so it falls back to english.  The source ArtB is updated (modified picture, same name).  Will the loc fileA be republished automatically? 
A: No, no re-publishing happened. But if you reload the published loc page, the artB will also be changed.
```

```
Q: Metadata ms.date is updated in FileA by writer; will loc fileA be republished with updated ms.date automatically?
A: ms.date is non-localized content, so Yes, the loc fileA will be automatically HB and republished.
```
