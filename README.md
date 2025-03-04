# powerbi-prac
# Microsoft Data Visualization Professional Certificate
createtable.jpg
![image](https://github.com/user-attachments/assets/d27e1ea1-9916-4d50-900b-d78b10b5c021)
![image](https://github.com/user-attachments/assets/2d4b07ac-7e27-4e2d-8f61-b98cbee93bc2)

![image](https://github.com/user-attachments/assets/0fa69017-50a2-4f32-a209-e26bb9587ab3)
![image](https://github.com/user-attachments/assets/be7ce3a5-6f66-4044-b8cd-a70e26d4fdfe)
![image](https://github.com/user-attachments/assets/af24e203-ca01-4f19-926b-d309ccd84c38)
mysql --host=172.21.123.41 --port=3306 --user=root --password=FD92INu9rM1VI9LCuKQFGw15

------------------------
mongoimport --version
mongoexport --version
. Download catalog.json:
wget https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0321EN-SkillsNetwork/nosql/catalog.json
![image](https://github.com/user-attachments/assets/eb87b7a8-f4f4-40ba-91e1-38e814fbb8db)

mongosh mongodb://root:1pnTdpmO0aVLqO3KTyN8KCGD@172.21.196.57:27017
![image](https://github.com/user-attachments/assets/f8bee1ba-4fde-445a-9371-0c8868ac3a95)
![image](https://github.com/user-attachments/assets/4dc6b9f2-9308-4356-b057-3d205f535ae8)
mongoimport --host 172.21.196.57 --port 27017 --username root --password 1pnTdpmO0aVLqO3KTyN8KCGD --authenticationDatabase admin --authenticationMechanism SCRAM-SHA-256 --db catalog --collection electronics --file catalog_fixed.json --jsonArray
https://labs-mongo-dry-millions-match.mongo.databases.labs.skills.network/

# Stagging Warehouse using pgAdmin4
![image](https://github.com/user-attachments/assets/1adeeefb-64e7-4a8d-822f-be25936c119d)
![image](https://github.com/user-attachments/assets/5b8b405b-3894-4435-81b5-d5809041f98f)

Task 7: Create the Schema in PostgreSQL
Generate SQL from ERD:

Click Generate SQL in the ERD tool.
Copy the SQL.
Create the Database "staging":

In pgAdmin, right-click Databases → Create → Database....
Name it staging → Click Save.
Execute the SQL in "staging":

Select the staging database.
Open Query Tool.
Paste the SQL script.
Click Execute (F5).
Verify Schema Creation: Run:

sql
Copy
Edit
SELECT table_name FROM information_schema.tables WHERE table_schema = 'public';
If all tables appear, the schema is successfully created.

Take a Screenshot and save it as createschema.jpg.
![image](https://github.com/user-attachments/assets/57b9634c-c069-48d2-8bb3-ec9c63b3f616)

of staging - 
BEGIN;


CREATE TABLE IF NOT EXISTS public.softcartdimcategory
(
    categoryid serial NOT NULL,
    categoryname character varying(50) COLLATE pg_catalog."default" NOT NULL,
    CONSTRAINT softcartdimcategory_pkey PRIMARY KEY (categoryid)
);

CREATE TABLE IF NOT EXISTS public.softcartdimcountry
(
    countryid serial NOT NULL,
    countryname character varying(50) COLLATE pg_catalog."default" NOT NULL,
    CONSTRAINT softcartdimcountry_pkey PRIMARY KEY (countryid)
);

CREATE TABLE IF NOT EXISTS public.softcartdimdate
(
    dateid serial NOT NULL,
    date date NOT NULL,
    year integer NOT NULL,
    quarter character varying(10) COLLATE pg_catalog."default" NOT NULL,
    month integer NOT NULL,
    monthname character varying(20) COLLATE pg_catalog."default" NOT NULL,
    week integer NOT NULL,
    weekday character varying(15) COLLATE pg_catalog."default" NOT NULL,
    weekend_flag boolean NOT NULL,
    CONSTRAINT softcartdimdate_pkey PRIMARY KEY (dateid)
);

CREATE TABLE IF NOT EXISTS public.softcartdimitem
(
    itemid serial NOT NULL,
    itemname character varying(100) COLLATE pg_catalog."default" NOT NULL,
    categoryid integer NOT NULL,
    CONSTRAINT softcartdimitem_pkey PRIMARY KEY (itemid)
);

CREATE TABLE IF NOT EXISTS public.softcartfactsales
(
    salesid serial NOT NULL,
    dateid integer NOT NULL,
    itemid integer NOT NULL,
    countryid integer NOT NULL,
    price numeric(10, 2) NOT NULL,
    CONSTRAINT softcartfactsales_pkey PRIMARY KEY (salesid)
);

ALTER TABLE IF EXISTS public.softcartdimitem
    ADD CONSTRAINT softcartdimitem_categoryid_fkey FOREIGN KEY (categoryid)
    REFERENCES public.softcartdimcategory (categoryid) MATCH SIMPLE
    ON UPDATE NO ACTION
    ON DELETE CASCADE;


ALTER TABLE IF EXISTS public.softcartfactsales
    ADD CONSTRAINT softcartfactsales_countryid_fkey FOREIGN KEY (countryid)
    REFERENCES public.softcartdimcountry (countryid) MATCH SIMPLE
    ON UPDATE NO ACTION
    ON DELETE CASCADE;


ALTER TABLE IF EXISTS public.softcartfactsales
    ADD CONSTRAINT softcartfactsales_dateid_fkey FOREIGN KEY (dateid)
    REFERENCES public.softcartdimdate (dateid) MATCH SIMPLE
    ON UPDATE NO ACTION
    ON DELETE CASCADE;


ALTER TABLE IF EXISTS public.softcartfactsales
    ADD CONSTRAINT softcartfactsales_itemid_fkey FOREIGN KEY (itemid)
    REFERENCES public.softcartdimitem (itemid) MATCH SIMPLE
    ON UPDATE NO ACTION
    ON DELETE CASCADE;

END;
