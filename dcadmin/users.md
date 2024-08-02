# users table schema

## Users_Index_seq 
```sql
CREATE SEQUENCE public."Users_Index_seq";

ALTER SEQUENCE public."Users_Index_seq" OWNER TO manager;

GRANT UPDATE, SELECT ON SEQUENCE public."Users_Index_seq" TO dcadmin;

GRANT ALL ON SEQUENCE public."Users_Index_seq" TO manager;

SELECT pg_catalog.setval('public.Users_Index_seq', 0, false);
```

## users table
```sql
CREATE TABLE IF NOT EXISTS public.users
(
    email text COLLATE pg_catalog."default",
    company text COLLATE pg_catalog."default" NOT NULL,
    rfid text COLLATE pg_catalog."default",
    regdate timestamp(4) with time zone NOT NULL DEFAULT now(),
    updatedate timestamp(4) with time zone DEFAULT now(),
    index bigint NOT NULL DEFAULT nextval('"Users_Index_seq"'::regclass),
    name text COLLATE pg_catalog."default",
    leave boolean DEFAULT false,
    employee_id text COLLATE pg_catalog."default",
    CONSTRAINT users_pkey PRIMARY KEY (index),
    CONSTRAINT "Users_Rfid" UNIQUE (rfid)
)
WITH (
    OIDS = FALSE
)
TABLESPACE pg_default;

ALTER TABLE IF EXISTS public.users
    OWNER to manager;

REVOKE ALL ON TABLE public.users FROM dcadmin;

GRANT DELETE, INSERT, SELECT, UPDATE ON TABLE public.users TO dcadmin;

GRANT ALL ON TABLE public.users TO manager;
```

## example data
```sql
INSERT INTO public.users (email, company, rfid, regdate, updatedate, name, leave, employee_id) VALUES ('thlee@digicaps.com', 'DigiCAP', '7f66b544bac405353e9b26713832cc973f75da225426e3ed952ba7a65389d9dd', '2019-01-25 12:29:52.1536+00', '2019-01-25 12:29:52.1536+00', '이태호', false, null);
INSERT INTO public.users (email, company, rfid, regdate, updatedate, name, leave, employee_id) VALUES ('smyeong@digicaps.com', 'DigiCAP', null, '2019-01-25 12:29:52.1536+00', '2019-01-25 12:29:52.1536+00', '이태호', false, 'e2217d3e4e120c6a3372a1890f03e232b35ad659d71f7a62501a4ee204a3e66d');
INSERT INTO public.users (email, company, rfid, regdate, updatedate, name, leave, employee_id) VALUES ('bojung@digicaps.com', 'DigiCAP', '50be65f3f60eaf7c632fc9a67c94ac7696762f1a3a445f91306cd0a20c089e67', '2019-01-25 12:30:24.5348+00', '2019-01-25 12:30:24.5348+00', '정병옥', false, null);

```