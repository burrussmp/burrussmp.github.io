# Developer Notes
## How to update resume
1. Create the pdf
2. Upload to google drive
3. In resume.html (in include) change the id of the url to point to the id of the file
## How to make a new page
1. Create a folder '_newpage'
2. Update navigate.xml
3. update config.xml with collection and the new page
4. update _docs_/_pages to include the base new page
5. Place new elements in the '_newpage' folder and specify the types as the 'newpage'

## How to upload a new article to blog
1. Place a new '*.md' in the '_blog' folder and name it type 'blog'
2. Look at others for examples of how to properly place categories, etc.
3. Make sure to add the post to _docs/_posts with YEAR-MONTH-DATE-Format... you can simply link to the other article.
4. That is, copy the YAML stuff and in the name link to /blog/PATHTOFILE

## How to make a new category
1. Add a new page to "_docs/_pages" with name "cat_newcategory.md"
2. Add the correct taxonomy and permalink
3. On the new posts, add the category to the table below!

| Category                |       Permalink      |
|-------------------------|:--------------------:|
| Machine Learning        |       /categories/ml |
| Artificial Intelligence |       /categories/ai |
| Augmented Reality       |       /categories/ar |
| Statistics              |    /categories/stats |
| Computer Vision         |       /categories/cv |
| Data Visualization      |  /categories/datavis |
| Opinion                 | /categories/opinions |
| Other                   | /categories/other |

## How to update resume

1. Go to vanderbilt google drive
2. Go to resume folder
3. Replace "Burruss Resume.pdf"
4. profit