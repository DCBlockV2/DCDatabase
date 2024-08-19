-- ### First of all, Create database and user ### --
-- # Check current
SELECT CURRENT_USER;
SELECT CURRENT_DATABASE();
SELECT * FROM pg_catalog.pg_tables WHERE schemaname = 'public';
SELECT * FROM information_schema.sequences;

-- # Create database
--DROP DATABASE IF EXISTS dckitchen;
CREATE DATABASE dckitchen OWNER manager;

-- If create database with no owner, use this
--ALTER DATABASE dckitchen OWNER to manager;

-- If grant all, must connected to database dckitchen and grant.
--GRANT ALL ON SCHEMA public TO manager;
-- All on all tables
--GRANT ALL ON ALL TABLES IN SCHEMA public TO manager;
-- All on exact sequence
--GRANT ALL ON TABLE public.orders TO manager;
-- All on all sequences
--GRANT ALL ON ALL SEQUENCES IN SCHEMA public TO manager;
-- All on exact sequence
--GRANT ALL ON SEQUENCE public.order_seq TO manager;

-- # Create user
--DROP USER IF EXISTS dckitchen;
CREATE USER dckitchen WITH PASSWORD 'PASSWORD_HERE';