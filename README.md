# Café stock tracker

A single-page stock tracker for the Jurong, Orchard and Tampines outlets. It reads and saves stock in the Supabase table `public.stock_counts`.

## Features

- A tab for each outlet, with items grouped by category
- Steppers to change stock on hand and reorder levels, saved per item
- Items at or below their reorder level are marked **Low**
- A combined "Order from suppliers" list that totals the shortfall across outlets and can be copied

## Sign-in

Users sign in with their tracker username and password. Any signed-in user can view stock; only admins can save changes. Access is enforced by row-level security in Supabase, not by the page.

The Supabase publishable key in `index.html` is meant to be public. Never put a secret or service-role key in this file.

## Deploy on Vercel

1. Import this repository at [vercel.com/new](https://vercel.com/new).
2. Framework preset: **Other**. Leave the build command and output directory empty.
3. Deploy. Every push to `main` deploys again.

## How saving works

Each save writes that item's count for today's date (one row per outlet, item and day). Earlier counts are kept as history, and the page always shows the latest one.
