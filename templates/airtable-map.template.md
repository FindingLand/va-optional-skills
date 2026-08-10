# Your Airtable map

**This is a blank template.** Vera copies it into **your own repo** as `reference/airtable-map.md`,
fills it in from your live base, and keeps it current. You can correct it by hand any time.

**If you are reading this file inside the shared skills library, it is the blank master and it is not
yours.** Yours lives in your own repo. An assistant must never resolve anything against this copy.

Every skill asks for tables and fields **by role**, never by name. "The table that holds leases", not
"the table called Leases". This file turns a role into whatever you actually called it, which is what
lets you rename things later without breaking anything.

If a skill says it cannot find something, this is the file to fix.

---

## Base

| | |
|---|---|
| Base id | |
| Base name | |
| Last checked | |

## How to read this file

- **Core** roles are needed by the everyday work. Fill these in first.
- **Optional** roles only matter if you run that kind of rental or track that kind of thing. Leave
  them blank and the skills that need them will say so instead of guessing.
- A blank row means "I do not have this". That is a valid answer and it is never an error.

---

## Tables

| Role | Core? | Your table name | Table id |
|---|---|---|---|
| `properties` | core | | |
| `units` | core | | |
| `tenants` | core | | |
| `leases` | core | | |
| `rent_payments` | core | | |
| `vendors` | core | | |
| `maintenance` | core | | |
| `tasks` | core | | |
| `routines` | core | | |
| `policy_settings_states` | core | | |
| `applicant_groups` | optional | | |
| `prospects` | optional | | |
| `leads` | optional | | |
| `communications` | optional | | |
| `mail` | optional | | |
| `documents` | optional | | |
| `folders` | optional | | |
| `insurance_policies` | optional | | |
| `deposit_interest_rates` | optional | | |
| `access_codes` | optional | | |
| `rooms` | optional | | |

`rooms` only applies if you rent individual rooms within a unit. `access_codes` only if you have
keypad locks with more than one code per unit.

---

## Fields

### properties (core)
| Role | Core? | Your field name |
|---|---|---|
| `address` | core | |
| `town` | core | |
| `state_or_region` | core | |
| `country` | core | |
| `archived` | core | |
| `climate_note` | optional | |

### units (core)
| Role | Core? | Your field name |
|---|---|---|
| `property_link` | core | |
| `name_or_number` | core | |
| `occupancy_status` | core | |
| `lease_type` | optional | |
| `default_rent` | optional | |
| `default_deposit` | optional | |
| `archived` | core | |

**Authority rule for `lease_type`:** the value on `leases` wins whenever a lease exists. The one on
`units` is only the default for a vacant unit.

### unit equipment (optional, drives seasonal and maintenance work)
| Role | Your field name |
|---|---|
| `heating_type` | |
| `cooling_type` | |
| `water_heating` | |
| `filter_size` | |
| `has_sump_pump` | |
| `water_source` | |
| `waste_system` | |
| `has_irrigation` | |
| `appliances` | |

Leave any of these blank. A skill that needs one and cannot find it will ask you for that single
line rather than guessing.

### tenants (core)
| Role | Core? | Your field name |
|---|---|---|
| `first_name` | core | |
| `last_name` | core | |
| `email` | core | |
| `phone` | optional | |
| `lease_link` | core | |
| `archived` | core | |

### leases (core)
| Role | Core? | Your field name |
|---|---|---|
| `unit_link` | core | |
| `tenant_link` | core | |
| `lease_type` | optional | |
| `rent_amount` | core | |
| `start_date` | core | |
| `end_date` | core | |
| `status` | core | |
| `deposit_held` | core | |
| `pet_deposit` | optional | |
| `subsidised` | optional | |
| `agency_portion` | optional | |
| `tenant_portion` | optional | |
| `move_out_date` | optional | |
| `forwarding_address` | optional | |

`subsidised`, `agency_portion` and `tenant_portion` only matter if you accept housing vouchers. Without
them the finance skill will not attempt to split a payment between an agency and a tenant.

### rent_payments (core)
| Role | Core? | Your field name |
|---|---|---|
| `lease_link` | core | |
| `period` | core | |
| `amount` | core | |
| `date_paid` | core | |
| `status` | core | |
| `paid_by` | optional | |

`paid_by` distinguishes a tenant payment from an agency payment. Without it, a subsidised lease
cannot be assessed correctly and the finance skill will say so rather than call a tenant late.

### vendors (core)
| Role | Core? | Your field name |
|---|---|---|
| `name` | core | |
| `category` | core | |
| `email` | optional | |
| `phone` | optional | |
| `insurance_expiry` | optional | |
| `licence_number` | optional | |
| `licence_expiry` | optional | |
| `tax_form_on_file` | optional | |
| `preferred` | optional | |

`tax_form_on_file` is whatever your country requires from a contractor before you pay them. Name the
requirement in `Notes` below so the skills can refer to it correctly.

### maintenance (core)
| Role | Core? | Your field name |
|---|---|---|
| `property_link` | core | |
| `unit_link` | core | |
| `description` | core | |
| `priority` | core | |
| `status` | core | |
| `vendor_link` | optional | |
| `reported_date` | core | |
| `cost` | optional | |

