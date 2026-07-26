# HCM Extract Types

| Serial No | Extract Type          | Changes Only | LDG Mandatory | Consumer | Additional Details  |
|-----------|-----------------------|--------------|---------------|----------|---------------------|
| 1         | Full Profile          | No Option    | N             | Y        | Only when undefined |
| 2         | HR Archive            | Optional     | N             | Y        | Only when undefined |
| 3         | Archive Retrieval     | Optional     | Y             | N        | Not Applicable      |
| 4         | Benefit Carrier       | Optional     | N             | Y        | Only when undefined |
| 5         | Payroll Interface     | Optional     | Y             | Y        | Only when undefined |
| 6         | Large Object          | No Option    | N             | Y        | Only when undefined |
| 7         | Recruiting Archive    | Optional     | N             | Y        | Only when undefined |
| 8         | Other Payroll Archive | Optional     | Y             | Y        | Only when undefined |

## Full Profile

This will not allow it to be a changes only extract.

## HR Archive

This can be a Changes Only extract.

## Archive Retrieval

This can be a Changes Only extract. In this type of extract LDG is Mandatory as it specifically designed to query and report on permanently Archived Payroll and local legislative Data.

## Benefit Carrier
This can be a Changes Only extract.

## Payroll Interface

This can be a Changes Only extract. In this type of extract LDG is Mandatory as it specifically designed to query and report on Payroll Data.

## Large Object

This will not allow it to be a changes only extract.

## Recruiting Archive
This can be a Changes Only extract.

## Other Payroll Archive
This can be a Changes Only extract. In this type of extract LDG is Mandatory as it specifically designed to query and report on Payroll Data.

## General Information:

Changes Only Parameter can only be set at the time of creation of an extract. It can't be changed from Extract Definition Page. Once an extract is set to Yes for Changes Only, It adds two Additonal Parameter alongwith Effective Date parameter(Default). Those Two Parameters are:
  1. Baseline Only -> Here you can select Yes/No. - For First time Run or Generating Baseline for that extract.
  2. Changes Only -> Here You can Set values defined within PER_EXT_CHANGES_ONLY Lookup.
     - All Attributes (N)
     - Changes Attributes (Y)
     - Changed and Marked Attributes (ATTRIBUTE)
     - Changed and Marked Attributes with Previous Values (ATTRIB_OLD)
     - Changed, Marked Attributes under threading Group (BLOCK)
     - Changed, Marked Attributes, Previous Values under threading Group (BLOCK_OLD)

| MODE          | LookupValue                                                     | Description                                                                                                                                                                                                                                                                                                 |
|---------------|-----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| N             | All attributes                                                  | If you run the extract with "Changes only" set to N, it is a Full Extract.                                                                                                                                                                                                                                  |
| Y             | Changed Attributes                                              | If you run the extract with "Changes only" set to Y, all data that has changed since the previous run will be extracted. In this case, if a single attribute has changed, all attributes across all data groups in the threaded database item will be extracted, even if other attributes remain unchanged. |
| ATTRIBUTE     | Changed and marked attributes                                   | If you run the extract with "Changes only" set to ATTRIBUTE, it will return only the changes from the previous run, extracting only the attributes that have been changed or those that are marked as "changed" or "always display" in the configuration.                                                   |
| ATTRIBUTE_OLD | Changed and marked attributes with Previous Values              | Display the attributes that have changed, or are configured as marked "changed" or "always display," along with their previous values.                                                                                                                                                                      |
| BLOCK         | Changed marked attributes under threading group                 | Display the attributes that have changed, or are configured as marked "changed" or "always display," and also extract all attributes under the threaded DBI.                                                                                                                                                |
| BLOCK_OLD     | Changed, marked attributes, previous data under threading group | Display the attributes that have changed, or are configured as marked "changed" or "always display," and also extract all attributes under the threaded DBI.                                                                                                                                                |

BLOCK and BLOCK_OLD is applicable for those extracts which are having Hierarchical structure of Data Groups.

## Effective Date Defaulting Rule
  1. Open the extract for which you want to specify the Effective Date parameter.
  2. In the Define tab, go to the Parameters region and select Advanced View from the Show list.
  3. Select the value from the Parameter Basis list.
  4. Click Save and Close.

## Enabling Advanced Edit Option

Need to add Lookup Entry with Lookup Code as *EXT_PUI_ENABLE* and Meaning as *YES* within seeded Lookup *ORA_PER_EXT_CONFIG*

