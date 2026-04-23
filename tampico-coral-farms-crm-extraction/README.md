# Tampico Coral Farms — CRM Data Extraction & HubSpot Import

### **1. The Hook *(1 sentence)***
Extracted and structured 5+ years of purchase history from 1,291 invoices across 64 customers into a clean, HubSpot-ready CRM dataset — turning a folder of Word documents into actionable customer intelligence.

### **2. Client / Context *(1–2 sentences)***
Tampico Coral Farms is a specialty coral aquaculture business that sells live corals (SPS, LPS, Soft Corals, Invertebrates) to aquarium retailers across the United States. They had no CRM in place and all customer records existed only as individual invoice files scattered across a shared Google Drive folder.

### **3. The Problem**
All customer contact information and purchase history lived exclusively inside individual `.docx` invoice files — one per order, organized by customer folder and year. There was no central record of who their customers were, how much they had spent, what they bought, or how to contact them. Before importing into HubSpot, every piece of data had to be extracted from 1,291 invoices. The core challenge was identifying the customer (receiver) fields on each invoice versus the sender's own information, parsing unstructured Word document tables for addresses, emails, phone numbers, and line items, classifying products into coral taxonomy categories, and merging everything into a single HubSpot-compatible import file.

### **4. My Role**
I designed and executed the full data pipeline end-to-end: connecting to Google Drive via rclone MCP, downloading all invoice files, writing the extraction and parsing scripts, building the field mapping to HubSpot's contact schema, and delivering the final import-ready CSV.

### **5. The Solution *(your process)***
Connected to Google Drive via rclone MCP to access the shared "Customer Information" folder containing 68 customer subfolders and 1,291 `.docx` invoice files, avoiding slow browser automation entirely. All invoices were parsed with `python-docx`, reading structured Word document tables to extract the "Bill To" section — customer name, address, phone, and email — while explicitly filtering out the sender's own contact information. Products were classified by matching line item descriptions against a coral taxonomy tree covering SPS, LPS, Soft Corals, Zoanthids, Mushrooms, Invertebrates, and WYSIWYG categories. A deep scan of all invoice text was then run to recover emails and phone numbers missed in the first pass using regex pattern matching across every paragraph and table cell. All fields were finally mapped to HubSpot's standard contact schema, with custom properties created for purchase history metrics including Total Spend, Total Orders, Lifetime Value, Average Order Value, Most Recent Product, and Top Product Category.

### **6. The Result *(lead with numbers)***
- **Primary metric:** 64 customer records fully structured and ready for HubSpot import — from zero CRM data
- **Secondary metrics:** 91% of customers now have contact first names (up from 0%); 98% have top product category and most recent product classified
- **Qualitative impact:** Tampico Coral Farms can now import directly into HubSpot, segment customers by product preference and lifetime value, and begin targeted outreach — something that was previously impossible without a major manual data entry effort

### **7. Visual / Screenshot**
The final deliverable is a 64-row, 25-column HubSpot contact import file with all extracted and enriched customer data, formatted to HubSpot's contact import schema and ready for immediate upload.

### **8. Tools Used**
`Python` · `python-docx` · `pandas` · `rclone` · `Google Drive MCP` · `regex` · `HubSpot` · `Google Sheets` · `Manus AI Agent`

### **9. Type Tag**
**Agent / Case Study** — Autonomous data extraction agent + CRM migration workflow