### tasks (core)
| Role | Core? | Your field name |
|---|---|---|
| `title` | core | |
| `status` | core | |
| `due_date` | optional | |
| `assigned_to` | optional | |
| `notes` | optional | |

### routines (core)
| Role | Core? | Your field name |
|---|---|---|
| `name` | core | |
| `instructions` | core | |
| `frequency` | core | |
| `due_day` | optional | |
| `skills_needed` | optional | |
| `autonomy` | core | |
| `external_sending_approved` | core | |
| `status` | core | |
| `priority` | core | |
| `last_completed` | core | |
| `last_result` | core | |
| `last_notes` | core | |

**`autonomy`** is either "do it" or "prepare it and wait for me".
**`external_sending_approved`** is a yes or no, per routine, and it defaults to no. It is the only
thing that ever permits a routine to send something to a tenant, a vendor or anyone else outside your
business while you are not watching. Leave it blank and nothing leaves the building.

### policy_settings_states (core)
One row per state, province or region you own property in.

| Role | Core? | Your field name |
|---|---|---|
| `state_or_region` | core | |
| `rent_due_day` | core | |
| `grace_period_days` | optional | |
| `grace_is_legal_or_lease` | optional | |
| `late_fee_type` | optional | |
| `late_fee_amount` | optional | |
| `late_fee_cap` | optional | |
| `notice_to_quit_days` | optional | |
| `entry_notice_hours` | optional | |
| `deposit_cap_rule` | optional | |
| `deposit_return_deadline_days` | optional | |
| `deposit_deadline_starts_from` | optional | |
| `deposit_interest_required` | optional | |
| `extra_protected_classes` | optional | |
| `attorney_threshold` | optional | |

**Every one of these is a value you or your attorney put in. No skill will ever fill one in from its
own knowledge, and no skill will state one of these as a legal fact if the row is empty. It will tell
you the row is empty and stop.**

### applicant_groups (optional)
| Role | Your field name |
|---|---|
| `group_name` | |
| `unit_link` | |
| `applicants_link` | |
| `stage` | |
| `decision` | |
| `documents_status` | |
| `move_in_date` | |
| `folder_link` | |

### prospects (optional)
| Role | Your field name |
|---|---|
| `name` | |
| `unit_of_interest` | |
| `stage` | |
| `last_contact_date` | |

### leads (optional)
| Role | Your field name |
|---|---|
| `name` | |
| `source` | |
| `unit_of_interest` | |
| `received_date` | |
| `status` | |
| `conversation` | |

### communications (optional)
| Role | Your field name |
|---|---|
| `party_link` | |
| `date` | |
| `channel` | |
| `summary` | |

### mail (optional)
| Role | Your field name |
|---|---|
| `received_date` | |
| `sender` | |
| `classification` | |
| `property_link` | |
| `action_needed` | |
| `attachment` | |

### documents (optional)
| Role | Your field name |
|---|---|
| `name` | |
| `type` | |
| `related_record` | |
| `file` | |
| `filed_date` | |

### folders (optional)
| Role | Your field name |
|---|---|
| `name` | |
| `path_or_url` | |
| `property_link` | |

### insurance_policies (optional)
| Role | Your field name |
|---|---|
| `property_link` | |
| `carrier` | |
| `policy_number` | |
| `renewal_date` | |
| `premium` | |

### deposit_interest_rates (optional)
| Role | Your field name |
|---|---|
| `state_or_region` | |
| `year` | |
| `rate` | |
| `method` | |

### access_codes (optional)
| Role | Your field name |
|---|---|
| `unit_link` | |
| `lock_name` | |
| `code` | |
| `holder` | |
| `expires` | |

### rooms (optional)
| Role | Your field name |
|---|---|
| `unit_link` | |
| `name` | |
| `occupancy_status` | |
| `tenant_link` | |

---

## Notes

Anything a skill should know that does not fit a row above. For example what your country calls the
tax form a contractor must file, or which of two similar tables is the real one.

---

## Rules, for your assistant

1. **Resolve by role, every time.** Never hardcode a table or field id into a skill, and never assume
   a name. Read this file.
2. **A blank optional row is an answer, not an error.** Say the feature is not set up and carry on
   with everything else. Never stop the whole job over an optional role.
3. **A blank CORE row stops that piece of work.** Say exactly which role is missing, in plain words,
   and offer to fill it in. Never silently pick the closest-looking table or field. Guessing wrong in
   a base full of real tenant data is far worse than stopping.
4. **When you need something this file has no role for at all**, ask the owner for that one line and
   offer to add it here. Do not pattern-match on field names.
5. **Refresh this file** on first run, whenever the owner asks, and whenever a lookup fails.
6. **A rename is a one-line fix here**, not a change to any skill.
7. **This file lives in the owner's own repo.** The copy in the shared library is a blank master and
   must never be used to resolve anything.

## A recommendation for your first few weeks

Keep your table names as they arrive in the starter base while you are learning the system. Rename
things once you know what each piece does. Renaming early is the quickest way to end up with an
assistant that cannot find your data, and it is a frustrating thing to debug in week one. After that,
rename whatever you like and update this file.
