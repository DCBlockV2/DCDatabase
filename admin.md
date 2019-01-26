# admin table schema

## Admin_Index_seq 
```sql
CREATE SEQUENCE public."Admin_Index_seq";

ALTER SEQUENCE public."Admin_Index_seq" OWNER TO manager;

GRANT UPDATE, SELECT ON SEQUENCE public."Admin_Index_seq" TO dcadmin;

GRANT ALL ON SEQUENCE public."Admin_Index_seq" TO manager;

SELECT pg_catalog.setval('public.Admin_Index_seq', 0, false);
```

## admin table
```sql
CREATE TABLE public.admin
(
    index bigint NOT NULL DEFAULT nextval('"Admin_Index_seq"'::regclass),
    id text COLLATE pg_catalog."default" NOT NULL,
    password text COLLATE pg_catalog."default",
    name text COLLATE pg_catalog."default",
    email text COLLATE pg_catalog."default",
    company text COLLATE pg_catalog."default",
    scope text COLLATE pg_catalog."default",
    regdate timestamp with time zone,
    updatedate timestamp with time zone,
    manageuser boolean DEFAULT false,
    managemenu boolean DEFAULT false,
    viewstatistics boolean DEFAULT false,
    manageadmin boolean DEFAULT false,
    CONSTRAINT admin_pkey PRIMARY KEY (index, id),
    CONSTRAINT unique_id UNIQUE (id)

)
WITH (
    OIDS = FALSE
)
TABLESPACE pg_default;

ALTER TABLE public.admin
    OWNER to manager;

GRANT INSERT, SELECT, UPDATE, DELETE ON TABLE public.admin TO dcadmin;

GRANT ALL ON TABLE public.admin TO manager;
```

## default data
```sql
INSERT INTO public.admin (id, password, name, email, company, scope, regdate, updatedate, manageuser, managemenu, viewstatistics, manageadmin) VALUES ('admin', 'ac9689e2272427085e35b9d3e3e8bed88cb3434828b43b86fc0596cad4c6e270', 'ADMIN', 'admin@digicaps.com', 'DigiCAP', 'ADMIN', '2018-12-19 05:49:39.380165+00', '2018-12-19 05:49:39.380165+00', true, true, true, true);
INSERT INTO public.admin (id, password, name, email, company, scope, regdate, updatedate, manageuser, managemenu, viewstatistics, manageadmin) VALUES ('cherry', '2daf0e6c79009f9234ed9baa5bb930898e2847810617e118518d88e4d3140a2e', 'Jung', 'cheery@digicaps.com', 'DigiCAP', 'OPERATOR', '2018-12-19 05:49:47.371338+00', '2018-12-19 05:49:47.371338+00', true, true, true, false);
INSERT INTO public.admin (id, password, name, email, company, scope, regdate, updatedate, manageuser, managemenu, viewstatistics, manageadmin) VALUES ('covision', '4b4b42f620114dcaf0bd54e88c55e8ed90765ea2f1c244442d51ab59597e648c', 'Hong', 'covision@covision.com', 'COVISION', 'OPERATOR', '2018-12-19 05:49:51.108309+00', '2018-12-19 05:49:51.108309+00', false, false, true, false);
INSERT INTO public.admin (id, password, name, email, company, scope, regdate, updatedate, manageuser, managemenu, viewstatistics, manageadmin) VALUES ('testuser', 'ae5deb822e0d71992900471a7199d0d95b8e7c9d05c40a8245a281fd2c1d6684', 'Shin', 'testuser1@digicaps.com', 'DigiCAP', 'USER', '2018-12-19 05:49:56.189522+00', '2018-12-19 05:49:56.189522+00', false, false, false, false);
```