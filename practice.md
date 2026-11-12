# library: three claims

## members

`status` says whether a membership is current: `active` or `lapsed`.

## loans

Every `member_ref` is a `member_id` in `members`. The query that shows it:

```sql
SELECT count(*) FROM loans l LEFT JOIN members m ON m.member_id = l.member_ref WHERE m.member_id IS NULL;
```

## The rule on loans

`fk_loans_member` refuses a loan whose `member_ref` is not a `member_id` in `members`.
