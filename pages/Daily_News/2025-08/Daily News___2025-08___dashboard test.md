  - ## Fox News Bulletin Board
    ```dataview
    TABLE l.link AS Segment, l.location AS Location, l.subject AS Subject, l.type AS Type, l.text AS Story
    FROM "Daily News"
    FLATTEN file.lists as l
    WHERE l.annotated
    AND contains(l.publication, "Fox News")
    SORT file.ctime desc
    LIMIT 10
    ```
    
    %%DATAVIEW_PUBLISHER: start
    ```dataview
    TABLE length(rows) AS Count
    FROM "Daily News"
    FLATTEN file.lists as l 
    WHERE l.annotated
    GROUP BY l.publication AS Publication
    SORT length(rows) DESC
    ```
    %%
    %% DATAVIEW_PUBLISHER: end %%
    
    #