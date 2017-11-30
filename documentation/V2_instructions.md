# Instructions for EML assembly line (version 2)

### Overview

The EML assembly line will help you create high quality metadata for your dataset. Below is a set of step-by-step instructions for making EML metadata for tabular data. The assembly line will soon be capable of handling other data types including: spatial vector, spatial raster, and images.

#### Installation

`EMLassemblyline v2.0` is not quite ready for prime time. Until then you will need to install from the development branch of this Github repository.

```
# Install and load devtools
install.packages("devtools")
library(devtools)

# Install and load EMLassemblyline from the development branch
install_github("EDIorg/EMLassemblyline", ref = "development")
library(EMLassemblyline)
```


### Step 1: Create a directory for your dataset

Create a new directory for your dataset. This is where the metadata parts created in the assembly line process will be stored and available for editing should you need to change the content.

Name this directory after your dataset. Replace spaces with underscores (e.g. `name of your directory` should be `name_of_your_directory`).

### Step 2: Move your dataset to the directory

Move the final versions of your data tables into this directory. These should be the final versions of the data you are ready to publish.

Rename these files following these rules:

* replace symbols with words
* replace parentheses with underscores
* replace periods with underscores
* replace blank spaces with underscores

e.g. `name.of.(your) d@t@.file` should be `name_of_your_data_file`


### Step 3: Select an intellectual rights license

We recommend two intellectual rights licenses:

