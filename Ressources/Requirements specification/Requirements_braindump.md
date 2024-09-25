### Requirements braindump

1. Every message should adhere to the following types within the db-schema and not be null:
- message_id: Integer
- author_id: Integer
- text: String
- pub_date: String
- flagged: Integer


2. When creating users the pass must be hased

**[Q]:** Do we need a relation/table for latest id? The Go Gorilla API expects a _Counts_ relation.