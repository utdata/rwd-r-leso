# Defence Logistics Agency's LESO program

The Defense Logistics Agency handles transfers of military surplus equipment to local law enforcement through the Law Enforcement Support Office (LESO) or [LESO Program](https://www.dla.mil/DispositionServices/Offers/Reutilization/LawEnforcement/).

The data is updated quarterly and available for download on their [LESO Public Information page](https://www.dla.mil/DispositionServices/Offers/Reutilization/LawEnforcement/PublicInformation/).

## Research about the data

### Shipment values

In 2020 I asked the LESO office about the `acquisition_value` measure and found that it should be *multiplied* by the `quantity`. The value is for single item.

In addition, I asked about why there are different prices for the same item, and received the following response on 2020-12-14:

> You are correct, the NSN is the National Stock Number. The primary reason a similar item has a different NSN designation is classification difference.  In some cases, this could be difference in features, a frequently added component to the item, or variance in storage requirements such as the recent vaccinees that are being assigned NSNs for DLA’s major subordinate command, Troop Support.The cost information is provided by the customer when they turn the items into DLA Disposition Services. Acquisition values can vary for numerous reasons. One is the above, variance in classification differences such as modifications. As with most commodities, other factors could include variance in acquisition cost depending on the quantity procured and the year acquired.

### Controlled vs non-controlled

The most recent year includes "non-controlled" items like blankets and boots, which are removed after a year. This inflates counts for the most recent year of data. During research in June 2022, I learned a number of things about this.

- non-controlled items are classified with a DEMIL CODE of "A" or the combination of DEMIL CODE "Q" and DEMIL IC of "6".
- Some non-controlled items, like aircraft or items of high value, remain on the property list.
- There are also errors in the coding the item "RECON SCOUT XT,SPEC". That will need to be fixed in 22Q2 data, but the DLA said it will be fixed in the future.

Here is my correspondence:

Question: Is there a way to tell from the data itself if the item is a controlled vs non-controlled item? I thought perhaps the DEMIL IC field with value of "A" might be non-controlled, but there seem to be items older than a year with that categorization that could be controlled and accurately remain, like RECON SCOUT XT,SPEC and AIRPLANE,CARGO-TRANSPORT.

> Property with the DEMIL codes A and Q6 are considered non-controlled general property and fall off the LESO property books after one year. All other Demil codes are considered controlled items and stay on the LESO property book until returned to DLA for disposition/disposal.

Followup question: When you say Q6, do you mean a demil_code of "Q" combined with demil_ic of "6". Would other property with demil_code "Q" but with a demil_ic of other numbers not be controlled? Second question: In the 22Q2 data, there are a number of items older than a year (n = 62) that are DEMIL CODE A and DEMIL IC 1 and they do seem like big items that might be "controlled". Some examples: RECON SCOUT XT,SPEC (ALABAMA LAW ENFORCEMENT AGENCY, 2016-08-25) and AIRPLANE,CARGO-TRANSPORT (ARIZONA DEPT OF PUBLIC SAFETY, 2015-12-03, $17,000,000). I could see the argument for them to be controlled (though SEAT,AIRCRAFT might be a maybe on that).

> The general rule is that property coded A and Q6 (6 being the integrity code) falls off the LESO property book after one year. However, there are some exceptions. For instance, aircraft are always controlled regardless of the demil code. Also, LESO has the discretion to keep items as controlled despite the demil code. This happens with some high value items. The RECON SCOUT XT, SPEC example you cited was actually initially coded incorrectly because the wrong NSN was used when it was coded as A. Once the correct NSN was verified with the manufacturer, is was renamed and recoded as D. The next quarterly report will reflect the new name and code.

Followup: Any chance there is a standard minimum value that represents "high value items" that you keep on the property book? 

> No, there isn’t a standard minimum value. It also may also depend on the type of property.

## Related data

- Two values are considered [Demil Codes](https://www.dla.mil/HQ/LogisticsOperations/Services/FIC/DEMILCoding/DEMILCodes/) which note how an item must be tracked or destroyed?
- There is also the `NSN` value, or [National Stock Number](https://www.dla.mil/AboutDLA/News/NewsArticleView/Article/1933320/what-is-a-national-stock-number/).
  - I downloaded a [version of NSN](https://catalog.data.gov/dataset/national-stock-number-extract) in June 2022, saved as `data-raw/nsn-extract-3-17-21.xlsx`. It doesn't have many matches.
  - [Breaks down](https://www.dla.mil/AboutDLA/News/NewsArticleView/Article/1675036/dla-uses-national-stock-numbers-to-manage-supplies-efficiently-throughout-their/) NSN values.
  
## Local agencies

See the analysis notebook for a list.

## Notebooks

- [Clean](01-cleaning.qmd) which loops through sheets in an Excel file.
- [Analysis](02-analysis.qmd) looks at some of the data and checks local agencies..


