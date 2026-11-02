# Agnos MVP

Agnos is a document-cleaning application built with Next.js and React. It helps you find repetitive text in plain-text documents, review the proposed removals, and export the cleaned result.

## Project Overview

The app provides a workspace for adding text documents, applying configurable cleaning rules, and reviewing the results before export. It splits documents on form-feed page breaks (`\f`) so it can check page boundaries for repeated headers and footers. Cleaning is performed with transparent text-matching rules; the app does not use an AI model.

This is an MVP: documents and settings are held in React state in the browser, so uploaded content is not persisted after the app is refreshed.

## Features

- Upload a plain-text `.txt` file or paste document text.
- Identify repeated first and last non-empty lines across form-feed-separated pages.
- Optionally remove standalone page numbers and duplicate non-empty lines.
- Configure each cleaning rule independently.
- Compare the original with the cleaned text and restore individual removed lines.
- Export cleaned content as a `.txt` file or newline-delimited JSON (`.jsonl`).
- Browse sample documents included with the project.

## Technologies Used

- **Next.js 16** — application framework and App Router.
- **React 19** — UI components and in-browser document state.
- **Tailwind CSS 4** — styling foundation, alongside the app's global CSS.
- **JavaScript** — application source language.
- **ESLint 9** and `eslint-config-next` — code linting.

## Project Folder Structure

```text
agnos-mvp/
├── app/
│   ├── dashboard/       # Dashboard route (redirects to the home page)
│   ├── export/          # Cleaned document downloads
│   ├── review/          # Document review and restoration
│   ├── rules/           # Cleaning rule settings
│   ├── globals.css      # Global styles
│   ├── layout.js        # Root layout and document provider
│   └── page.js          # Main document workspace
├── components/
│   ├── Documents/       # Document list and text upload
│   ├── Export/          # Export interface
│   ├── Layout/          # Navigation and sidebar
│   ├── Review/          # Cleaned preview and removed-item review
│   └── UI/              # Shared interface components
├── context/
│   └── DocumentContext.js  # In-memory document and rule state
├── data/
│   ├── cleanDocument.js    # Text-cleaning and output helpers
│   └── dummyDocuments.js   # Sample documents
├── DESIGN-SYSTEM.md     # Current styling foundations and conventions
├── PRODUCT-ASSUMPTIONS.md
├── package.json         # Dependencies and npm scripts
└── README.md
```

## Installation Instructions

You will need [Node.js](https://nodejs.org/) and npm installed.

Clone the repository and install its dependencies:

```bash
git clone https://github.com/chetanmoger0578-eng/agnos-mvp.git
cd agnos-mvp
npm install
```

## How to Run the Project

Start the Next.js development server:

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

Other available project commands:

```bash
npm run lint
npm run build
npm run start
```

`npm run start` serves a production build; run `npm run build` first.

## Usage Instructions

1. Open the home page and add a `.txt` file or paste text into the upload area.
2. Select a document to open its review page.
3. Use **Cleaning rules** to enable or disable repeated-header, repeated-footer, page-number, and duplicate-line removal.
4. Clean the document, review the highlighted removals, and restore any lines you want to keep. The original text remains unchanged.
5. Open **Export documents** and download the cleaned text as TXT or JSONL.

Repeated headers and footers are detected from the first and last non-empty lines on pages separated by form-feed characters. Page-number matching and duplicate-line removal are based on text patterns, not document layout or AI analysis.

## Future Improvements

- Persist documents and rule preferences between visits.
- Support additional input and output formats.
- Add automated tests for cleaning rules and document workflows.
- Offer more cleaning rules and clearer controls for page detection.

## Project Team

- Chetan Moger
- Manohar U
- Imamhusen
