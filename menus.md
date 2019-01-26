# menus table schema

## Menus_Index_seq 
```sql
CREATE SEQUENCE public."Menus_Index_seq";

ALTER SEQUENCE public."Menus_Index_seq" OWNER TO manager;

GRANT ALL ON SEQUENCE public."Menus_Index_seq" TO manager;

GRANT UPDATE, SELECT ON SEQUENCE public."Menus_Index_seq" TO dccaffe;

SELECT pg_catalog.setval('public."Menus_Index_seq"', 88, true);
```

## menus table
```sql
CREATE TABLE public.menus
(
    name_en text COLLATE pg_catalog."default" NOT NULL,
    name_kr text COLLATE pg_catalog."default" NOT NULL,
    price integer NOT NULL,
    dc_digicap integer,
    dc_covision integer,
    reg_date timestamp with time zone NOT NULL DEFAULT now(),
    update_date timestamp with time zone NOT NULL DEFAULT now(),
    category integer NOT NULL,
    "order" integer NOT NULL,
    code integer NOT NULL DEFAULT nextval('menu_code_seq'::regclass),
    index bigint NOT NULL DEFAULT nextval('"Menus_Index_seq"'::regclass),
    opt_size integer NOT NULL,
    opt_type integer NOT NULL,
    event_name text COLLATE pg_catalog."default",
    CONSTRAINT "Index" PRIMARY KEY (index),
    CONSTRAINT uk_category_code UNIQUE (category, code)
,
    CONSTRAINT fk_category FOREIGN KEY (category)
        REFERENCES public.category (code) MATCH SIMPLE
        ON UPDATE NO ACTION
        ON DELETE NO ACTION
)
WITH (
    OIDS = FALSE
)
TABLESPACE pg_default;

ALTER TABLE public.menus
    OWNER to manager;

GRANT INSERT, SELECT, UPDATE, DELETE ON TABLE public.menus TO dccaffe;

GRANT ALL ON TABLE public.menus TO manager;

CREATE INDEX "fki_Category" ON public.menus USING btree
    (category)
    TABLESPACE pg_default;
```

