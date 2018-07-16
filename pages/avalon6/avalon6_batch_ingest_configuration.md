---
title: Batch Ingest Configuration
summary: "System information for configuring Batch Ingest tasks and processes."
sidebar: avalon6_sidebar
permalink: avalon6_batch_ingest_configuration.html
folder: avalon6
---

## Configuring Batch Ingest

The data for Batch Ingest is stored within an SQL database. Manifest Files are registered in the BatchRegistries table, and individual rows are stored in the BatchEntries table, linked by a key. Admins can view these tables to understand how the spreadsheets are ingested and how information is stored. See the `db/schema.rb` file for more information on these tables.

The different tasks that schedule Batch Ingest can be found in the `config/schedule.rb` file, and their times can be altered as desired:

* `avalon:batch:ingest` - checks for new spreadsheets
* `avalon:batch:ingest_status_check` - checks for completed batches, sends report emails
* `avalon:batch:ingest_stalled_check` - checks for stalled batches (no activity in 4 days), sends report emails
After a new spreadsheet is detected and validated, an IngestBatchEntryJob is queued as `:ingest`(for those who want to throttle jobs in the queue). If the job queue is lost, every row in BatchEntries with as `current_status` of `Queued` will need to be re-added to the job queue. The job is documented and defined in `app/jobs/ingest_batch_entry_job.rb`.


Every twenty-four hours, a task will check for Batch Ingest processes with no activity since the last check. Activity includes changes to the batch registry (username, collection, etc.) and changes to individual entries (entries succeeding or failing). For processes that have been inactive for 4 days or longer, an alert email will be sent to the notification email address for Avalon for all batches with no activity. This alert is informational only; it does not imply that anything is wrong.