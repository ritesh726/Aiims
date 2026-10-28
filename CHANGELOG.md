# NEET 2027 CBT package changes

- Added a live countdown targeting 2 May 2027 (midnight IST) to the homepage.
- Added an AIIMS Rishikesh campus image with Wikimedia Commons attribution.
- Added Student Result History link and `student-dashboard.html`.
- Added mark-for-review and clear-response controls to BTS-01/02/03 CBT pages.
- The exam timer starts only after a student signs in.
- Results save to browser LocalStorage and attempt cloud sync to Supabase.
- Attempt numbers are sequential per student and test; result screen shows previous attempt and mark change where scored.
- BTS-03 does not include a verified answer key in the supplied files, so its marks/correct/wrong counts are intentionally not invented.

## Required before cloud sync works
Run `supabase_setup.sql` in the matching Supabase project's SQL Editor, then test sign-up, email confirmation (if enabled), sign-in, and submission. If the configured project URL/key are not yours, replace them with your own Supabase project URL and publishable/anon key. Never put a service-role key in browser HTML.

- Added PDF-to-CBT admin page: extract text from question PDFs, optional OCR for scanned pages, optional answer-key PDF import, editable question preview, answer validation, local draft saving, and standalone CBT HTML export. Added homepage link to the generator.
- Publishing to all students still requires uploading the generated CBT HTML file to GitHub and redeploying Vercel; browser-local drafts are not public.


## Image and diagram support
- PDF-to-CBT admin now renders each uploaded PDF page as a compact JPEG image bank.
- Each question can select the relevant source PDF page to include its diagrams/figures in the generated CBT.
- Each question can alternatively upload a cropped image (PNG/JPG/WebP); uploaded image takes priority over the selected page.
- Generated CBT HTML embeds the image data and displays the question image above its options, including on mobile.
- PDF page images are stored once in the generated file and referenced by page number to avoid duplicating large image data for every question.
- Admin preview supports checking the image selected for each question.
- This is page-image capture, not perfect automatic diagram cropping: select the correct page or upload a crop for best results.


## Result review improvement
- Added a dedicated Incorrect & Unattempted Questions section to BTS-01/02/03 results, showing all options and marking the student's answer and correct answer.
- Updated PDF-to-CBT generated tests to include the same focused review section for wrong and unattempted questions.


## Attempt history and review update (2026-10-28)
- Student Result History now fetches `question_details` from Supabase and provides per-attempt review with filters for all, wrong, and unattempted questions.
- PDF-generated CBTs save attempt records under the same per-student LocalStorage key used by the dashboard; cloud inserts now omit fields not present in the Supabase table.
- Added optional Supabase sign-in and attempt persistence to the 39 available imported Test 1–40 HTML papers. Each saves attempt number, date/time, score, correct/wrong/unattempted totals, accuracy, and question-level answers.
- Added all 39 imported practice papers to the homepage. Test 14 was not present in the supplied Tests 1–40 archive, so only the 39 supplied files are linked.
- Verified JavaScript syntax for all 47 HTML files. BTS-03 remains unscored until a verified answer key is supplied.

## Homepage branding update
- Updated only the homepage (`index.html`) header to show `DR RITESH KUMAR | AIM2AIIMSRISHIKESH`. Other page headers were left unchanged.
