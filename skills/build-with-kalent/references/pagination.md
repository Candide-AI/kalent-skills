# Pagination

One call returns at most 10 profiles (`nbToFetch` from 1 to 10). A 200 with 10 talents is not the end. A partial 200 is not the end either.

`estimationCount` is the pool size. It is capped at 10,000, and 10,000 means “10,000 or more”. Pagination continues past 10,000. Do not stop because the counter shows 10000.

Paginate by repeating the same prompt (or the same filters) with `relatedSearchTransactionIds`, accumulating every `searchTransactionId`. Maximum 300 ids.

Stop only when `resultCompleteness` is partial with reason `pool_exhausted`, or you have enough profiles, or credits run out.

The same prompt can shift the pool between calls. Transaction ids prevent duplicates. They do not freeze the pool.

Scoring only the first page and concluding the pool is small is a real failure.
