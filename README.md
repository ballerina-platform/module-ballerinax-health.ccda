# module-ballerinax-health.ccda
HL7v3 CDA Ballerina Modules


This package is designed to handle CCDA (Continuity of Care Document Architecture) for healthcare data interoperability. It provides utilities to streamline the creation and management of CCDA-compliant documents.

## Features

- Parse CCDA documents and extract relevant data.
- Record representation for CCDA documents.

## Prerequisites

- Ballerina version 2201.12.0 or later

## Building the Package

To build the package, you need to have Ballerina installed on your system. Follow the instructions on the [Ballerina website](https://ballerina.io/downloads/) to install it.

Clone the repository and build the package using the following commands:

```bash
git clone https://github.com/ballerina-platform/module-ballerinax-health.ccda.git
cd module-ballerinax-health.ccda
bal build
```
## Usage

To use the package, import it in your Ballerina project:

```ballerina
import ballerina/io;
import ballerinax/health.ccda.r3;
```

## Example

Here's a simple example of how to use the package to parse a CCDA document:

```ballerina
import ballerina/io;
import ballerinax/health.ccda.r3 as ccda;

public function main() returns error? {
    // Sample CCDA document
    string ccdaDocument = "<ClinicalDocument>...</ClinicalDocument>";
    xml ccdXml = check xml:fromString(xmlStr);
    
    // Parse the CCDA document
    anydata parsedDocument = check ccda:parse(ccdXml);

    if parsedDocument is ccda:ContinuityofCareDocumentCCD {
        io:println("Parsed CCDA Document: " + parsedDocument.toString());
    } else {
        io:println("Failed to parse CCDA document: ");
    }
}
```
