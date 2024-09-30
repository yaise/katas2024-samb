# Storing uploaded resumes in file store

## Status

Accepted

## Context

Candidates will upload resumes to ClearView. These resumes will typically be PDFs that will be used throughout ClearView and will be transferred to prospective employers. We need to store these original resumes.

## Decision

We will store these resumes in a file-store service like AWS S3. There's equivalent file store services across cloud providers.

