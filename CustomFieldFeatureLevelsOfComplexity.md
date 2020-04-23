# Custom Field Feature - Levels of complexity

## Option 1: We define the config
ZPV1|name+surname+title|||



## Option 2: They input xml based on extension

1. Input and save config  
  * Validation on save
     * Basic structure
     * Compulsory parameters (like url)
     * Correctly formatted placeholders
     * Correctly structured extensions
2. Replace place holders with data
  * Find place holders in config
  * Tokenise custom field and map to place placeholders
  * Replace placeholders in config string
  * Validation
    * If cannot match. Remove extension from DOM.
      * Problem: There will be separate extension with the label which will still be there. This will require extra work to identify. Messy.
3. Parse into extension objects

4. Add extensions to resource
