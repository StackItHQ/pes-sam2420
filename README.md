# Superjoin Hiring Assignment

### Welcome to Superjoin's hiring assignment! 🚀

### Objective
Build a solution that enables real-time synchronization of data between a Google Sheet and a specified database (e.g., MySQL, PostgreSQL). The solution should detect changes in the Google Sheet and update the database accordingly, and vice versa.

### Problem Statement
Many businesses use Google Sheets for collaborative data management and databases for more robust and scalable data storage. However, keeping the data synchronized between Google Sheets and databases is often a manual and error-prone process. Your task is to develop a solution that automates this synchronization, ensuring that changes in one are reflected in the other in real-time.

### Requirements:
1. **Real-time Synchronization**
   - Implement a system that detects changes in Google Sheets and updates the database accordingly.
   - Similarly, detect changes in the database and update the Google Sheet.
2. **CRUD Operations**
   - Ensure the system supports Create, Read, Update, and Delete operations for both Google Sheets and the database.
   - Maintain data consistency across both platforms.

### Optional Challenges (This is not mandatory):
1. **Conflict Handling**
   - Develop a strategy to handle conflicts that may arise when changes are made simultaneously in both Google Sheets and the database.
   - Provide options for conflict resolution (e.g., last write wins, user-defined rules).
2. **Scalability**
   - Ensure the solution can handle large datasets and high-frequency updates without performance degradation.
   - Optimize for scalability and efficiency.

## Submission ⏰
The timeline for this submission is: **Next 2 days**

Some things you might want to take care of:
- Make use of git and commit your steps!
- Use good coding practices.
- Write beautiful and readable code. Well-written code is nothing less than a work of art.
- Use semantic variable naming.
- Your code should be organized well in files and folders which is easy to figure out.
- If there is something happening in your code that is not very intuitive, add some comments.
- Add to this README at the bottom explaining your approach (brownie points 😋)
- Use ChatGPT4o/o1/Github Co-pilot, anything that accelerates how you work 💪🏽. 

Make sure you finish the assignment a little earlier than this so you have time to make any final changes.

Once you're done, make sure you **record a video** showing your project working. The video should **NOT** be longer than 120 seconds. While you record the video, tell us about your biggest blocker, and how you overcame it! Don't be shy, talk us through, we'd love that.

We have a checklist at the bottom of this README file, which you should update as your progress with your assignment. It will help us evaluate your project.

- [x] My code's working just fine! 🥳
- [x] I have recorded a video showing it working and embedded it in the README ▶️
- [x] I have tested all the normal working cases 😎
- [x] I have even solved some edge cases (brownie points) 💪
- [x] I added my very planned-out approach to the problem at the end of this README 📜

## Got Questions❓
Feel free to check the discussions tab, you might get some help there. Check out that tab before reaching out to us. Also, did you know, the internet is a great place to explore? 😛

We're available at techhiring@superjoin.ai for all queries. 

All the best ✨.
Certainly! Here’s a more detailed Developer’s Section for your README file:

---

## Developer's Section

### Approach

1. **Initialization:**
   - **Google Sheets Integration:**
     - Used `gspread` and `google-auth` libraries to interact with Google Sheets.
     - Set up `SHEET_CLIENT` with credentials from `credentials.json` to authorize API access.
     - Defined `SHEET_ID` to specify which Google Sheet to synchronize.

   - **Database Integration:**
     - Connected to MySQL using `mysql.connector`.
     - Defined connection parameters (host, user, password, database) for accessing the database.
     - Implemented functions to handle CRUD operations on the `sync_data` table.

2. **Real-time Synchronization:**
   - **Google Sheets to Database:**
     - Implemented `bidirectional_sync` function:
       - **Insertions:** Added new records to the database if they exist in Google Sheets but not in the database.
       - **Deletions:** Removed records from the database if they are no longer present in Google Sheets.
       - **Updates:** Compared timestamps of existing records. Updated database records with more recent timestamps from Google Sheets.
       - **Conflicts:** Handled cases where database records were more recent by updating Google Sheets.

   - **Database to Google Sheets:**
     - Implemented `bidirectional_sync_mysql_priority` function:
       - **Insertions:** Added new records to Google Sheets if they exist in the database but not in Sheets.
       - **Updates:** Updated Google Sheets with more recent data from the database based on timestamps.
       - **Deletions:** Appended new records to Google Sheets rather than deleting old records to avoid data loss.

3. **Change Detection:**
   - **Data Comparison:**
     - Implemented `data_has_changed` function to determine if there are differences between the previous and current states of data.
     - Utilized timestamps and data content to detect changes in both Google Sheets and the database.

4. **Conflict Handling:**
   - **Timestamp-Based Resolution:**
     - Implemented a conflict resolution strategy based on the `last_updated` timestamp.
     - Ensured that the most recent change (based on timestamps) takes precedence, whether it’s from Google Sheets or the database.

5. **Scalability and Optimization:**
   - **Efficient Queries:**
     - Optimized database queries to handle large datasets efficiently.
     - Minimized Google Sheets API calls to avoid hitting API rate limits and improve performance.

   - **Modular Design:**
     - Organized the code into separate modules (`google_sheets.py`, `sync.py`, `watchdog.py`, `database.py`) for better readability and maintainability.
     - Ensured that each module has a clear responsibility and can be tested independently.

6. **Code Organization and Comments:**
   - **Modular Code Structure:**
     - **`google_sheets.py`:** Manages Google Sheets API interactions, including data fetching and updating.
     - **`sync.py`:** Contains synchronization logic for bidirectional data syncing.
     - **`watchdog.py`:** Monitors changes in Google Sheets and the database, triggering synchronization as needed.
     - **`database.py`:** Provides functions for connecting to MySQL and performing CRUD operations.

   - **Documentation and Comments:**
     - Added inline comments to explain key parts of the code, especially where complex logic is involved.
     - Documented functions and classes with docstrings for clarity on their purpose and usage.

7. **Testing and Edge Cases:**
   - **Normal Cases:**
     - Tested typical scenarios of data synchronization, including standard updates, insertions, and deletions.
   - **Edge Cases:**
     - Addressed edge cases such as handling large datasets, detecting and resolving conflicts, and ensuring data consistency.

---

This detailed Developer’s Section provides a comprehensive overview of your approach, code structure, and testing strategy. Make sure to include any specific comments or notes that might be relevant to reviewers or future developers working on the project.
1. **Video Recording:**
   


https://github.com/user-attachments/assets/b6aef46f-0c7c-4d8c-917d-d97c36386d38





---

