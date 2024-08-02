# purchases table schema

## purchases_index_seq 
```sql
CREATE SEQUENCE public.purchases_index_seq;

ALTER SEQUENCE public.purchases_index_seq
    OWNER TO manager;

GRANT ALL ON SEQUENCE public.purchases_index_seq TO manager;

GRANT UPDATE, SELECT ON SEQUENCE public.purchases_index_seq TO dccaffe;

SELECT pg_catalog.setval('public.Users_Index_seq', 0, false);
```

## purchases table
```sql
CREATE TABLE public.purchases
(
    count integer,
    price integer,
    dc_price integer,
    name text COLLATE pg_catalog."default",
    user_record_index bigint,
    code integer,
    menu_name_kr text COLLATE pg_catalog."default",
    receipt_status integer NOT NULL DEFAULT 0,
    opt_size integer,
    opt_type integer,
    update_date timestamp with time zone NOT NULL DEFAULT now(),
    cancel_date timestamp with time zone,
    purchase_date timestamp with time zone DEFAULT now(),
    canceled_date timestamp with time zone,
    index bigint NOT NULL DEFAULT nextval('purchases_index_seq'::regclass),
    receipt_id bigint,
    category bigint,
    random_id text COLLATE pg_catalog."default",
    purchase_type integer,
    email text COLLATE pg_catalog."default",
    company text COLLATE pg_catalog."default",
    CONSTRAINT receipt_random_id UNIQUE (receipt_id, random_id)

)
WITH (
    OIDS = FALSE
)
TABLESPACE pg_default;

ALTER TABLE public.purchases OWNER to manager;

GRANT INSERT, SELECT, UPDATE, DELETE ON TABLE public.purchases TO dccaffe;

GRANT ALL ON TABLE public.purchases TO manager;

CREATE INDEX "fki_Purchases_UserIndex"
    ON public.purchases USING btree
    (user_record_index)
    TABLESPACE pg_default;
```

## example data
```sql
```