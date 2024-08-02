# temporary_uri table schema

## purchase_receipt_id 
```sql
CREATE SEQUENCE public.purchase_receipt_id;

ALTER SEQUENCE public.purchase_receipt_id OWNER TO manager;

GRANT ALL ON SEQUENCE public.purchase_receipt_id TO manager;

GRANT UPDATE, SELECT ON SEQUENCE public.purchase_receipt_id TO dccaffe;

SELECT pg_catalog.setval('public.purchase_receipt_id', 0, false);
```

## temporary_uri table
```sql
CREATE TABLE public.temporary_uri
(
    user_record_index bigint NOT NULL,
    reg_date timestamp with time zone NOT NULL DEFAULT now(),
    name text COLLATE pg_catalog."default",
    random_uri text COLLATE pg_catalog."default",
    search_date_after timestamp with time zone,
    search_date_before timestamp with time zone
)
WITH (
    OIDS = FALSE
)
TABLESPACE pg_default;

ALTER TABLE public.temporary_uri OWNER to manager;

GRANT INSERT, SELECT, UPDATE, DELETE ON TABLE public.temporary_uri TO dccaffe;

GRANT ALL ON TABLE public.temporary_uri TO manager;
```

## example data
```sql
```