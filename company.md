# company table schema

## company_index_seq 
```sql
CREATE SEQUENCE public.company_index_seq;

ALTER SEQUENCE public.company_index_seq OWNER TO manager;

GRANT UPDATE, SELECT ON SEQUENCE public.company_index_seq TO dcadmin;

GRANT ALL ON SEQUENCE public.company_index_seq TO manager;

SELECT pg_catalog.setval('public.company_index_seq', 3, false);
```

## company table
```sql
CREATE TABLE public.company
(
    index bigint NOT NULL,
    name_en text COLLATE pg_catalog."default" NOT NULL,
    name_kr text COLLATE pg_catalog."default" NOT NULL,
    reg_date timestamp with time zone NOT NULL DEFAULT now(),
    update_date timestamp with time zone NOT NULL DEFAULT now(),
    code smallint NOT NULL,
    CONSTRAINT pk_company_code PRIMARY KEY (code)
)
WITH (
    OIDS = FALSE
)
TABLESPACE pg_default;

ALTER TABLE public.company OWNER to manager;

GRANT INSERT, SELECT, UPDATE, DELETE ON TABLE public.company TO dcadmin;

GRANT ALL ON TABLE public.company TO manager;
```

## default data
```sql
INSERT INTO public.company (name_en, name_kr, reg_date, update_date, code) VALUES (1, 'digicap', '디지캡', '2019-01-04 10:25:16.889603+00', '2019-01-04 10:25:16.889603+00', 1);
INSERT INTO public.company (name_en, name_kr, reg_date, update_date, code) VALUES (2, 'covision', '코비전', '2019-01-04 10:25:27.859652+00', '2019-01-04 10:25:27.859652+00', 2);
```