## example data
```sql
NSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('juice', '주스', 3000, 1000, 0, '2018-11-16 05:59:02.950534+00', '2018-11-16 05:59:02.950534+00', 300, 0, 2, 22, 0, 1, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('rooibos', '루이보스', 2500, 1000, 0, '2018-11-15 15:30:17.034955+00', '2018-11-15 15:30:17.034955+00', 200, 1, 8, 9, 0, 2, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('green tea', '녹차', 2500, 1000, 0, '2018-11-15 15:30:44.595946+00', '2018-11-15 15:30:44.595946+00', 200, 2, 9, 10, 0, 2, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('earl gray', '얼그레이', 2500, 1000, 0, '2018-11-15 15:31:17.037031+00', '2018-11-15 15:31:17.037031+00', 200, 3, 10, 11, 0, 2, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('chamomile', '카모마일', 2500, 1000, 0, '2018-11-15 15:31:48.454424+00', '2018-11-15 15:31:48.454424+00', 200, 4, 11, 12, 0, 2, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('sparkling water', '탄산수', 3000, 1000, 0, '2018-11-16 05:59:25.971071+00', '2018-11-16 05:59:25.971071+00', 300, 2, 3, 23, 0, 1, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('Strawberry', '딸기', 3000, 1000, 0, '2018-11-16 06:00:10.572395+00', '2018-11-16 06:00:10.572395+00', 400, 0, 1, 24, 0, 1, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('Strawberry banana', '딸기 바나나', 3000, 1000, 0, '2018-11-16 06:00:31.540516+00', '2018-11-16 06:00:31.540516+00', 400, 1, 2, 25, 0, 1, '여름 추천');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('hibiscus', '히비스커스', 2500, 1000, 0, '2018-11-15 15:32:13.683579+00', '2018-11-15 15:32:13.683579+00', 200, 0, 12, 13, 0, 2, '여성 건강 추천');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('peach', '복숭아', 2500, 1000, 0, '2018-11-15 15:32:36.428509+00', '2018-11-15 15:32:36.428509+00', 200, 5, 13, 14, 0, 2, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('citron', '유자', 3300, 1000, 0, '2018-11-15 15:33:17.619865+00', '2018-11-15 15:33:17.619865+00', 200, 6, 14, 15, 0, 2, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('lemon', '레몬', 3300, 1000, 0, '2018-11-15 15:33:36.416801+00', '2018-11-15 15:33:36.416801+00', 200, 7, 15, 16, 0, 2, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('taro', '타로', 3300, 1000, 0, '2018-11-16 06:08:06.457925+00', '2018-11-16 06:08:06.457925+00', 600, 1, 1, 40, 0, 1, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('apple mango', '애플망고', 3000, 1000, 0, '2018-11-16 06:00:54.163349+00', '2018-11-16 06:00:54.163349+00', 400, 2, 3, 26, 0, 1, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('kiwi', '키위', 3000, 1000, 0, '2018-11-16 06:01:13.247256+00', '2018-11-16 06:01:13.247256+00', 400, 3, 4, 27, 0, 1, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('peach', '복숭아', 3000, 1000, 0, '2018-11-16 06:02:09.012545+00', '2018-11-16 06:02:09.012545+00', 400, 4, 5, 29, 0, 1, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('grapefruit', '자몽', 3300, 1000, 0, '2018-11-16 06:05:31.111573+00', '2018-11-16 06:05:31.111573+00', 500, 0, 1, 35, 0, 1, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('lemon', '레몬', 3300, 1000, 0, '2018-11-16 06:06:40.602653+00', '2018-11-16 06:06:40.602653+00', 500, 1, 2, 37, 0, 2, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('espreso', '에스프레소', 2500, 1000, 0, '2018-11-15 15:20:57.075281+00', '2018-11-15 15:20:57.075281+00', 100, 0, 1, 1, 0, 2, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('americano', '아메리카노', 2500, 1000, 0, '2018-11-15 15:23:45.601289+00', '2018-11-15 15:23:45.601289+00', 100, 1, 2, 2, 0, 2, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('white grapes', '청포도', 3000, 1000, 0, '2018-11-16 06:03:30.959367+00', '2018-11-16 06:03:30.959367+00', 400, 5, 6, 30, 0, 1, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('cookie and cream', '쿠키앤크림', 3300, 1000, 0, '2018-11-16 06:03:55.914204+00', '2018-11-16 06:03:55.914204+00', 400, 6, 7, 31, 0, 1, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('java chip', '자바칩', 3300, 1000, 0, '2018-11-16 06:04:18.174703+00', '2018-11-16 06:04:18.174703+00', 400, 7, 8, 32, 0, 1, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('apple mango yogurt', '애플망고요거트', 3300, 1000, 0, '2018-11-16 06:04:40.958579+00', '2018-11-16 06:04:40.958579+00', 400, 8, 9, 33, 0, 1, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('americano(small)', '아메리카노', 2000, 1000, 0, '2018-11-15 15:25:27.490971+00', '2018-11-15 15:25:27.490971+00', 100, 2, 3, 4, 1, 0, '굳모닝 이벤트');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('caffee latte', '까페라떼', 3000, 1000, 0, '2018-11-15 15:26:16.516409+00', '2018-11-15 15:26:16.516409+00', 100, 3, 4, 5, 0, 2, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('cookie', '쿠키', 1000, 0, 0, '2018-11-16 06:08:28.761197+00', '2018-11-16 06:08:28.761197+00', 700, 1, 1, 41, 0, 0, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('fescopy', '페스츄피', 1500, 0, 0, '2018-11-16 06:08:49.891475+00', '2018-11-16 06:08:49.891475+00', 700, 0, 2, 42, 0, 0, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('royal milky', '로얄 밀크티', 3300, 1000, 0, '2018-11-15 15:33:59.937893+00', '2018-11-15 15:33:59.937893+00', 200, 8, 16, 17, 0, 2, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('sandwich1', '샌드위치1', 4500, 0, 0, '2018-11-16 06:09:12.945656+00', '2018-11-16 06:09:12.945656+00', 700, 2, 3, 43, 0, 0, '마감 임박');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('citron', '유자', 3300, 1000, 0, '2018-11-16 06:06:59.559973+00', '2018-11-16 06:06:59.559973+00', 500, 2, 3, 38, 0, 2, '겨울 감기 예방 추천');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('white grapes', '청포도', 3300, 1000, 0, '2018-11-16 06:07:31.528204+00', '2018-11-16 06:07:31.528204+00', 500, 3, 4, 39, 0, 1, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('vanilla latte', '바닐라라떼', 3300, 1000, 0, '2018-11-15 15:27:16.432018+00', '2018-11-15 15:27:16.432018+00', 100, 4, 5, 6, 0, 2, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('cafe mocha', '까페모카', 3300, 1000, 0, '2018-11-15 15:27:56.841799+00', '2018-11-15 15:27:56.841799+00', 100, 5, 6, 7, 0, 2, 'MD 추천');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('sandwich2', '샌드위치2', 4500, 0, 0, '2018-12-20 02:36:18.349874+00', '2018-12-20 02:36:18.349874+00', 700, 3, 4, 44, 0, 0, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('melther flower', '멜더플라워', 3300, 1000, 0, '2018-11-15 15:34:37.880733+00', '2018-11-15 15:34:37.880733+00', 200, 9, 17, 18, 0, 2, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('caramel makiato', '카라멜 마끼아또', 3300, 1000, 0, '2018-11-15 15:29:07.024264+00', '2018-11-15 15:29:07.024264+00', 100, 6, 7, 8, 0, 2, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('citrus', '청귤', 3300, 1000, 0, '2018-11-15 15:35:10.427158+00', '2018-11-15 15:35:10.427158+00', 200, 10, 18, 19, 0, 2, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('indian chai latte', '인디안 차이라떼', 3000, 1000, 0, '2018-11-15 15:35:51.564571+00', '2018-11-15 15:35:51.564571+00', 200, 11, 19, 20, 0, 2, '');
INSERT INTO public.menus (name_en, name_kr, price, dc_digicap, dc_covision, reg_date, update_date, category, "order", code, index, opt_size, opt_type, event_name) VALUES ('carbonated drink', '탄산음료', 1000, 1000, 0, '2018-11-16 05:58:41.809197+00', '2018-11-16 05:58:41.809197+00', 300, 1, 1, 21, 0, 2, '');
```