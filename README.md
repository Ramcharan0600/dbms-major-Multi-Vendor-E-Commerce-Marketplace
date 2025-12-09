# Multi-Vendor E-Commerce Marketplace  
**DBMS Major Project – Topic 3**  
Submitted by:A Ramcharan 
DBMS: MySQL 8.0 (MySQL Workbench)

## Project Overview (Real-World Logic)
A complete database for a multi-vendor platform like **Flipkart / Amazon / Meesho** where:
- Multiple vendors register → get admin approval → list products
- Customers can buy items from 5 different vendors in **one single order**
- Platform takes 10% commission → rest goes to vendors
- Stock never goes negative (transaction protected)
- Reviews only for purchased items

**Core Logic**:  
One customer order → stored in `orders` table  
Each item → separate row in `order_items` table with its own `vendor_id`  
→ This single design handles everything: split earnings, stock, reviews, reports.

## Database Schema – 8 Tables
| Table          | Purpose |
|------|--------|
| `categories` & `subcategories` | Product categorization |
| `vendors` | Seller registration + approval workflow |
| `customers` | Buyer details |
| `products` | Items listed by vendors |
| `orders` | One order per checkout (total_amount) |
| `order_items` | Heart of the system – links order ↔ product ↔ vendor |
| `reviews` | Rating & feedback system |

## Key Features Implemented
- Vendor approval system (status: pending/approved)
- One order → multiple vendors → automatic earning split
- Stock management with **ACID transaction** (no overselling)
- 12+ complex analytical queries (top vendors, low stock, monthly revenue, etc.)
- Proper indexing for speed
- Full normalization up to **3NF**
- 180+ realistic data rows
- Role-based security ready
- Complete backup/restore script

## Folder Structure (All Deliverables)
├── README.md                              ← You are reading this
├── 02_er_diagram.png                      ← Full ER Diagram
├── 02_er_notes.md                         ← Entity & relationship explanation
├── 03_schema_draft.md                     ← Table-wise columns & data types
├── 03_create_tables.sql                      ← Complete DDL (tables + constraints + indexes)
├── 04_normalization.md                    ← 1NF → 3NF proof with FDs
├── 05_seed_data.sql                       ← 180+ INSERT statements
├── 05_data_dictionary.md                  ← Meaning of every column
├── 06_crud_and_queries.sql                ← CRUD + 15 complex queries
├── 06_query_results/                      ← Screenshots of all query outputs
├── 07_indexes.sql & 07_explain_report.md  ← Performance optimization
├── 08_transactions.sql & 08_concurrency_demo.md ← ACID + race condition fix
├── 09_constraints.sql + 09_roles_privileges.sql + 09_security_tests.md
├── 10_backup_restore.md                   ← mysqldump & restore steps
├── 10_reports.sql & 10_reports/           ← CSV reports
└── 10_final_pack/
└── multivendor_ecommerce_full_dump.sql ← One-click full DB restore

## How to Run the Project (Teacher can test in 2 minutes)
1. Open MySQL Workbench
2. Run `03_create_tables.sql` → creates schema
3. Run `05_seed_data.sql` → loads all data
4. Run any query from `06_crud_and_queries.sql`
5. See results + screenshots in `06_query_results/`

## Sample Real Data
**Top Vendors**: TechGalaxy (Rahul Kumar), FashionTrendz (Priya Singh)  
**Highest Order**: ₹1,85,000 (MacBook Pro)  
**Pending Vendors**: BookWorld, ToyLand

## Future Enhancements (Already Designed)
- Separate `payments` table with status
- Shopping cart table
- Vendor dashboard web page (PHP + Bootstrap)
- Email notifications on order

**Project completed on time with full testing**  
Thank you for this amazing learning experience
