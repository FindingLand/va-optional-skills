# Your Airtable map

**This is a template. Vera copies it into your own repo, fills it in from your live base, and keeps
it current. You can edit it by hand any time she gets something wrong.**

Every skill you receive asks for tables and fields **by role**, never by name. "The table that holds
leases", not "the table called Leases". This file is what turns a role into whatever you actually
called it, which is what lets you rename things later without breaking your assistant.

If a skill ever says it cannot find something, this is the file to look at first.

---

## Base

| | |
|---|---|
| Base id | `TO BE FILLED BY VERA` |
| Base name | |
| Last checked | |

## Tables

Fill in the middle column with your table's real name. Leave a row blank if you do not have that
table yet, and the skills that need it will say so plainly instead of guessing.

| Role | Your table name | Table id |
|---|---|---|
| `properties` | | |
| `units` | | |
| `tenants` | | |
| `leases` | | |
| `lease_details_mtr` | | |
| `rent_payments` | | |
| `applicant_groups` | | |
| `prospects` | | |
| `leads` | | |
| `vendors` | | |
| `maintenance` | | |
| `tasks` | | |
| `communications` | | |
| `mail` | | |
| `documents` | | |
| `folders` | | |
| `insurance_policies` | | |
| `policy_settings_states` | | |
| `deposit_interest_rates` | | |
| `routines` | | |
| `automations` | | |

## Fields

Only the fields a skill actually needs. Same idea: role on the left, your real field name in the
middle.

### properties
| Role | Your field name |
|---|---|
| `address` | |
| `town` | |
| `state` | |
| `archived` | |

### units
| Role | Your field name |
|---|---|
| `property_link` | |
| `occupancy_status` | |
| `lease_type` | |
| `access_code` | |

### tenants
| Role | Your field name |
|---|---|
| `first_name` | |
| `last_name` | |
| `email` | |
| `phone` | |
| `lease_link` | |
| `archived` | |

### leases
| Role | Your field name |
|---|---|
| `unit_link` | |
| `tenant_link` | |
| `lease_type` | |
| `rent_amount` | |
| `start_date` | |
| `end_date` | |
| `deposit_held` | |
| `status` | |

### rent_payments
| Role | Your field name |
|---|---|
| `lease_link` | |
| `period` | |
| `amount` | |
| `date_paid` | |
| `status` | |

### vendors
| Role | Your field name |
|---|---|
| `name` | |
| `category` | |
| `insurance_expiry` | |
| `w9_on_file` | |

### maintenance
| Role | Your field name |
|---|---|
| `property_link` | |
| `unit_link` | |
| `priority` | |
| `status` | |

### insurance_policies
| Role | Your field name |
|---|---|
| `property_link` | |
| `renewal_date` | |

### policy_settings_states
| Role | Your field name |
|---|---|
| `state` | |
| `rent_due_day` | |
| `grace_period_days` | |
| `late_fee_type` | |
| `late_fee_amount` | |
| `deposit_return_deadline_days` | |
| `notice_to_quit_days` | |

---

## Rules, for your assistant

1. **Resolve by role, every time.** Never hardcode a table or field id into a skill, and never
   assume a name. Read this file.
2. **Refresh it** on first run, whenever the owner asks, and whenever a lookup fails. A failed lookup
   usually means the base changed, not that the data is gone.
3. **When a role is blank or missing, say so in plain words** and name the role that could not be
   resolved, so the owner can fill in one line here. Never silently pick the closest-looking table.
   Guessing wrong in a base full of real tenant data is worse than stopping.
4. **A rename is a one-line fix here**, not a change to any skill. That is the whole point of this
   file.
5. **Keep this file in the owner's own repo**, never in the shared library. It describes their base.

## A recommendation for the first four weeks

While you are going through the program, **keep your table names as they come in the starter base**.
Rename things later, once you know what each piece does. Renaming early is the fastest way to end up
with an assistant that cannot find your data, and it is a frustrating thing to debug in week one.

After the program, rename whatever you like. Update this file, and everything keeps working.
