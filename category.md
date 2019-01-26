# category table schema

## category_code_seq 
```sql
CREATE SEQUENCE public.category_code_seq;

ALTER SEQUENCE public.category_code_seq OWNER TO manager;

ALTER SEQUENCE public.category_code_seq INCREMENT 100;

GRANT ALL ON SEQUENCE public.category_code_seq TO manager;

GRANT UPDATE, SELECT ON SEQUENCE public.category_code_seq TO dccaffe;

SELECT pg_catalog.setval('public.category_code_seq', 700, false);
```

## category table
```sql
CREATE TABLE public.category
(
    "order" integer NOT NULL,
    name text COLLATE pg_catalog."default" NOT NULL,
    code bigint NOT NULL DEFAULT nextval('category_code_seq'::regclass),
    CONSTRAINT pk_code PRIMARY KEY (code)
)
WITH (
    OIDS = FALSE
)
TABLESPACE pg_default;

ALTER TABLE public.category OWNER to manager;

GRANT INSERT, SELECT, UPDATE, DELETE ON TABLE public.category TO dccaffe;

GRANT ALL ON TABLE public.category TO manager;
```

## default data
```sql
INSERT INTO public.category ("order", name, code) VALUES (6, 'Cookie&Bakery', 700);
INSERT INTO public.category ("order", name, code) VALUES (1, 'Tea', 200);
INSERT INTO public.category ("order", name, code) VALUES (0, 'Coffee', 100);
INSERT INTO public.category ("order", name, code) VALUES (2, 'Drink', 300);
INSERT INTO public.category ("order", name, code) VALUES (3, 'Smoothie', 400);
INSERT INTO public.category ("order", name, code) VALUES (4, 'Ade', 500);
INSERT INTO public.category ("order", name, code) VALUES (5, 'Bubble Tea', 600);
```