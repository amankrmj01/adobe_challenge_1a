# Adobe Challenge 1A: Structured Outline Extraction

## Objective
Extract the title and hierarchical headings (H1, H2, H3) from any PDF document, outputting a clean, structured JSON outline. This enables foundational understanding and downstream document analysis.

## Methodology
1. **Font Feature Analysis:** Analyze font sizes and boldness throughout the document to dynamically identify heading styles.
2. **Adaptive Heading Detection:**
   - **Rule-Based Filtering:** Exclude non-heading elements (page numbers, TOC entries, long lines, sentences ending with punctuation).
   - **Regex Pattern Matching:** Capture structured, numbered headings (e.g., "1. Introduction", "2.1. Sub-section").
   - **Font-Based Fallback:** Detect unnumbered headings using font size and boldness.
3. **Title Identification:** Select the largest, most prominent text on the first page as the document title.
4. **Post-processing:** Deduplicate and clean the extracted outline for accuracy.

## Key Files
- `outline_extractor.py`: Implements PDF text analysis and heading extraction logic.
- `config.py`: Stores configuration parameters for input/output and extraction settings.
- `requirements.txt`: Lists required Python packages (e.g., pdfplumber).
- `Dockerfile`: Containerizes the solution for reproducible execution.

## Technologies Used
- Python
- pdfplumber (PDF parsing and layout analysis)


## Usage
1. Place your input PDFs and scenario files in the designated input directory. The input directory should contain pdfs to be extracted.

2. Build the Docker image:
   ```sh
   docker build -t amankrmj01/adobe-1a .
   ```
3. Run the Docker container, mounting your input and output directories:
   ```sh
   docker run --rm -v D:\dev_mode\test\input:/data/input:ro -v D:\dev_mode\test\output:/data/output --network none amankrmj01/adobe-1a
   ```
   - Replace `D:\dev_mode\test\input` with the path to your input folder containing pdfs.
   - Replace `D:\dev_mode\test\output` with the path to your desired output folder.

## Docker
A Dockerfile is provided to simplify setup and execution:
- Uses a Python base image.
- Installs all required dependencies from `requirements.txt`.
- Copies source files and sets up the entrypoint to run `main.py`.

This allows you to run the solution in a consistent environment without manual Python setup.

---

This approach enables robust, adaptive extraction of document outlines for further analysis or integration into larger document intelligence workflows.