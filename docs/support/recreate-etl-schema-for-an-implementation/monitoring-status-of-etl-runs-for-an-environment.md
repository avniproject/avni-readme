---
title: Monitoring Status of ETL Runs for an environment
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
To monitor ETL runs across all organisations of an environment, use the reports below. Each opens in Metabase in a new window, and you need to sign in to Metabase to see it. Staging and Pre-release have a query instead of a report.

## Production

<a href="https://reporting.avniproject.org/question/4842" target="_blank" rel="noopener noreferrer">Latest ETL run details for all organisations, production</a>

## Staging and Pre-release

There is no report for these two environments. To see the latest ETL run for each organisation, run this query on that environment's database:

```sql
select organisation, category, status, last_run_start, last_run_end, success, last_successful_run, error_message from
    (select concat(og.name, ' ' , o.name) organisation,
            qjd.job_group as job_group,
            oc.id as oc_id,
            oc.name category,
            os.id as os_id,
            os.name status,
            to_char(sjr.started_at at time zone 'Asia/Kolkata', 'yyyy-mm-dd HH24:mi') last_run_start,
            to_char(sjr.ended_at at time zone 'Asia/Kolkata', 'yyyy-mm-dd HH24:mi') last_run_end,
            max(to_char(sjr.started_at at time zone 'Asia/Kolkata', 'yyyy-mm-dd HH24:mi')) filter ( where success = true ) over (partition by sjr.job_name) last_successful_run,
            sjr.success, sjr.error_message, rank() over (partition by sjr.job_name order by started_at desc ) rnk
     from scheduled_job_run sjr
              join qrtz_job_details qjd on sjr.job_name = qjd.job_name
              left join organisation o on sjr.job_name = o.uuid
              left join organisation_group og on sjr.job_name = og.uuid
              left join organisation_category oc on oc.id = o.category_id
              left join organisation_status os on os.id = o.status_id
     where sjr.started_at > current_timestamp - interval '1 month'
    ) a
where rnk = 1
  and coalesce(TRIM(organisation), '') <> ''
  and job_group = 'SyncJobs'
order by last_successful_run desc;
```

## RWB Prod

<a href="https://reporting.avniproject.org/question/5159" target="_blank" rel="noopener noreferrer">Latest ETL run details for all organisations, RWB production</a>

To look only at **failed** ETL runs for production Live and UAT organisations, use:

## Production ETL failures only

<a href="https://reporting.avniproject.org/question/4840" target="_blank" rel="noopener noreferrer">Latest ETL run failures, production Live and UAT organisations</a>
