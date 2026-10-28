NEET 2027 CBT + STUDENT HISTORY UPDATE PACKAGE

Files:
- index.html: homepage, AIIMS Rishikesh photo, live countdown to 2 May 2027, existing test/question-bank links, Student Result History link.
- BTS-01_NEET_2027_CBT.html / BTS-02_NEET_2027_CBT.html / BTS-03_NEET_2027_CBT.html: CBT pages with timer, question palette, clear response, mark for review, auto-submit, per-student attempt numbering, LocalStorage history, Supabase sync, and question-wise result review. BTS-03 has no verified answer key in the supplied source.
- student-dashboard.html: sign-in page, cross-attempt result comparison, and a View Review action for saved question-level details (all, wrong, unattempted).
- supabase_setup.sql: table and row-level security setup for Supabase.
- NEET_Question_Bank_Generator_25901.html + questions.json: existing question bank generator and question data.
- 39 imported Test 1–40 HTML papers: linked from the Additional Practice Tests section. Each now saves attempt summaries and question-level selected/correct answer details locally; signing in enables Supabase sync.
- NEET_40K_Custom_Question_Bank_Generator.html: existing 40K generator entry page.

IMPORTANT SETUP:
1. Open supabase_setup.sql and run it once in Supabase Dashboard > SQL Editor for the same Supabase project configured in the BTS files.
2. Confirm the Supabase project URL and publishable/anon key in the CBT files belong to your own project. Never put a service_role key in browser code.
3. Supabase Auth email sign-up/sign-in must be enabled. If email confirmation is enabled, students must confirm their email before signing in.
4. Supabase saves cloud history only after the SQL schema and RLS policies are installed. LocalStorage saves on the same browser/device even if cloud sync fails.
5. BTS-03 has no answer key in the supplied source, so it records attempt/answer details but deliberately does not invent correct/wrong counts or a score for that paper. Add a verified key before scoring BTS-03.
6. The countdown target is 2 May 2027 at 00:00 IST. This is the target date supplied by the project owner; check official NTA notices for the final exam schedule.
7. The campus image is loaded from Wikimedia Commons and includes attribution; internet is needed for that image.
8. This package is not deployed to Vercel. Upload/extract the full folder to the correct GitHub repository, then redeploy. Test sign-up, submission, local history and Supabase history before sharing the site.

- pdf-to-cbt.html: PDF-to-CBT admin tool. Upload a question PDF and optional answer-key PDF, extract text with PDF.js, optionally OCR scanned pages, review/edit questions/options/answers, then download a generated CBT HTML file.

PDF-TO-CBT NOTES:
1. Open pdf-to-cbt.html from the deployed website. Internet is needed for PDF.js and optional Tesseract OCR.
2. Upload the question PDF and, if separate, the answer-key PDF. Review every extracted question and answer before generating.
3. This tool is a best-effort parser. It cannot guarantee exact extraction for all layouts. Review the extracted text, options, answer key and diagrams/images before generating; correct any missing content manually.
4. Downloaded CBT files are not automatically pushed to GitHub. To make a new test available to all students, upload the downloaded HTML file to the repository, add a link to index.html, and redeploy Vercel. Drafts saved in LocalStorage exist only in that browser.
5. The generated CBT uses the project's configured Supabase project/key for optional cloud result sync after student sign-in. Verify the project is yours and run supabase_setup.sql before use. Never expose a service_role key.

UPDATE NOTES:
- Student dashboard now fetches question_details from Supabase and opens a per-attempt review with filters for wrong and unattempted questions.
- PDF-generated CBT attempts use the same aim2aiims_attempts_<student key> LocalStorage convention as the dashboard and omit non-schema fields from cloud inserts.
- Imported legacy test pages include optional Supabase sign-in, local attempt persistence, attempt numbering, and question-level result details. Cloud sync requires supabase_setup.sql to have been run successfully.
