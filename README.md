# SQLite_Lego_data

Exploration of three Lego datasets from rebrickable.com using SQLite

Run by using

    $ sqlite3 Q2.db < Q2.SQL.txt > Q2.OUT.txt 
    
in command prompt to get a database and outputfile.

a.i Create three tables named:

    sets 
    themes
    parts

with columns having the indicated data types:

    sets

    set_num (text)
    name (text)
    year (integer)
    theme_id (integer)
    num_parts (integer)

    themes

    id (integer)
    name (text)
    parent_id (integer)

    parts

    part_num (text)
    name (text)
    part_cat_id (integer)
    part_material_id (integer)

a.ii Import the provided files as follows:

     sets.csv file into the sets table
     themes.csv file into the themes table
     parts.csv file into the parts table 

b.  Create the following indexes for the tables specified below. This step increases the speed of subsequent operations

    sets_index for the set_num column in sets table
    parts_index for the part_num column in parts table
    themes_index for the id column in themes table

LEGO sets belong to either a top level theme, e.g.,  ‘Castle’, ‘Town’, ‘Space’ or a theme → sub-theme hierarchy, e.g.,Town → Classic Town, Town → Outback, Town → Race.  

c.i Create a view (virtual table) called top_level_themes that contains only the top level themes. This view contains the id and name of any theme in the themes table that does not have a parent theme.          

c.ii Query that shows the total number of top level themes as count in the view.      

d. Find top 10 level themes with the most sets using the top_level_themes view. Sorting output in descending order from highest to lowest.      

e. Query that expresses the number of sets from above as a percentage of the total number of sets that belong only to top level themes, limiting the output only to themes with a percentage >= 5.00.  Format all decimal values to 2 decimal places.

f. As LEGO released more sets, some themes were subdivided into sub-themes.  List each sub-theme and its total number of sets for the ‘Castle’ theme Sort the output by number of sets highest to lowest, then alphabetically.  

Look at cumulative number of LEGO sets that have been released over time.  

g.i. First, create a new view called sets_years that contains the ROWID, year, and number of sets (sets_count) released each year.

g.ii. Second, using the view sets_years,find the cumulative number of sets for each year.  

SQLite supports simple but powerful Full Text Search (FTS) for fast text-based querying (FTS documentation). Import lego data from the parts.csv  into a new FTS table called parts_fts with the schema: 

    parts_fts(part_num (text),
    name (text),
    part_cat_id (integer),
    part_material_id (integer))


h.i Count the number of unique parts as “count_overview” whose name field begins with the prefix ‘mini’.  A unique part is identified by a unique part_num. Matches are not case sensitive.  

h.ii List the part_num’s of the unique parts as “part_num_boy_minidoll” that contain the terms ‘minidoll’ and ‘boy’ in the name field with no more than 5 intervening terms. Matches are not case sensitive.  Here, match full words, not word parts/sub-strings. 

h.ii List the part_num’s of the unique parts as “part_num_girl_minidoll” that contain the terms ‘minidoll’ and ‘girl’ in the name field with no more than 5 intervening terms. Matches are not case sensitive.  Here, match full words, not word parts/sub-strings .
