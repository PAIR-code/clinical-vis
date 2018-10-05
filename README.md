# ClinicalVis

ClinicalVis is a medical record visualization that attempts to improve upon the
baseline table-based medical record visualizations.

This project contains two Polymer elements:
* clinical-vis: The updated medical record visualization
* clinical-table: A baseline table-based medical record visualization

## Install the Polymer-CLI

First, make sure you have the
[Polymer CLI](https://www.npmjs.com/package/polymer-cli) installed. Then run
`polymer serve` to serve your element locally.

## Viewing demos of the elements

From this top-level clinical-vis directory:
```
$ polymer install
$ polymer serve
```
Then navigate to:
* `http://localhost:8081/components/clinical-vis/demo/index.html` for a demo of
  the clinical-vis visualization
* `http://localhost:8081/components/clinical-vis/demo/table-index.html` for a
  demo of the baseline clinical-table visualization

## Using the elements

Each of the elements exposes a single bound parameter, 'json', which should be
set to a JSON object containing the patient record to visualize. This is the
expected format of the JSON object:

Top level key-value pairs:
* 'diagnosis': (string) Admitting diagnosis
* 'dob': (string) Date of birth (YYYY-MM-DD)
* 'ethnicity': (string) Ethnicity
* 'gender': (string) Gender
* 'icu_type': (string) ICU type
* 'notes': (array) List of notes in the medical record, see below.
* 'events': (array) List of events in the medical record, see below.

Each note in the 'notes' field is an object with the following key-value pairs:
* 'timestamp': (string) Number of seconds since UNIX epoch when the note was
  taken
* 'category': (string) Category of the note, such as "Nursing" or "Radiology"
* 'note': (string) Text of the note.

Each event in the 'events' field is an object describing a measured or observed
value with the following key-value pairs:
* 'timestamp': (string) Number of seconds since UNIX epoch when the event was
  recorded
* 'key': (string) Name of the event, such as 'Temperature' or 'Heart Rate'
* 'category': (string) The category of the event, such as 'Vitals' or 'Labs'
* 'value_string': (string) If the event data is a string, such as the the value
  'Clear' for the category 'Lung Sounds', then this field holds the value.
* 'value_num': (number) If the event data is a number, such as the the value
  165 for the category 'Platelets', then this field holds the value.

## This is not an official Google product
