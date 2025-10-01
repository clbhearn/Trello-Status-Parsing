# Trello-Status-Parsing
This is a lightweight tool that helps track the status of cards across selected Trello lists. It extracts the **first line of each card's description** (used as a status), filters out archived cards, groups them by list, and exports the results into a cleanly formatted Word document.

# Why I Built This
Trello is great for organizing partnership pipelines and project tracking, but exporting structured status updates for reporting or sharing can be tedious. This script automates that process, making it easy to generate a readable status report from a Trello board export — especially useful for program managers, partnership teams, or research project coordinators.

# Features
- Filters only the lists you care about (customizable)
- Skips archived cards
- Extracts the **first line** of each card’s description as the status
- Exports to `.docx` (Word) with:
  - Bold section headers (list names)
  - Bullet-style formatting for card titles
  - Indented sub-bullet for statuses

## 🖥️ Example Output
== "List 1 Name" ==<br>
•"Card 1 Name"<br>
&nbsp;&nbsp;&nbsp;&nbsp;o Status: "Text in First Line of card"
  <br>
•"Card 2 Name"<br>
&nbsp;&nbsp;&nbsp;&nbsp;o Status: "Text in First Line of card"
<br>

== "List 2 Name" ==<br>
•"Card 1 Name"<br>
&nbsp;&nbsp;&nbsp;&nbsp;o Status: "Text in First Line of card"
  <br>
•"Card 2 Name"<br>
&nbsp;&nbsp;&nbsp;&nbsp;o Status: "Text in First Line of card"
<br>


## How to Use

### 1. Export your Trello board to JSON

Go to your Trello board → top-right menu → **More** → **Print and Export** → **Export JSON**.
### 2. Customize code

To run this script locally, you’ll need to make a few small adjustments:

- Set the input file path

  - By default, the script looks for a Trello JSON export at: 
  ```python
  example_data/trello_export.json
  ```
  - If your file is in a different location, either:
  
    - Pass the path as a command-line argument:
  ```python
  python trello_status_reporter.py /path/to/your/export.json
  ```
  
    - Or update the fallback path directly in the script (in the main() function).

- Update the target Trello lists

  - Inside the script, there’s a variable called `target_lists`. This controls which Trello lists will be included in the output report.
```python
target_lists = ["List1", "List2", "List3", "List4"]
```

  - Replace these with the exact names of the lists on your Trello board (e.g., "In Progress", "Done").

- (Optional) Rename the output file

  - By default, the script creates a Word document called:
```
trello_status_report.docx
```

  - You can change this by editing the output_path variable in the main() function.
### 3. Run the script

```bash
python trello_status_reporter.py /path/to/your/trello_export.json
```

The script will generate a file named partnership_status_report.docx (you can rename this in the code).

### 3. Open the output
trello_status_report.docx


### Dependencies

Install via pip:

```bash
pip install -r requirements.txt
```

### Requires Python 3.7+

### Customization

To change which Trello lists are included, update the target_lists variable in the script.

To change the output file name or folder, modify the output_path.

### Potential Enhancements

- Live Trello API integration (no manual JSON export)
- Export to CSV or Markdown
- GUI or web version
- Slack/Email integration for automated reporting

