# orders table schema

## order_seq
```sql
DROP SEQUENCE IF EXISTS public.order_seq;

CREATE SEQUENCE IF NOT EXISTS public.order_seq START 1;

-- If create sequence with no owner, use this
--ALTER SEQUENCE public.order_seq OWNER TO manager;

GRANT UPDATE, SELECT ON SEQUENCE public.order_seq TO dckitchen;

SELECT NEXTVAL('order_seq');
SELECT CURRVAL('order_seq');
SELECT SETVAL('order_seq', 1);
--SELECT pg_catalog.setval('public.order_seq', 1, false);
--SELECT pg_catalog.setval('public.order_seq', 1, true);
```

## orders table
```sql
DROP TABLE IF EXISTS orders;
CREATE TABLE IF NOT EXISTS orders (
    order_id BIGINT NOT NULL DEFAULT NEXTVAL('order_seq'),
    user_info jsonb NOT NULL,
    order_date DATE NOT NULL DEFAULT CURRENT_DATE,
    receipt_id BIGINT NOT NULL,
    order_data jsonb NOT NULL,
    order_status INT NOT NULL,
    pending_date TIMESTAMP WITH TIME ZONE NOT NULL DEFAULT CURRENT_TIMESTAMP,
    complete_date TIMESTAMP WITH TIME ZONE,
    cancel_date TIMESTAMP WITH TIME ZONE,
    CONSTRAINT order_pk PRIMARY KEY (order_id),
    CONSTRAINT order_uk UNIQUE (order_date, receipt_id)
    )
WITH (
    OIDS = FALSE
)
TABLESPACE pg_default;

ALTER TABLE public.orders OWNER to manager;

GRANT ALL ON TABLE public.orders TO manager;

GRANT INSERT, SELECT, UPDATE, DELETE ON TABLE public.orders TO dckitchen;

CREATE INDEX order_date_idx 
    ON public.orders
    USING btree (order_date)
    TABLESPACE pg_default;
```

## example data
```sql
INSERT INTO "orders" ("order_id", "user_info", "order_date", "receipt_id", "order_data", "order_status", "pending_date", "complete_date", "cancel_date") VALUES (322, '{"rfid": "e34995e4568945802195a33d7b4e109ae52137c1e4e029e3b08e9c28d55bba64", "employee_id": null}', '2024-08-14', 19, '{"date": 1723659289682, "name": "권남훈", "company": "digicap", "purchases": [{"code": 1, "count": 5, "price": 2500, "category": 100, "opt_size": "REGULAR", "opt_type": "BOTH"}, {"code": 8, "count": 1, "price": 2500, "category": 200, "opt_size": "REGULAR", "opt_type": "BOTH"}], "receipt_id": 19, "purchase_type": 0}', 20, '2024-08-14 09:14:50+00', NULL, '2024-08-14 09:15:36+00');
INSERT INTO "orders" ("order_id", "user_info", "order_date", "receipt_id", "order_data", "order_status", "pending_date", "complete_date", "cancel_date") VALUES (321, '{"rfid": "e34995e4568945802195a33d7b4e109ae52137c1e4e029e3b08e9c28d55bba64", "employee_id": null}', '2024-08-14', 18, '{"date": 1723659188758, "name": "권남훈", "company": "digicap", "purchases": [{"code": 1, "count": 5, "price": 2500, "category": 100, "opt_size": "REGULAR", "opt_type": "BOTH"}, {"code": 8, "count": 1, "price": 2500, "category": 200, "opt_size": "REGULAR", "opt_type": "BOTH"}], "receipt_id": 18, "purchase_type": 0}', 40, '2024-08-14 09:13:09+00', '2024-08-14 09:13:12+00', '2024-08-14 09:13:22+00');
INSERT INTO "orders" ("order_id", "user_info", "order_date", "receipt_id", "order_data", "order_status", "pending_date", "complete_date", "cancel_date") VALUES (319, '{"rfid": "e34995e4568945802195a33d7b4e109ae52137c1e4e029e3b08e9c28d55bba64", "employee_id": null}', '2024-08-14', 16, '{"date": 1723658901074, "name": "권남훈", "company": "digicap", "purchases": [{"code": 1, "count": 5, "price": 2500, "category": 100, "opt_size": "REGULAR", "opt_type": "BOTH"}, {"code": 8, "count": 1, "price": 2500, "category": 200, "opt_size": "REGULAR", "opt_type": "BOTH"}], "receipt_id": 16, "purchase_type": 0}', 30, '2024-08-14 09:08:21+00', '2024-08-14 09:12:30+00', NULL);
```