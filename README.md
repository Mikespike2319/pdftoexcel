# PDF to Excel Converter

A local, offline web application that extracts tabular data from PDF files and converts it to Excel format.

## Features

- **Local Processing**: All processing happens in your browser - no data is sent to external servers
- **Table Detection**: Automatically detects tables in PDF pages using text positioning
- **Flexible Page Selection**: Process specific pages or page ranges
- **Configurable Parameters**: Adjust row and column tolerance for better table detection
- **Multiple Output Options**: One worksheet per table or per page
- **Progress Tracking**: Real-time progress updates with ETA
- **Modern UI**: Clean, responsive interface

## How to Use

1. **Open the Application**: Open `pdf-to-excel.html` in your web browser
2. **Select a PDF File**: Click "Choose PDF File" and select your PDF
3. **Configure Options**:
   - **Pages to parse**: Enter page numbers or ranges (e.g., "1-50, 120, 300-350")
   - **Row tolerance**: Adjust how close text items need to be to be considered in the same row (default: 2.5px)
   - **Column clustering tolerance**: Adjust how close text items need to be to be considered in the same column (default: 6px)
   - **Output options**: Choose between one worksheet per detected table or per page
4. **Process**: Click "Parse & Export" to start processing
5. **Download**: The Excel file will be automatically downloaded when processing is complete

## Parameters Explained

### Row Tolerance (y-merge)
- Controls how close text items need to be vertically to be grouped into the same row
- Lower values (1-3px) for tightly formatted tables
- Higher values (5-10px) for loosely formatted tables

### Column Clustering Tolerance (x-cluster)
- Controls how close text items need to be horizontally to be grouped into the same column
- Lower values (3-6px) for tables with narrow columns
- Higher values (8-15px) for tables with wide columns

## Output Options

### One Worksheet Per Detected Table
- Creates separate worksheets for each table found in the PDF
- Worksheet names: `p{page}_t{table_number}` (e.g., `p1_t1`, `p1_t2`)
- Best for PDFs with multiple distinct tables

### One Worksheet Per Page
- Creates one worksheet per page containing all detected tables
- Worksheet names: `page_{page_number}` (e.g., `page_1`, `page_2`)
- Best for PDFs with tables that span multiple pages

## Technical Details

- **PDF Processing**: Uses PDF.js for text extraction and positioning
- **Excel Generation**: Uses SheetJS for Excel file creation
- **Table Detection**: Custom algorithm based on text positioning and clustering
- **Browser Compatibility**: Works in all modern browsers (Chrome, Firefox, Safari, Edge)

## Troubleshooting

### No Tables Detected
- Try increasing the row and column tolerance values
- Check if the PDF contains actual text (not just images)
- Try processing individual pages to isolate issues

### Poor Table Structure
- Adjust the tolerance parameters
- Try different page ranges
- Check the log output for warnings or errors

### Large Files
- Process pages in smaller batches
- Close other browser tabs to free up memory
- Consider splitting large PDFs into smaller files

## File Structure

```
pdf-to-excel.html    # Main application
pdf.min.js          # PDF.js library
xlsx.min.js         # SheetJS library
test.html           # Library test file
README.md           # This file
```

## Browser Requirements

- Modern browser with JavaScript enabled
- Support for File API and Blob API
- Support for Web Workers (for background processing)
- At least 100MB of available memory for large PDFs

## Privacy

This application processes all data locally in your browser. No files or data are sent to any external servers. Your PDF content never leaves your device.
