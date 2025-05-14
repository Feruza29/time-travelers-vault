 ### Time Traveler's Vault - Phase 2

A persistent command-line borrowing system **SQLite**, built in Python. This project simulates a time traveler's vault where users borrow historical
and futuristic artifacts.

### 💥 New in Phase 2:
- ✅ **SQLite database integration**
- ✅ Data persistence: items, users, borrowing records
- ✅ Turn tracking to simulate time and enforce overdue logic
- ✅ Improved logic to prevent double-borrowing


## 📊 Database Schema

### 'users'

| Column      | Type       | Details         |
--------------|------------|-----------------|
| user_id     | INTEGER    | Primary Key     |
| name        | TEXT       | Not null        |

### 'items'

| Column      | Type       | Details         |
--------------|------------|-----------------|
| item_id     | INTEGER    | Primary Key     |
| name        | TEXT       | Not null        |
| origin_era  | TEXT       | Not null        |
| max_duration| INTEGER    | Duration limit  |
| is_borrowed | INTEGER    | Default 0(false)|

### 'borrowed_items'

| Column            |    Type        |     Details                            |
|-------------------|----------------|----------------------------------------|
| user_id           | INTEGER        | Foreign key -> 'users (user_id)'       |
| items_id          | INTEGER        | Foreign key -> 'items (item_id)'       |
| turns_borrowed    | INTEGER        | Tracks how long item has been borrowed |


##  🛠️ How it Works

1. Add user(s) and item(s)
2. Borrow items
3. Return them before they're overdue!
4. Advance time with 'next_turn()' - if 'turns_borrowed > max_duration', triggers a **TIME DISPUPTION**

