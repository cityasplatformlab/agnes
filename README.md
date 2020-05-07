# notes on SP widget for Agnes

**User**

Agnes, 79, lives alone, no smart phone, no PC / internet at home. Is coded as an at-risk individual.

**Intention**

Would like to know if there's an ACTIVE covid-19 outbreak at her friend Doris' retirement home i.e. Chester Village.


**Open Dataset**: [Outbreaks in Toronto Healthcare Institutions 2020](https://open.toronto.ca/dataset/outbreaks-in-toronto-healthcare-institutions/)

--------------------------------------------------

### Endpoints

> After browsing through OpenData Toronto's CKAN API.


**Entire package list:**

https://ckan0.cf.opendata.inter.prod-toronto.ca/api/3/action/package_list

**For the "package" that holds desired dataset:**

https://ckan0.cf.opendata.inter.prod-toronto.ca/api/3/action/package_show?id=outbreaks-in-toronto-healthcare-institutions

------------------------------

### `PROBLEMATIC DATA DESIGN?`

- No endpoints to access the parameters / data fields of the 2020 dataset from within this package, i.e. the data fields within the Excel file themselves are not accessible through API calls (which is also probably why we aren't able to preview the data right within the website)
- The data seems to have been hardcoded into an Excel file that gets updated and re-uploaded. So the max you can get to with API call is the URL to download the Excel file.

------------------------------

### Signal

  **Excel file URL:**

  http://opendata.toronto.ca/toronto.public.health/outbreaks-in-toronto-healthcare-institutions/ob_report_2020.xls

  Now, in this Excel sheet, we're looking for:

 - __Institution Name__ to match _Chester Village_
 - __Active__ to match _"Y" or "N"_
 - If answer is _"N"_ --> let Agnes know if and when the outbreak had ended i.e. match to __Date Declared Over__

------------------------------

### `QUESTION RE: AFFORDANCES`

**Is it even possible to access data from Excel file / URL using SignalPattern?
If yes, how? If not, what would be the workaround?** <br>

Esp. since this spreadsheet is not natively built on a platform like Airtable. We are going to run into scenarios like these very often with local data. <br>

> Need to check in with Peter about this functionality.

------------------------------

**Current workaround for demo:**

- Make own API from the spreadsheet ✅ --> https://sheetlabs.com/CAPL/outbreaks2020
- Design queries on SignalPattern ✅ --> [Active Outbreak](https://www.signalpattern.com/patterns/nravella/3SNS0CVv!result) + [Start / End Date of Outbreak](https://www.signalpattern.com/patterns/nravella/3SNS0CVv!result_info)
- Use JSONata for parsing queries ✅
- Test with SMS ✅

![SMS Test Screenshot](https://pasteboard.co/J7hjhI0Q.jpg)
