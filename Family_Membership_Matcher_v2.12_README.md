# Family Membership Matcher v2.12

© Glen Carruthers

## What the app does

The Family Membership Matcher reviews a member Excel or CSV file and connects each **OTHER** member to their **FAMILY_HEAD**. It helps Membership Officers find missing family links and differences in payment dates, District, Squadron, and address information.

The app displays matched families, lets you search and view their full records, and creates Excel and CSV reports. It is a review tool: it does not edit your source file or update the membership system.

## Getting started

1. Save the app HTML file on your computer.
2. Double-click the file to open it in your web browser.
3. Have an internet connection when opening the app. Its Excel/CSV support loads from an online library.
4. Click **Choose Member File**, or drag your member file onto the upload area.
5. Wait for the activity spinner to finish and the results to appear.

Accepted file types: **.xlsx, .xls, and .csv**. For Excel files, the app reads **only the first worksheet**. Put column headings in the first row and member records below them.

## Required and optional columns

| Information | Recognized headings |
| --- | --- |
| Family role — required | Family Role |
| Link to family head — required | Family Head Uid / Family Head UID |
| Member identifier — required | User ID / UserID / Member ID / Individual ID |
| First name | First Name / FirstName / givenName / Given Name |
| Last name | Last Name / LastName / surname |
| Payment date | Next Payment Date / NextPaymentDate |
| District | District / District Name / districtNames |
| Squadron | Squadron / Squadron Name / squadronNames |
| Address line 1 | Address 1 / Address1 / Address Line 1 / addressLine1 |
| Address line 2 | Address 2 / Address2 / Address Line 2 / addressLine2 |
| City | City / Home City / Home City/Town |
| Province | Province / Province State / ProvinceState / provinceState / Prov |
| Postal code | Postal Code / PostalCode / Zip Code / ZIP |

Heading recognition ignores capitalization, spaces, and punctuation. If several identifier columns are present, the app prefers **User ID**, then **UserID**, then **Member ID**, then **Individual ID**. Make sure the OTHER member’s Family Head Uid contains the value from the identifier column being used.

Optional columns enable the corresponding searches or checks. All original columns, including fields such as email and phone numbers, are available in the full family details. This version does not recognize **ecommerceexpiryDate** as the payment date heading; rename that heading to **Next Payment Date** if necessary.

## How family matching works

- The app recognizes FAMILY_HEAD and OTHER roles, ignoring capitalization, spaces, and punctuation in the role text.
- Each OTHER member’s **Family Head Uid** is compared with the FAMILY_HEAD’s member identifier.
- One family can have several OTHER members. The results contain one row for each matched OTHER member, with the head’s information repeated.
- Results are sorted by Family Head ID, then by OTHER Member ID.
- An OTHER member without a matching head appears under **Missing Family Links**.
- A head without any linked OTHER member also appears under **Missing Family Links**.
- Duplicate head IDs are recorded for review. Matching uses the first head record found for that ID; review the duplicate records in the Excel report.

Names and addresses help you investigate records, but they are not used to establish the family link. Records with roles other than FAMILY_HEAD or OTHER are not included in family matching. The app does not filter families by Membership Type or determine whether membership is active or expired.

## Understanding the summary

| Summary box | Meaning |
| --- | --- |
| Matched families | Number of distinct matched Family Head IDs within the date/year selection |
| Family heads | Number of matched families; heads without OTHER members are not included here |
| Other members | Number of matched OTHER records within the date/year selection |
| Records needing review | Missing heads, heads missing OTHER members, plus duplicate head ID occurrences |

The **Records needing review** box does not include payment, unit, or address mismatches. Those appear as coloured matched rows and in separate Excel worksheets. Duplicate occurrences in this box are counted across the loaded file, while missing links follow the date/year selection. The Excel duplicate worksheet lists all duplicate head records that satisfy the date/year selection, so its total may differ from the box.

Text searches narrow the matched table and its “Showing…” count; they do not change the summary boxes or Missing Family Links table.

## Filtering by Next Payment Date

### Select a year

Leave **From** and **To** blank, then select a year under **Next Payment Year**. Use **All Years** to remove the year restriction. Available years come from the loaded payment dates.

### Select a date range

1. Enter a **From** date, a **To** date, or both.
2. Click **Apply Date Range**. Changing either date also applies the range automatically.
3. Read the status message and review the displayed families.

Both endpoints are included. A From date alone includes that date and later dates; a To date alone includes that date and earlier dates. The From date must not be later than the To date.

Entering a range clears the year selection. To return to a year filter, click **Clear Dates**, then choose the year. To display every date, clear the dates and select **All Years**.

**A whole matched family is included when any linked family member has a Next Payment Date within the selection.** All connected OTHER members are then shown, including those whose own dates fall outside the selection. This allows you to compare dates within the family.

Missing-link records are filtered by their own payment date. Blank or unreadable payment dates are excluded when a date/year filter is active. Use clear, consistent dates such as **2026-10-07** to avoid ambiguity.

