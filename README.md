# AV Equipment Rental

Microsoft Power Platform prototype for an audiovisual and photographic equipment rental company. I designed and built it on my own in 2 months, from requirements to the prototype presented to the client.

This repository contains the unpacked export of the Dataverse solution `AvEquipmentRental` (version 1.0.0.1).

## What it does

- **Back office (model-driven app "AV Equipment Rental Admin")**: staff manage the equipment catalogue, review rental requests, update rental status, record returns and track invoices.
- **Customer website (Power Pages)**: customers send rental requests through a form that saves them straight into Dataverse.

## Solution contents

### Dataverse tables

| Table | Main columns |
| --- | --- |
| Equipment | SKU, name, brand, category, description, daily rate, deposit, replacement value, minimum rental days, total and available units, requires training, active, product image |
| Rental | rental number, customer (account or contact), equipment, quantity, start date, due date, returned on, status, total amount |
| Rental Invoice | invoice number, rental, issue date, due date, status, total amount |

Status lifecycles:
- Rental: Draft, Reserved, Checked Out, Returned, Overdue, Cancelled
- Rental Invoice: Draft, Issued, Paid, Overdue, Void

### Model-driven app with custom pages (Power Fx)

| Page | Purpose |
| --- | --- |
| Dashboard | Equipment inventory with images, daily rate and stock, filtered by category (Cameras, Lenses, Audio, Lighting) and by unavailable items |
| Equipment Management | Add and edit equipment, inventory, availability and rates |
| Rental Management | Review customer requests, update rental status and record returns |
| Alerts | Rented, returned and overdue equipment |
| Invoices | Issued invoices, due dates and payment status |
| Auctions | Placeholder for a future module for retired and replacement equipment |

### Power Pages site

- Basic form "Request a rental form" on the Rental table (form "Portal - New Rental").
- Table permission "Rental - Create": customers can only create rental requests.
- Site search and the default site chatbot.

## Folder structure

| Path | Content |
| --- | --- |
| `solution.xml` | Solution manifest: publisher, version and root components |
| `customizations.xml` | Tables, columns, relationships, choices, forms, views, app and site map |
| `CanvasApps/` | Custom pages of the model-driven app (`.msapp`) |
| `powerpagecomponents/`, `Assets/` | Power Pages site: pages, templates, forms, permissions and images |
| `bots/`, `botcomponents/` | Default chatbot of the Power Pages site |
| `dvfilesearch*/`, `dvtablesearch*/` | Search configuration |

## How to import

1. Zip the contents of this folder (the files, not the folder itself).
2. In [Power Apps](https://make.powerapps.com), open **Solutions > Import solution** and select the zip.
3. After the import, publish all customizations and set up the Power Pages site in the target environment.

## Tech stack

Microsoft Power Platform, Dataverse, Power Apps (model-driven app and custom pages), Power Fx, Power Pages, Liquid.
