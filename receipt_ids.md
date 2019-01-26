# receipt_ids table schema

## receipt_ids table
```sql
CREATE TABLE public.receipt_ids
(
    name text COLLATE pg_catalog."default" NOT NULL,
    regdate timestamp with time zone NOT NULL DEFAULT now(),
    receipt_id bigint NOT NULL DEFAULT 0,
    user_record_index bigint NOT NULL DEFAULT 0,
    company text COLLATE pg_catalog."default",
    random_id text COLLATE pg_catalog."default",
    email text COLLATE pg_catalog."default",
    CONSTRAINT pk_receipt_id PRIMARY KEY (receipt_id),
    CONSTRAINT receipt_random_id_2 UNIQUE (receipt_id, random_id)

)
WITH (
    OIDS = FALSE
)
TABLESPACE pg_default;

ALTER TABLE public.receipt_ids
    OWNER to manager;

GRANT INSERT, SELECT, UPDATE, DELETE ON TABLE public.receipt_ids TO dccaffe;

GRANT ALL ON TABLE public.receipt_ids TO manager;
```

## example data
```sql
```