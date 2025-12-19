# Sales Agent

## Overview
The Sales Agent is an intelligent automation tool designed for processing Requests for Proposals (RFPs) in the electrical cables industry. It automates the scanning of tender portals, downloads and analyzes RFP documents, extracts key specifications, and generates human-readable review reports. This project is part of the EY Techathon, demonstrating multi-agent system capabilities for efficient RFP management.

## Features
- **Automated RFP Scanning**: Scans multiple tender portals (e.g., NTPC, GeM) for RFPs due within 90 days.
- **PDF Download and Analysis**: Downloads RFP PDFs, extracts specifications like conductor size, voltage, fire rating, and traceability.
- **Review Document Generation**: Creates detailed Technical Review Documents in PDF format for human review.
- **Selective Human Intervention**: Flags high-risk or complex RFPs for manual approval before forwarding to downstream agents (e.g., Technical Agent, Pricing Agent).
- **Mock Data Generation**: Includes tools to generate realistic mock tender portals and RFP PDFs for testing and demonstration.
- **Batch Processing**: Processes multiple unique RFPs in a single run, with deduplication to avoid redundancy.

## Architecture
The system follows a pipeline approach:
1. **Scan**: Extract tender links from portal HTML.
2. **Select**: Filter RFPs based on due dates and uniqueness.
3. **Download**: Fetch and store PDF documents.
4. **Analyze**: Parse PDF content to extract specs and traceability.
5. **Generate**: Produce review PDFs and queue for human review if needed.
6. **Forward**: Send approved RFPs to next agents in the workflow.

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/ChanikyaSaiL/Sales-Agent.git
   cd Sales-Agent
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

   Required packages: `requests`, `beautifulsoup4`, `PyPDF2`, `reportlab`.

## Usage
### Generate Mock Data
Create sample tender portals and RFP PDFs for testing:
```bash
python generate_mock_data.py
```

### Run the Sales Agent
Process RFPs from mock portals:
```bash
python demo.py
```

This will scan portals, download PDFs, analyze them, and generate review documents in the `output/` directory.

### Selective Human Review
- Check `output/review_queue.csv` and `output/review_queue.html` for RFPs needing approval.
- Edit the CSV to set `approved=yes` and add notes.
- Run the pickup routine (to be implemented) to forward approved items.

## Project Structure
```
Sales-Agent/
├── sales_agent.py          # Main Sales Agent logic
├── demo.py                 # Runner script for demonstration
├── generate_mock_data.py   # Mock data generator
├── requirements.txt        # Python dependencies
├── data/
│   └── rfps/               # Downloaded RFP PDFs
├── mock_tenders/           # Mock portal HTML files
├── output/                 # Generated review PDFs and queues
└── scripts/                # Utility scripts for debugging
```

## Technologies Used
- **Python 3**: Core language
- **Requests & BeautifulSoup**: Web scraping
- **PyPDF2**: PDF text extraction
- **ReportLab**: PDF generation
- **Git**: Version control

## Future Enhancements
- Integrate LangGraph for workflow orchestration
- Add real-time portal monitoring
- Implement full human-in-the-loop UI
- Expand to other industries beyond electrical cables

## Contributing
Contributions are welcome! Please fork the repository and submit a pull request.

## License
This project is licensed under the MIT License.

## Contact
For questions or feedback, reach out to the project maintainers.