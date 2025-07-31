# 📊 Take-Home Assignment: FIFA World Cup Data Extraction to Google Sheets

## 👋 Overview

This document outlines the process of extracting structured data from the **Wikipedia page: [List of FIFA World Cup finals](https://en.wikipedia.org/wiki/List_of_FIFA_World_Cup_finals)** and appending the extracted data into a **Google Sheet** using the **Google Sheets API via Postman**.

All steps have been designed strictly using only the available building blocks from the **Step Library for IE assignment**.

---

## 🧾 Task Objective

Extract the following information from the **first 10 rows** of the Wikipedia table:

* **Year**
* **Winner**
* **Score**
* **Runners-up**

Append this data into a **Google Sheet** using the **Google Sheets API POST method**, configured and invoked via **Postman**.

---

## 🔧 Tools and Technologies

* **Wikipedia** (source of tabular data)
* **Google Sheets API**
* **Postman** (for sending the POST request)
* **Mermaid.js** (for flowchart visualization)

---

## 🗺️ Flowchart

The complete process is visualized using **Mermaid.js** and includes all logical steps from data extraction to API call. The flowchart includes:

* Iterative DOM parsing from the Wikipedia table
* Construction of a row array
* API call block (`POST` to Sheets endpoint)
* Visual callout blocks for API parameters

You can view the interactive flowchart live at:

🔗 [Mermaid Live Editor Flowchart](https://mermaid.live/edit#)

> The following file formats are attached:
>
> * `flowchart.svg`
> * `flowchart.png`
> * `mermaid-flowchart.txt`

---

## 🪜 Step-by-Step Breakdown (Based on Step Library)

| Step            | Description                                                                                                                      |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| **Open page**   | Navigates to the [Wikipedia page](https://en.wikipedia.org/wiki/List_of_FIFA_World_Cup_finals) that contains the required table. |
| **Loop**        | Iterates from **1 to 10**, corresponding to the first 10 rows of the Wikipedia table.                                            |
| **ExtractHTML** | Captures DOM elements for each of the 4 fields: Year, Winner, Score, and Runners-up using XPath.                                 |
| **Append Row**  | Builds an in-memory JSON array with each extracted row: `[ "1930", "Uruguay", "4–2", "Argentina" ]`                              |
| **Call API**    | Sends a `POST` request to Google Sheets API with the final JSON payload.                                                         |

---

## 🧩 DOM Paths Used for Extraction

The XPath for each table column is based on the structure of the first table on the Wikipedia page:

| Field      | XPath                                                          |
| ---------- | -------------------------------------------------------------- |
| Year       | `//*[@id="mw-content-text"]/div[1]/table[1]/tbody/tr[i]/td[1]` |
| Winner     | `//*[@id="mw-content-text"]/div[1]/table[1]/tbody/tr[i]/td[2]` |
| Score      | `//*[@id="mw-content-text"]/div[1]/table[1]/tbody/tr[i]/td[3]` |
| Runners-up | `//*[@id="mw-content-text"]/div[1]/table[1]/tbody/tr[i]/td[4]` |

---

## 📤 Google Sheets API Request Details (cURL / Postman)

### ✅ Endpoint

```http
POST https://sheets.googleapis.com/v4/spreadsheets/{spreadsheetId}/values/{range}:append?valueInputOption=USER_ENTERED
```

### 📌 Parameters

| Parameter          | Description                                                                                     |
| ------------------ | ----------------------------------------------------------------------------------------------- |
| `spreadsheetId`    | The unique ID of your Google Sheet (from URL after `/d/`). Example: `1Xz3ABC456DEFG_HijklMN...` |
| `range`            | The target sheet and range. Example: `Sheet1!A1:D1`                                             |
| `valueInputOption` | `USER_ENTERED` to respect formatting and evaluate formulas, or `RAW` to insert as-is            |

### 🧾 Headers

```http
Authorization: Bearer <ACCESS_TOKEN>
Content-Type: application/json
```

> ⚠️ Ensure the token has scope:
> `https://www.googleapis.com/auth/spreadsheets`

### 📦 Request Body (JSON)

```json
{
  "values": [
    ["1930", "Uruguay", "4–2", "Argentina"],
    ...
  ]
}
```

---

## 📎 References & Attachments

* ✅ [Wikipedia Page](https://en.wikipedia.org/wiki/List_of_FIFA_World_Cup_finals)
* ✅ [Google Sheets API: Append Values](https://developers.google.com/sheets/api/reference/rest/v4/spreadsheets.values/append)
* 📎 `flowchart.svg`, `flowchart.png`, `mermaid-flowchart.txt`

---

## 📬 Submission

completed, submitted:

* The flowchart (PNG/SVG)
* Mermaid source code (text file)
* This `README.md`
---

## 🙋 Questions?

If you have any questions or need clarification, feel free to reach out to me on this account details / email-id.

