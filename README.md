### **Project: ScryVault**

**Purpose:** A web-based application designed for rapid, real-world inventory management for the specialized online bookstore, Ældern Tomes. The app is optimized for mobile use on an iPhone.

### **Technology Stack**

* **Frontend:** HTML, Tailwind CSS, JavaScript  
* **Database:** Supabase (PostgreSQL)  
* **External Libraries:**  
  * lucide-icons for UI icons.  
  * zxing/library for barcode scanning via the device camera.  
* **Deployment:** Live on Netlify via Netlify Drop.

### **Current Features & Status (As of end-of-day, June 26\)**

* **Database Schema:** A robust, two-table schema is implemented.  
  * books: Stores master record for a title (ISBN/ID, Title, Author, Publisher, Binding, Cover URL).  
  * inventory: Stores each unique copy with its own details (Condition, Purchase Price, Market Price, Date Purchased, Location Purchased, Notes, Listed Status).  
* **Core Functionality:**  
  * **Live ISBN Scanner:** Uses the phone's camera to scan barcodes.  
  * **Manual Entry:** Allows adding books that predate ISBNs or aren't found in online databases.  
  * **Multi-Copy Tracking:** The system correctly handles multiple copies of a single title.  
  * **Interactive "Listed" Status:** Users can toggle the is\_listed status of any inventory item directly from the main view.  
* **User Interface:**  
  * The collection is displayed as an **accordion**, where each book title can be expanded to show the inventory of its individual copies.  
  * The UI is mobile-first but functional on desktop.  
  * The information hierarchy on each book card has been adjusted to prioritize Title, ISBN, and Publisher info.  
* **Known Good State:** The event bubbling issue (clicking a button and collapsing the accordion) has been fixed. The app is stable and functional.

### **Next Steps & To-Do List**

1. **Improve Data Quality:**  
   * **Priority \#1:** Switch the data lookup from the **OpenLibrary API** to the more robust **Google Books API** to get more accurate metadata and, crucially, better cover images.  
   * Implement an **"Edit Before Saving"** workflow. After looking up a new book, the app should present the fetched data in an editable form, allowing the user to verify/correct the cover art, publisher, etc., before creating the master record in the database.  
2. **UI/UX Refinements:**  
   * Implement an "item detail page" or an "edit copy" modal, accessible by clicking/tapping on a specific inventory copy. This would allow for editing details after the initial entry.  
   * Add a search/filter bar for the main collection view.