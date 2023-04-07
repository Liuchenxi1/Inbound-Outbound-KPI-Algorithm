# Outbound-KPI-Algorithm 📋✍🏻

This algorithm primarily focuses on Python. There are several issues that need to be addressed : 

1. The system assigns different timestamps to files with the same name, depending on the download time. For example: 202304060821_ Quality TS - Qualit, 2023-04-08-08:21. This KPI report requires 6 different reports from the system service. Modifying or deleting the file name manually would require significant effort.  This will be the initial step in loading the large datasets.

2. All 6 raw datasets contain timestamps that vary based on the date. The most challenging part is line 7, where a date and time range needs to be determined based on today's date. Specifically, if today is Monday, the date and time range should not include the weekend. However, if today is Tuesday, the date and time range should include the weekend. For the rest of the weekdays, the date and time range should account for the previous two days. To achieve this, the datetime and timedelta packages were utilized. Three different target dates were set, with a target time of 14:00:00, and these were applied within a loop to calculate the appropriate date and time range.

3. Another big challenge is encountered in line 23, where the reports are timestamped with UK/London time, which does not align with the local time in Nashville, TN. To resolve this, the timestamps are converted to UTC time, then to EU/LDN time, and finally to Chicago time. Additionally, within the small loop, if today is Monday, the time range is set to three days, including the weekend, while for other days, it only includes counts from yesterday.

4. The remaining steps involve regular filtering and selecting columns/values from different datasets. Since the datasets have different columns and timestamp requirements, and the size of the datasets is large, merging them is not necessary. To avoid potential mistakes, a simpler approach based on mathematical operations was chosen, while ensuring that all values extracted from the raw data are accurate and error-free. 😎
