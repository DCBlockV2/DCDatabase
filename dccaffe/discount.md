# discount table schema

## discount table
```sql
CREATE TABLE public.discount
(
    menu_index bigint NOT NULL,
    discount bigint NOT NULL,
    company text COLLATE pg_catalog."default",
    reg_date timestamp without time zone DEFAULT now(),
    update_date timestamp without time zone DEFAULT now(),
    CONSTRAINT uk_index_company UNIQUE (menu_index, company)
,
    CONSTRAINT fk_index FOREIGN KEY (menu_index)
        REFERENCES public.menus (index) MATCH SIMPLE
        ON UPDATE NO ACTION
        ON DELETE NO ACTION
)
WITH (
    OIDS = FALSE
)
TABLESPACE pg_default;

ALTER TABLE public.discount OWNER to manager;

GRANT INSERT, SELECT, UPDATE, DELETE ON TABLE public.discount TO dccaffe;

GRANT ALL ON TABLE public.discount TO manager;

CREATE INDEX fki_fk_menu_index
    ON public.discount USING btree
    (menu_index)
    TABLESPACE pg_default;
```

## default data
```sql

INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (21, 0, 'covision', '2019-01-11 13:10:58.864244', '2019-01-14 13:31:11.529635');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (22, 1000, 'digicap', '2019-01-11 13:10:58.864244', '2019-01-14 13:31:11.529635');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (22, 0, 'covision', '2019-01-11 13:10:58.864244', '2019-01-14 13:31:11.529635');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (23, 1000, 'digicap', '2019-01-11 13:10:58.864244', '2019-01-14 13:31:11.529635');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (23, 0, 'covision', '2019-01-11 13:10:58.864244', '2019-01-14 13:31:11.529635');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (40, 1000, 'digicap', '2019-01-11 00:34:06.540663', '2019-01-11 13:07:00.198434');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (40, 0, 'covision', '2019-01-11 01:45:56.49245', '2019-01-11 13:07:00.198434');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (24, 1000, 'digicap', '2019-01-11 13:10:18.256401', '2019-01-11 13:10:18.256401');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (24, 0, 'covision', '2019-01-11 13:10:18.256401', '2019-01-11 13:10:18.256401');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (25, 1000, 'digicap', '2019-01-11 13:10:18.256401', '2019-01-11 13:10:18.256401');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (25, 0, 'covision', '2019-01-11 13:10:18.256401', '2019-01-11 13:10:18.256401');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (26, 1000, 'digicap', '2019-01-11 13:10:18.256401', '2019-01-11 13:10:18.256401');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (26, 0, 'covision', '2019-01-11 13:10:18.256401', '2019-01-11 13:10:18.256401');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (27, 1000, 'digicap', '2019-01-11 13:10:18.256401', '2019-01-11 13:10:18.256401');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (27, 0, 'covision', '2019-01-11 13:10:18.256401', '2019-01-11 13:10:18.256401');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (29, 1000, 'digicap', '2019-01-11 13:10:18.256401', '2019-01-11 13:10:18.256401');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (29, 0, 'covision', '2019-01-11 13:10:18.256401', '2019-01-11 13:10:18.256401');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (30, 1000, 'digicap', '2019-01-11 13:10:18.256401', '2019-01-11 13:10:18.256401');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (30, 0, 'covision', '2019-01-11 13:10:18.256401', '2019-01-11 13:10:18.256401');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (31, 1000, 'digicap', '2019-01-11 13:10:18.256401', '2019-01-11 13:10:18.256401');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (31, 0, 'covision', '2019-01-11 13:10:18.256401', '2019-01-11 13:10:18.256401');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (32, 1000, 'digicap', '2019-01-11 13:10:18.256401', '2019-01-11 13:10:18.256401');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (32, 0, 'covision', '2019-01-11 13:10:18.256401', '2019-01-11 13:10:18.256401');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (33, 1000, 'digicap', '2019-01-11 13:10:18.256401', '2019-01-11 13:10:18.256401');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (33, 0, 'covision', '2019-01-11 13:10:18.256401', '2019-01-11 13:10:18.256401');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (13, 1000, 'digicap', '2019-01-11 13:12:10.215827', '2019-01-11 13:12:10.215827');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (13, 0, 'covision', '2019-01-11 13:12:10.215827', '2019-01-11 13:12:10.215827');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (9, 1000, 'digicap', '2019-01-11 13:12:10.215827', '2019-01-11 13:12:10.215827');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (9, 0, 'covision', '2019-01-11 13:12:10.215827', '2019-01-11 13:12:10.215827');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (10, 1000, 'digicap', '2019-01-11 13:12:10.215827', '2019-01-11 13:12:10.215827');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (10, 0, 'covision', '2019-01-11 13:12:10.215827', '2019-01-11 13:12:10.215827');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (11, 1000, 'digicap', '2019-01-11 13:12:10.215827', '2019-01-11 13:12:10.215827');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (11, 0, 'covision', '2019-01-11 13:12:10.215827', '2019-01-11 13:12:10.215827');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (12, 1000, 'digicap', '2019-01-11 13:12:10.215827', '2019-01-11 13:12:10.215827');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (12, 0, 'covision', '2019-01-11 13:12:10.215827', '2019-01-11 13:12:10.215827');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (14, 1000, 'digicap', '2019-01-11 13:12:10.215827', '2019-01-11 13:12:10.215827');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (14, 0, 'covision', '2019-01-11 13:12:10.215827', '2019-01-11 13:12:10.215827');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (15, 1000, 'digicap', '2019-01-11 13:12:10.215827', '2019-01-11 13:12:10.215827');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (15, 0, 'covision', '2019-01-11 13:12:10.215827', '2019-01-11 13:12:10.215827');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (16, 1000, 'digicap', '2019-01-11 13:12:10.215827', '2019-01-11 13:12:10.215827');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (16, 0, 'covision', '2019-01-11 13:12:10.215827', '2019-01-11 13:12:10.215827');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (17, 1000, 'digicap', '2019-01-11 13:12:10.215827', '2019-01-11 13:12:10.215827');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (17, 0, 'covision', '2019-01-11 13:12:10.215827', '2019-01-11 13:12:10.215827');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (18, 1000, 'digicap', '2019-01-11 13:12:10.215827', '2019-01-11 13:12:10.215827');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (18, 0, 'covision', '2019-01-11 13:12:10.215827', '2019-01-11 13:12:10.215827');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (19, 1000, 'digicap', '2019-01-11 13:12:10.215827', '2019-01-11 13:12:10.215827');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (19, 0, 'covision', '2019-01-11 13:12:10.215827', '2019-01-11 13:12:10.215827');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (20, 1000, 'digicap', '2019-01-11 13:12:10.215827', '2019-01-11 13:12:10.215827');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (20, 0, 'covision', '2019-01-11 13:12:10.215827', '2019-01-11 13:12:10.215827');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (1, 1000, 'digicap', '2019-01-11 13:13:03.95766', '2019-01-11 13:13:03.95766');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (1, 0, 'covision', '2019-01-11 13:13:03.95766', '2019-01-11 13:13:03.95766');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (2, 1000, 'digicap', '2019-01-11 13:13:03.95766', '2019-01-11 13:13:03.95766');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (2, 0, 'covision', '2019-01-11 13:13:03.95766', '2019-01-11 13:13:03.95766');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (4, 1000, 'digicap', '2019-01-11 13:13:03.95766', '2019-01-11 13:13:03.95766');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (4, 0, 'covision', '2019-01-11 13:13:03.95766', '2019-01-11 13:13:03.95766');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (5, 1000, 'digicap', '2019-01-11 13:13:03.95766', '2019-01-11 13:13:03.95766');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (5, 0, 'covision', '2019-01-11 13:13:03.95766', '2019-01-11 13:13:03.95766');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (6, 1000, 'digicap', '2019-01-11 13:13:03.95766', '2019-01-11 13:13:03.95766');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (6, 0, 'covision', '2019-01-11 13:13:03.95766', '2019-01-11 13:13:03.95766');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (7, 1000, 'digicap', '2019-01-11 13:13:03.95766', '2019-01-11 13:13:03.95766');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (7, 0, 'covision', '2019-01-11 13:13:03.95766', '2019-01-11 13:13:03.95766');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (8, 1000, 'digicap', '2019-01-11 13:13:03.95766', '2019-01-11 13:13:03.95766');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (8, 0, 'covision', '2019-01-11 13:13:03.95766', '2019-01-11 13:13:03.95766');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (42, 0, 'digicap', '2019-01-11 13:13:51.588421', '2019-01-11 13:13:51.588421');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (42, 0, 'covision', '2019-01-11 13:13:51.588421', '2019-01-11 13:13:51.588421');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (41, 0, 'digicap', '2019-01-11 13:13:51.588421', '2019-01-11 13:13:51.588421');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (41, 0, 'covision', '2019-01-11 13:13:51.588421', '2019-01-11 13:13:51.588421');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (43, 0, 'digicap', '2019-01-11 13:13:51.588421', '2019-01-11 13:13:51.588421');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (43, 0, 'covision', '2019-01-11 13:13:51.588421', '2019-01-11 13:13:51.588421');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (44, 0, 'digicap', '2019-01-11 13:13:51.588421', '2019-01-11 13:13:51.588421');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (44, 0, 'covision', '2019-01-11 13:13:51.588421', '2019-01-11 13:13:51.588421');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (38, 1000, 'digicap', '2019-01-11 13:08:59.704957', '2019-01-23 10:48:15.334176');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (38, 0, 'covision', '2019-01-11 13:08:59.704957', '2019-01-23 10:48:15.334176');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (39, 1000, 'digicap', '2019-01-11 13:08:59.704957', '2019-01-23 10:48:15.334176');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (39, 0, 'covision', '2019-01-11 13:08:59.704957', '2019-01-23 10:48:15.334176');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (21, 1000, 'digicap', '2019-01-11 13:10:58.864244', '2019-01-14 13:31:11.529635');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (35, 1000, 'digicap', '2019-01-11 12:56:01.28626', '2019-01-23 10:48:15.334176');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (35, 0, 'covision', '2019-01-11 13:08:59.704957', '2019-01-23 10:48:15.334176');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (37, 1000, 'digicap', '2019-01-11 13:08:59.704957', '2019-01-23 10:48:15.334176');
INSERT INTO public.discount (menu_index, discount, company, reg_date, update_date) VALUES (37, 0, 'covision', '2019-01-11 13:08:59.704957', '2019-01-23 10:48:15.334176');
```