1. __CC0__ the most accomodating of data reuse ... This data package is released to the “public domain” under Creative Commons CC0 1.0 “No Rights Reserved” (see: https://creativecommons.org/publicdomain/zero/1.0/). It is considered professional etiquette to provide attribution of the original work if this data package is shared in whole or by individual components. A generic citation is provided for this data package on the website https://portal.edirepository.org (herein “website”) in the summary metadata page. Communication (and collaboration) with the creators of this data package is recommended to prevent duplicate research or publication. This data package (and its components) is made available “as is” and with no warranty of accuracy or fitness for use. The creators of this data package and the website shall not be liable for any damages resulting from misinterpretation or misuse of the data package or its components. Periodic updates of this data package may be available from the website. Thank you.

2. __CCBY__ requires attribution ... This information is released under the Creative Commons license - Attribution - CC BY (https://creativecommons.org/licenses/by/4.0/). The consumer of these data ("Data User" herein) is required to cite it appropriately in any publication that results from its use. The Data User should realize that these data may be actively used by others for ongoing research and that coordination may be necessary to prevent duplicate publication. The Data User is urged to contact the authors of these data if any questions about methodology or results occur. Where appropriate, the Data User is encouraged to consider collaboration or co-authorship with the authors. The Data User should realize that misinterpretation of data may occur if used out of context of the original study. While substantial efforts are made to ensure the accuracy of data and associated documentation, complete accuracy of data sets cannot be guaranteed. All data are made available "as is." The Data User should be aware, however, that data are updated periodically and it is the responsibility of the Data User to check for new versions of the data. The data authors and the repository where these data were obtained shall not be liable for damages resulting from any use or misinterpretation of the data. Thank you.


### Step 4: Identfy the types of data in your dataset

Currently, the assembly line only works for tabular data and is the default option.

#### table

A flat file composed of columns containing variables and rows containing observations. Column names must follow these rules:

* replace symbols with words
* replace parentheses with underscores
* replace periods with underscores
* replace blank spaces with underscores

e.g. `land.cover.use (%)` should be `percent_land_cover_use`


### Step 5: Import the core metadata templates

Run the function `import_templates` in the RStudio Console window to populate the directory with metadata templates for you to complete. You will need to supply a few arguments to this function.

```
# First load the EMLassemblyline package
library(EMLassemblyline)

# View documentation on how to use the import_templates function
?import_templates

# Import templates for an example dataset licensed under CC0, with 2 tables.
import_templates(path = "/Users/csmith/Desktop/gleon_chloride",
                 license = "CC0",
                 data.files = c("lake_chloride_concentrations",
                                "lake_characteristics")
                 )
```

### Step 6: Script your workflow

Open __my_workflow.R__ in RStudio. This is a blank script for you to build an assembly line workflow, which can be revisited or modified for future assembly line runs.


### Step 7: Abstract

Open the file __abstract.txt__ and write an abstract for your dataset. The abstract should cover what, why, when, where, and how for your dataset. Write your abstract in plain text.

Do not use special characters, symbols, or formatting. Don't use hyperlinks (URLs are acceptable). The reason for this is that the EML schema only allows characters that are apart of the unicode character set. 

NOTE: You can create your abstract in Microsoft Word and then copy over to __abstract.txt__ but first you will need to remove any non-unicode characters. To do this go to [this web service](http://utils.paranoiaworks.org/diacriticsremover/) and paste your abstract into the window. Click the button "Remove Diacritics" to remove these non-compliant characters, then copy the resultant text into __abstract.txt__. You will want to give it one last look over after performing this operation to ensure no information has been lost.


### Step 8: Methods

Open the file __methods.txt__ and describe the methods for your dataset. Be specific, include instrument descriptions, or point to a protocol online. If this dataset is a synthesis of other datasets please specify dataset origins, preferably their DOI or URL plus general citation information. 

Do not use special characters, symbols, or formatting. Don't use hyperlinks (URLs are acceptable). The reason for this is that the EML schema only allows characters that are apart of the unicode character set. 

NOTE: You can create your methods in Microsoft Word and then copy over to __methods.txt__ but first you will need to remove any non-unicode characters. To do this go to [this web service](http://utils.paranoiaworks.org/diacriticsremover/) and paste your methods into the window. Click the button "Remove Diacritics" to remove these non-compliant characters, then copy the resultant text into __methods.txt__. You will want to give it one last look over after performing this operation to ensure no information has been lost.


### Step 9: Additional information

Do you have additional text based information that doesn't fall under the scope of the abstract or methods for your dataset (e.g. a list of research articles or theses derived from this dataset)? If so, then open __additional_info.txt__ in a text editor and add this information. You can delete this file if you won't be using it, or you can keep it around for later if you change your mind.

Do not use special characters, symbols, or formatting. Don't use hyperlinks (URLs are acceptable). The reason for this is that the EML schema only allows characters that are apart of the unicode character set. 

NOTE: You can create your additional information in Microsoft Word and then copy over to __additional_info.txt__ but first you will need to remove any non-unicode characters. To do this go to [this web service](http://utils.paranoiaworks.org/diacriticsremover/) and paste your additional information into the window. Click the button "Remove Diacritics" to remove these non-compliant characters, then copy the resultant text into __additional_info.txt__. You will want to give it one last look over after performing this operation to ensure no information has been lost.


### Step 10: Keywords

Open the tab delimited file __keywords.txt__ in a spreadsheet editor and list the keywords that best describe your dataset. DO NOT edit this file in a text editor. [Consult the LTER controlled vocabulary](http://vocab.lternet.edu/vocab/vocab/index.php) for keywords. In addition to keywords about the data include keywords that describe your lab, station, and project (e.g. OBFS, LTREB, etc.).

Definitions for columns of this file:

* **keyword** A keyword describing your dataset.
* **keywordThesaurus** A keywordThesaurus (i.e. a controlled vocabulary like the resource listed above) corresponding to the keyword listed in the keyword column. If the keyword is not from a thesaurus or controlled vocabulary, leave corresponding entry in the keywordThesaurus field blank.

### Step 11: Personnel

Open the tab delimited file __personnel.txt__ in a spreadsheet editor and enter information about the personnel associated with this dataset.

Definitions for columns of this file:

* **givenName** Given name of person (required).
* **surName** Surname of person (required).
* **organizationName** Name of organization the person is associated with (not required).
* **electronicMailAddress** Email address of person (not required unless a contact for your dataset).
* **userId** ORCID of person (not required). A valid entry for userId is the 16 digit number separated by dashes (i.e. XXXX-XXXX-XXXX-XXXX). An ORCID is like a social security number for scientists. [Create one here](https://orcid.org/).
* **role** Role of person with respect to this dataset.
        Valid entries for role are:
    + **creator** Dataset creator (required; at least 1 creator must be listed for your dataset).
    + **pi** Principal investigator associated with this dataset (required; at least 1 pi must be listed for your dataset).
    + **contact** Dataset contact (required; at least 1 contact must be listed for your dataset).
    + Any other entries into the 'role' column are acceptable and will be defined under the associated party element of this dataset with whatever value is entered under role.
    + If a person serves more than one role, duplicate this persons information in another row but with the additional role.
* **projectTitle** Title of the project this dataset was created under (optional). Project titles are only listed on lines where the personnel role is pi. If auxiliary projects were involved in creating this dataset then add a new line of personnel below the primary project and list the auxiliary project title and associated pi.
* **fundingAgency** Name of the entity funding the creation of this dataset (optional; but required if fundingNumber is present). Only include an entry in this column for rows where role pi.
* **fundingNumber** Number of the grant or award that supported creation of this dataset (opotional; but required if fundingAgency is present). Only include an entry in this column for rows where role pi.


### Step 12: Attributes
    
An __attributes_datatablename.txt__ file has been created for each of your data tables. Edit each of these tab delimited files in a spreadsheet editor. DO NOT edit this file in a text editor. You will see this file has been partially populated with information detected by the `import_templates` function. You will have to double check values listed in all the columns except __attributeName__. 

Instructions for completing the attribute table are as follows:

* **attributeName** Attribute name (column name) as it appears in the data table and in the same order.
* **attributeDefinition** Define the attribute. Be specific, it can be lengthy.
* **class** Specify the attribute class. This is the type of value stored under the attribute.     + **numeric** For numeric variables.
    + **categorical** For categorical variables.
    + **character** For variables containing text or symbols that are not categorical.
    + **Date** For date time data.
    + The list of valid options are case sensitive. If an attribute has class of `numeric` or `Date`, then all values of this attribute must be either numeric or date time. If any character strings are present in an otherwise `numeric` attribute, this attribute must be classified as `character`. Similarly if any values of a "Date" attribute do not match the date time format string (details below), then this attribute must be classified as `character`.

* **unit** If an attributes class is numeric, then you must provide units. If the attribute is numeric but does not have units, enter `dimensionless`. If the attribute class is categorical, character, or Date then leave the unit field blank. If the attribute is numeric and has units search the standard unit dictionary for the unit of interest and enter the unit `name` as it appears in the dictionary (unit names are case sensitive). Open the dictionary by running these lines of code in the RStudio console window:

```
# Import the standard units list
standardUnits <- get_unitList()

# View and search the standard units
View(standardUnits$Units)

```
* If you cannot find a unit in the dictionary, create one and add it to __custom_units.txt__. Open this tab delimited file in a spreadsheet editor. DO NOT edit this file in a text editor. If you have no custom units to report then delete this file. Valid custom units must be convertible to SI Units (i.e. International System of Units). If it cannot be converted to SI then list it in the attribute defintion and enter "dimensionless" in the unit field. To create a custom unit define the:
    + **id** This is equivalent to the unit name. Reference the standard unit dictionary formatting.
    + **unitType** The type of unit being defined. Reference the dictionary for examples.
    + **parentSI** The SI equivalent of the id you have entered.
    + **multiplierToSI** This is the multiplier to convert from your custom unit to the SI unit equivalent.
    + **description** A description of the custom unit. Reference the dictionary for examples.
    
* **dateTimeFormatString** Enter the date time format string for each attribute of "Date" class. Remember, a class of "Date" specifies the attribute as a date, time, or datetime. Enter the format string in this field. If the attribute class is not "Date", leave this field blank. Below are rules for constructing format strings. Additional information is listed under "dateTime-eml-attribute" of the current [EML specification](https://knb.ecoinformatics.org/#external//emlparser/docs/index.html). Valid date time formats are a combination of date, time, and time zone strings. Below are a set of best practice recomendations that we strongly encourage you to follow, but are by no means the full list of currently acceptable format strings.
    + **Date format strings:** YYYY-MM-DD, YYYY, YYYYMMDD, YYYY-MM, YYYYMM, YYYY-DDD, YYYYDDD; where YYYY is year, MM is month, DD is day of month, and DDD is day of year.
    + **Time format strings:** hh:mm:ss.sss, hhmmss.sss, hh:mm:ss, hhmmss, hh:mm, hhmm, hh; where hh is hour (in 24 hr clock), mm is minute, ss is second, and ss.sss is decimal second.
    + **Time zone format strings:** Z, +hh:mm, +hhmm, +hh, -hh:mm, -hhmm, -hh; where Z (capitalized) is Coordinated Universal Time, and + and - denote times ahead and behind UTC respectively.
If reporting a date without time, select one of the date format strings. If reporting a date and time, select one date and one time format string and combine with a single space (e.g. YYYY-MM-DD hh:mm) or with a "T" (e.g. YYYY-MM-DDThh:mm). If reporting a date and time, it is recommended that a time zone specifier be appended without a space (e.g. YYYY-MM-DD hh:mm-hh:mm, or YYYY-MM-DDThh:mm-hh:mm).
* **missingValueCode** If a code for 'no data' is used, specify it here (e.g. NA, -99999).
* **missingValueCodeExplanation** Define the missing value code here.
    
    
### Step 13: Configuration    

Open __configuration.R__ in RStudio and supply additional parameters to functions used in the assembly line. Detailed instructions are listed in this file.
    
### Step 14: Close files

Make sure all files of your dataset directory are closed. Some functions will error out if these files are open.

### Step 15: Categorical variables

If your data tables contain any attributes with the categorical class, you will need to supply definitions for the categorical codes. Use the function `define_catvars` to do this. `define_catvars` searches through each attribute file looking for attributes with a categorical class. If found, the function extracts unique categorical codes for each attribute and writes them to a file for you to define.

```
# View documentation for this function
?define_catvars

# Run this function for your dataset
define_catvars(path = "/Users/csmith/Desktop/gleon_chloride")

```

A tab delimited __catvars_datatablename.txt__ will be created for each of your data tables containing categorical variables. Open these in a spreadsheet editor and add definitions for each code.

### Step 16: Geographic coverage

If your dataset contains more than one sampling location, then you will want to add this information to your metadata. As of now the assembly line only supports point locations, multiple areas are not yet supported. Often a data user will search for data withing a geographic area.

Run the function `extract_geocoverage` to get the unique latitude, longitude, and site name combinations from your data and write to file. `extract_geocoverage` requires specific inputs that may require altering the latitude and longitude formate of your data. See documenation for details.

```
# View documentation for this function
?extract_geocoverage

# Run this function for your dataset
extract_geocoverage(path = "/Users/csmith/Desktop/gleon_chloride",
                    data.file = "lake_characteristics.csv",
                    lat.col = "lake_latitude",
                    lon.col = "lake_longitude",
                    site.col = "lake_name")
```
This function outputs a tab delimited file named __geographic_coverage.txt__ to your dataset directory. You may edit this in a spreadsheet editor if you'd like, but if the data table this information has been extracted from is accurate, then there is no need for editing.

### Step 17: Make EML
    
Now you are ready to synthesize your completed metadata templates into EML. This step is relatively simple. The `make_eml` function requires only one argument, the path to the dataset working directory.

```
# View documentation for this function
?make_eml

# Make EML for your dataset
make_eml(path = "/Users/csmith/Desktop/gleon_chloride")

```
If your EML is valid you will receive the message: **EML passed validation!**. If validation fails, open the EML file in an XML editor and look for the invalid section. Often a minor tweak to the EML can be made manually to bring it into compliance with the EML schema.


### Step 18: Upload your data package to the EDI repository

Your data and metadata form a package that may be uploaded to the [EDI data repository](https://portal.edirepository.org/nis/home.jsp). [Follow these instructions](https://environmentaldatainitiative.org/resources/assemble-data-and-metadata/step-4-submit-your-data-package/) to upload your data package.

