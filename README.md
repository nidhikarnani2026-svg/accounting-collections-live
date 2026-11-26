# Accounting and Collections dashboard (live)

A dashboard with Daily, Weekly and Monthly views that reads live from the Tally database each time it is opened.

## How it works

- `index.html` is the whole page. It holds no figures.
- When you open it, it asks you to sign in. After sign-in it runs seven read-only queries against the Tally database and draws the numbers.
- It rechecks every 10 minutes while the page is open, and whenever you come back to the tab, so a new Tally sync shows up on its own.

## Who can see the numbers

Only a login that the Tally database already treats as an active super-admin. Anyone else sees the sign-in box and nothing more. Every query is recorded in the database's own access log.

The key in the page is the database's public key, which is meant to be visible in browsers. It unlocks nothing without a login.

## Assumed rules

These stand in for decisions that are still open:

- Blank credit terms count as 30 days.
- Each customer's oldest invoices are treated as paid first.
- A proforma invoice counts as a new order.
- Grades come from days late: A none, B up to 30, C 31 to 90, D over 90.
- Wages include bonus. Marketing leaves out commission on sales.
- Material cost is materials issued to production, which needs a month-end stock value to confirm.

Reminders sent and Escalated are blank because the mail log is not connected.
