
# File Processing Application

This application processes files for various instruments by reading input files, organizing their data, and saving the processed results into new directories.

## Supported Instruments

The following instruments are currently supported by this application:

- PK

## Usage Instructions

### Running the Application

To run the application, you need to provide pairs of instrument names and their associated directories as command-line arguments. Each pair consists of the instrument name followed by a space and the path to the directory containing the files for that instrument.

Example:
```bash
FileProcessingApp.exe PK "C:\path\to\PK\directory"
```

You can specify multiple instrument-directory pairs by providing additional arguments:
```bash
FileProcessingApp.exe PK "C:\path\to\PK\directory" AnotherInstrument "C:\path\to\AnotherInstrument\directory"
```

### Directory Structure

For each instrument, the application creates two directories inside the specified directory:

- `לפני_עיבוד_קובץ_<instrument>`: Contains the original files before processing.
- `לאחר_עיבוד_קובץ_<instrument>`: Contains the processed files.

### Processing Logic

#### PK Instrument

For the PK instrument, the application performs the following steps:

1. Reads all lines from the input file.
2. Organizes lines by `ALIQUOT` name.
3. Writes existing lines to the output file.
4. Adds missing required tests to the output file.

The required tests for the PK instrument are:

- Rh
- K
- Titer
- TPHA
- ABO GROUP

## Adding New Instruments

To add support for new instruments, modify the `ProcessFile` method to handle additional instrument names and implement the corresponding processing logic.

```csharp
static void ProcessFile(string instrumentName, string filePath, string processedDirectory)
{
    switch (instrumentName)
    {
        case "PK":
            PK_Processing(filePath, processedDirectory);
            break;
        // Add more cases for other instruments if needed
    }
}
```

Implement the specific processing logic in a new method similar to `PK_Processing`.

## License

This project is licensed under the MIT License.
```

This version of the README provides clear usage instructions, including how to run the application with command-line arguments, details on the directory structure, and guidelines for adding support for new instruments.
