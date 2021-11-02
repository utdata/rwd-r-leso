---
output:
  html_document:
    df_print: paged
knit: (function(inputFile, encoding) { rmarkdown::render(
    inputFile,
    encoding = encoding,
    output_dir = "docs",
    output_file='index.html'
  ) })
---

# Defence Logistics Agency's LESO program,

The Defense Logistics Agency handles transfers of military surplus equipment to local law enforcement through the Law Enforcement Support Office (LESO) or [LESO Program](https://www.dla.mil/DispositionServices/Offers/Reutilization/LawEnforcement/).

The data is updated quarterly and available for download on their [LESO Public Information page](https://www.dla.mil/DispositionServices/Offers/Reutilization/LawEnforcement/PublicInformation/).

## Notebooks

- [import-clean](https://utdata.github.io/rwd-r-leso/01-import-clean.html) which loops through sheets in an Excel file.