## Searching for a family

Use any combination of these fields:

| Search field | What it searches |
| --- | --- |
| Last Name | The head’s and linked OTHER members’ last names |
| Address 1 | The head’s and linked OTHER members’ first address lines |
| Postal Code | Family postal codes, ignoring spaces and punctuation |
| Family Head UID | All or part of the linked Family Head ID |
| General search | All original fields for the head and linked OTHER members, plus the Family Head ID |

Searches ignore capitalization and accept partial text. A matching family is shown together with all its connected OTHER members. When several search boxes contain text, the family must satisfy every box; different members of the family may satisfy different boxes. Searches also respect the date/year selection.

Use **Clear General Search** to empty only the general search field. Use **Clear All Search Filters** to empty every text search field. These buttons do not clear date/year filters.

## Colours and status messages

| Colour or label | Meaning |
| --- | --- |
| Green “Matched” label | The link exists and no checked differences were found |
| Red matched row | Head and OTHER payment dates differ |
| Gold matched row | District and/or Squadron differ |
| Teal matched row | Address 1, Address 2, City, and/or Province differ |
| Purple matched row | More than one mismatch category is present |
| Alternating pale blue/purple group shading | Groups multiple OTHER members belonging to the same head when no mismatch colour takes priority |
| Red in Missing Family Links | OTHER member has no matching FAMILY_HEAD |
| Amber in Missing Family Links | FAMILY_HEAD has no linked OTHER member |

Read the **Status** text to see the specific differences. A blank value on one side and a populated value on the other can produce a mismatch. Postal codes can be searched but are not part of the address mismatch check. Multiple OTHER members are grouped for review; their presence alone is not flagged as an error.

## Viewing complete family records

Click **View All** beside a matched row. The page scrolls to **Family Details**, showing the FAMILY_HEAD and a separate record for each connected OTHER member. Each record displays every column from the source file.

The details are read-only. In this version, the Missing Family Links rows do not have a View All button; inspect those records in the Excel report or source file.

## Exporting reports

### Export Excel Report

Click **Export Excel Report** and wait for the spinner. The downloaded workbook contains:

| Worksheet | Contents |
| --- | --- |
| Summary | Date/year selection, source record count, family totals, and issue counts |
| Matched Families | Matched head/OTHER pairs and their status |
| Payment Date Issues | Pairs with different payment dates |
| District Squadron Issues | Pairs with District or Squadron differences |
| Address Issues | Pairs with address, city, or province differences |
| Missing Family Head | OTHER records without a matching head |
| Missing Other Member | Heads without linked OTHER members |
| Duplicate Head IDs | Head records sharing an identifier |

A pair with several kinds of issues can appear in several issue worksheets. Do not add those worksheet counts together as a count of unique members.

The filename follows **Family_Membership_Match_Report_All_Years_v2.12.xlsx**, with the selected year replacing All_Years when applicable. A custom range is recorded in the Summary worksheet, rather than in the filename.

### Export Matched CSV

Click **Export Matched CSV** for a simpler file containing matched pairs, status, identifiers, names, payment dates, District, and Squadron. It does not contain the separate issue worksheets or the full source records.

**Both exports follow the date/year selection but ignore the text search boxes.** They may therefore contain more matched rows than the searched table currently displays. Exported worksheets contain selected report fields, rather than every original source column.

Your browser saves the files using its normal download settings. Check its Downloads list or folder after the spinner finishes.

## Clearing data and starting again

Click **Clear** to remove the loaded results, searches, and date selection. Then choose another member file. The app does not remember loaded member data after the page is closed or refreshed; export the reports you want to keep.

## Troubleshooting

| Problem | What to check |
| --- | --- |
| “Excel support could not load” | Connect to the internet, reopen or refresh the app, and load the file again. |
| Missing required column message | Check the first worksheet and the required headings listed above. |
| No data rows | Make sure the first worksheet contains records below its headings. |
| Family members do not match | Check the OTHER member’s Family Head Uid against the head’s selected identifier column. Also check the role values and consistent ID formatting, including leading zeros. |
| No records within a date range | Clear text searches, verify Next Payment Date is recognized, check the date format, and try All Years with dates cleared. |
| Extra family members appear outside the date range | This is expected: the app keeps the entire matched family when any family member falls within the range. |
| Export has more rows than the displayed search | Exports ignore text searches and use only the date/year selection. |
| No download appears | Check the browser’s Downloads list and download permissions. If an activity error appears, reload the app and try again. |

## Suggested review process

1. Load the complete member file and review all families first.
2. Export the Excel report and investigate missing links and duplicate head IDs.
3. Review payment, District/Squadron, and address differences.
4. Use searches and View All to inspect complete family records.
5. Make any confirmed corrections in your authorized source or membership system.
6. Load a fresh export to verify the corrections.

Member data is processed in the browser by this app; its code does not send the selected member file to a server. Keep the source file and downloaded reports in a suitable location because they contain personal information.
