# vibe-getCalendarCounts


<b>Authors</b>: 
Tyler Harris, Shane Nielson
<br><b>Purpose</b>: 
Get events & attendees counts from a Vibe calendar for a specific date range
<br><b>Assumptions</b>: attendee teams & groups will be ignored in counts
<br><b>Execute from Linux</b>:
```mysql -u<user> -p -t < getCalendarCountsFromVibe.sql > getCalendarCountsFromVibe.txt```
<br><i>Note: Report output can be found in getCalendarCountsFromVibe.txt after running the above command.</i>

Example report:
- 1st table: Get total count of events
- 2nd table: List of events and a count of their attendees
- 3rd table: Get total count of attendees
```
+--------------------+
| TotalCountOfEvents |
+--------------------+
|                  2 |
+--------------------+
+------------------+----------------+---------------------+---------------------+---------------------------------------------------------+---------------------+----------+------------------+
| title            | attendee_count | dtStart             | dtEnd               | description_text                                        | creation_date       | name     | stringValue      |
+------------------+----------------+---------------------+---------------------+---------------------------------------------------------+---------------------+----------+------------------+
| new appointment  |              3 | 2016-05-12 20:30:00 | 2016-05-12 21:00:00 | <p>test</p>                                             | 2016-05-05 20:30:49 | attendee | 22,1,29          |
| meet with batman |              6 | 2016-05-11 15:51:00 | 2016-05-11 16:21:00 | <p>Batman is going to take us out in the batmobile!</p> | 2016-05-06 15:52:49 | attendee | 22,88,1,89,29,87 |
+------------------+----------------+---------------------+---------------------+---------------------------------------------------------+---------------------+----------+------------------+
+-----------+-----------+--------------------+
| StartDate | EndDate   | TotalAttendeeCount |
+-----------+-----------+--------------------+
| 2016-05-% | 2016-05-% |                  9 |
+-----------+-----------+--------------------+
```

Configuring variables can be found at the top of the script:
```
-- Note: Only change year and month for startDate and endDate. Day value needs to be % since query uses LIKE.
SET @lv_input_startDate := '2016-05-%'; 
SET @lv_input_endDate := '2016-05-%';
SET @lv_input_calendarPathName := '/Novell Workspaces/Team Workspaces/Services/Global Technical Support/Technical Training Resources/Calendar';
```
