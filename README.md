# Oracle PDB Assignment

**Full Name:** Mugenga Divin  
**Student ID:** 27163  
**Course:** PL/SQL   
**Assignment:** Oracle PDB Tasks 1–3  
**Date:** 5/10/2025

---

## Overview of Tasks

### Task 1 – Create a New Pluggable Database (PDB)
- **PDB Name:** `DI_PDB_27163`  
- **Admin User:** `divin_plsqlauca_27163`  
- **Purpose:** Store class work and demonstrate creation of a PDB.  
- **Tools Used:** SQL Developer / SQL*Plus  

**Description:**  
I created a new pluggable database using SQL Developer. After setting the proper file paths and assigning an admin user, the PDB was successfully created. I verified the PDB status using `SELECT pdb_name, status FROM dba_pdbs;` and confirmed the user existed.  

**Screenshot:**  
[View Task 1 Creation Screenshot](./screenshots/task1.png)

---

### Task 2 – Create and Delete a PDB
- **PDB Name Created:** `DI_TO_DELETE_PDB_27163`  
- **Admin User:** `divin_delete_pdb_27163` (Password: 123)  
- **Steps:**
  1. Created the PDB successfully using SQL Developer and specified the proper `FILE_NAME_CONVERT` paths.  
  2. Opened the PDB to ensure it was active.  
  3. Closed the PDB immediately before deletion.  
  4. Dropped the PDB including all datafiles to fully remove it.  
- **Purpose:** Demonstrate creation and safe deletion of a PDB.  

**Screenshot (Creation):**  
[View Task 2 Creation Screenshot (1)](./screenshots/task2_creation.png)  

[View Task 2 Creation Screenshot (2)](./screenshots/task2_creation_1.png)  

**Screenshot (Deletion):**  
[View Task 2 Deletion Screenshot](./screenshots/task2_deletion.png)  

---

### Task 3 – Oracle Enterprise Manager (OEM)
- **PDB Accessed:** `DI_PDB_27163`  
- **Username:** `divin_plsqlauca_27163`  
- **Purpose:** Show graphical proof of PDB and user created in Tasks 1 & 2.  
- **Notes:** Logged into OEM selecting the PDB container instead of the root container (CDB$ROOT) to display the correct username and PDB.  

**Screenshot (OEM Dashboard):**  
[View Task 3 OEM Screenshot](./screenshots/task3.png)

---

## Issues Encountered & Solutions

1. **ORA-65005: Missing or invalid file name pattern**
   - **Problem:** While creating the PDB, Oracle reported an error because the target folder paths for the PDB datafiles did not exist. Initially, I had tried copying the default PDB seed paths directly without creating new directories.  
   - **Solution:** I manually created a new folder for the PDB (`DI_PDB_27163`) and updated the `FILE_NAME_CONVERT` paths in the PDB creation command. This ensured Oracle could locate the source files and correctly create the PDB in the target location.

2. **Logged in as SYS instead of PDB user in SQL Developer**
   - **Problem:** After creating the PDB and user, I opened the worksheet under the root container (CDB$ROOT), which showed me as `SYS` instead of my PDB admin user.  
   - **Solution:** I created a new connection in SQL Developer specifically for `divin_plsqlauca_27163` under the `DI_PDB_27163` container. Opening the worksheet under this connection allowed me to log in as my PDB admin user and verify the PDB creation.

3. **OEM Login Container Selection**
   - **Problem:** When first logging into Oracle Enterprise Manager, I initially tried logging into the root container (CDB$ROOT), which displayed SYS as the current user. This would not satisfy the requirement to show my PDB username in the dashboard.  
   - **Solution:** I carefully selected the `DI_PDB_27163` container during login. This displayed the dashboard with my PDB and username (`divin_plsqlauca_27163`), which was exactly what the assignment required for the screenshot.

4. **File path / folder creation for Task 2 PDB**
   - **Problem:** When creating the `DI_TO_DELETE_PDB_27163` PDB, I initially received a similar ORA-65005 error because the target folder did not exist.  
   - **Solution:** I created a dedicated folder for this PDB, ensured the file paths in `FILE_NAME_CONVERT` matched, then the creation succeeded. I then closed and dropped the PDB safely, demonstrating the creation and deletion process.

---

## Files Included in Repository
- `task1_create_pdb.sql` – SQL script for Task 1  
- `task2_create_delete_pdb.sql` – SQL script for Task 2  
- `screenshots/task1_creation.png` – Screenshot for Task 1 PDB creation  
- `screenshots/task2_creation_1.png` – Screenshot for Task 2 PDB creation  
- `screenshots/task2_deletion.png` – Screenshot for Task 2 PDB deletion  
- `screenshots/task3.png` – Screenshot for Task 3 OEM dashboard  
- `README.md` – Assignment overview and documentation