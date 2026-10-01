# Dropper Academy — Supabase Connected Version

This version uses Supabase Auth + Postgres + Row Level Security. The browser only contains the publishable key. No secret/service-role key is included.

## 1) Run the database schema
In Supabase Dashboard → SQL Editor → New query, paste **supabase_schema.sql** and Run.

## 2) Create your admin account
Open the app, create a normal student account using your own email, then in Supabase SQL Editor run:

`update public.profiles set role='admin' where id = (select id from auth.users where email='YOUR_EMAIL');`

Replace YOUR_EMAIL with the email you used. Do not send your password or secret key anywhere.

## 3) Open the app
For local testing, serve the folder with any static web server. It can also be deployed to Vercel or another static host. Do not open it using file:// if your browser blocks module/network requests.

## 4) Supabase email confirmation
If email confirmation is enabled, the student must confirm the email before password login works. You can configure this in Supabase Authentication settings.

## Important
The publishable key is designed for browser use when RLS policies are configured. Never put `sb_secret_...` or a service-role key into config.js or frontend code.
