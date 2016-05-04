# MetaDB User Manual (draft) #

<u><b><i>Project Summary and Brief History</i></b></u>

MetaDB is a distributed metadata collection tool developed by Lafayette College Libraries. It allows institutions to use a web-based interface to split digital collection building tasks among several people.

For example, at Lafayette, a librarian creates new projects, defines metadata requirements, supplies data for administrative fields, and imports high-resolution master TIF images into the system. Subject specialists then access the system remotely and enter descriptive data about each item. Once all metadata has been collected, projects are exported as CSV or tab-delimited data files that are easily ingested into most repository systems.

MetaDB supports several features that strengthen digital collection building efforts, including the use of controlled vocabularies, the ability to search, browse, sort, and edit records in different ways, and support for concurrent access by multiple users. The application extracts technical metadata from images, and automatically creates JPG access derivatives that can include branded or banded text, as well as zoomable high-resolution images for close study.

MetaDB version 3 was developed by Eric Luhrs, Digital Initiatives Librarian at Lafayette College, and Computer Science students Long Ho ’10 and Haruki Yamaguchi ’11.

**This document assumes that you are logging in under administrative access to a properly configured and working MetaDB deployment. This document will go through each feature of the MetaDB user interface and try to explain it as best as possible.**

## Main Screen ##

The main menu, as seen, should be pretty straightforward to understand. There is a user name and password section that you must fill out correctly. Once you log in you will be able to access the administrative menus along the top bar.

## User Management ##

<u><b><i>Create User</i></b></u>

This is the user management page. You may create new users and delete them at any time.

_Username_ is a string of any length containing the username. Try not to use special symbols, as they may be problematic when doing internal processing.

_User Type_ is the main level of privileges the user will be granted.

"Administrators" (admin) can access all of MetaDB's systems and automatically have access to all projects. "Workers" (worker) can only access specific portions of MetaDB's systems that are specified by administrators, and can be assigned one or more projects. Administrators cannot be deleted (a manual removal is necessary).

_Password_ and _Confirm Password_ are the password for this new user. It can be changed later if desired.

<u><b><i>Delete User</i></b></u>

You may delete any of the "worker" privilege users in this menu. Once you hit “confirm”, the user will be erased from the MetaDB database along with any associated permissions.

<u><b><i>User Settings</i></b></u>

This is where users can be granted and revoked access to projects, as well as changing their settings such as user type and password.

To give a user access to a project, select the user from the drop down menu, choose the project from the “Project” column, enter the permission settings and click “Grant”. The next time the user logs in, they should be given the appropriate access.

## Project Management ##

<u><b><i>Create Project</i></b></u>

This is where you can create new projects.

_Project Name_ is the name for the project. Try not to use capital letters, special symbols or spaces to prevent possible internal problems.

_Department abbreviation_ is a convenience field that can be used as internal identifiers. This field does not directly affect MetaDB's operation.

<u><b><i>Delete Project</i></b></u>

This page allows you to delete existing projects.

"Delete all data and images" will delete all metadata, as well as all derivative images created from that project. It will also erase any user permissions tied to that project. Before carrying out this operation, ensure that you make back ups.

"Delete administrative/descriptive data only" will only clear out the administrative and descriptive metadata and leave all technical fields, derivative images, as well as user permissions intact.

"Delete technical data and images only" will clear out the technical data and all derivative images but leave administrative/descriptive data, as well as user permissions, intact. To repopulate technical data and derivative images, the collection will need to be re-processed by MetaDB.

<u><b><i>Edit Project</i></b></u>

Here, you may customize the current project’s metadata fields. There are two types of editable metadata: administrative metadata, and descriptive metadata. For our intentions regarding the usage of two different types of metadata, consult the Project Overview document.

Administrative and Descriptive Metadata are in essence two derivations of the same thing, except that since they have separate access rights, it is possible for a user to have access to one but not the other. Still, in terms of field management, they are identical.

_Adding fields_

Under each heading (“Administrative Metadata” and “Descriptive Metadata”), you will see a list of current fields and a blank row for adding new fields.

One new field has already been provided, but more fields may be added with the "+" button. The "Add multiple fields" text box at the bottom may be used to add multiple fields at once.

Upon adding a new field(s), there are some settings that must be chosen via the check boxes:

  * Search Date: If you would like the field to contain searchable date information, check this option. Note that all data in this field must be valid dates.

  * Display Date: If you would like the field to contain human-readable (display) date information, check this option.

  * Large Text Field: If you would like the editing window for the field to be a text box rather than a one line editor, check this box. An example of using this may be to provide a descriptive paragraph.

  * Controlled Vocabulary: For detailed information about Controlled Vocabulary, see the Controlled Vocabulary section. Selecting this box will bring up a sub-window which will allow you to choose from an existing vocabulary, upload a new one or manually add a new list.

  * Allow Multiple Terms: If this option is checked, users may enter more than one term contained in the vocabulary when inputting metadata.

  * Allow New Terms: If this option is checked, users may add new terms to the vocabulary as they input data; that is, it will be possible to attain suggestions from the vocabulary list, but it will also be possible to modify the vocabulary list on the fly.
  * **Note: If a field is not controlled, neither “allow multiple terms” nor “allow new terms” will be available.**

Once you are done with the settings, hit “Update” and your changes should be reflected.

_Removing fields_

Remove fields by clicking the “-“ to the right of the field. Removing the field will mean that **all data contained in this field for all items in the project will be lost.**

<u><b><i>Derivative Settings</i></b></u>

This is where derivative generation, as well as manual processing of new items in a project, takes place.

_Enabling/Disabling_

By default, thumbnails and "zoom" JPEGs are automatically generated and you cannot disable these. You may disable the “custom" and "full size” settings, meaning these images will not be generated.

_Size_

You can enter a maximum size, in terms of maximum width and maximum length, for the derivative setting. MetaDB will automatically calculate the appropriate scale factor for you, so there’s no need to specify the size exactly. This serves as a threshold; no dimension of the resulting derivative can exceed this value.

_Brand_

The “brand” setting controls text annotation for "custom" and "fullsize" derivatives.

  * "None" means that the image is left untouched and no text will be generated.

  * "Under" means that annotation text will be added to the bottom of the scaled image, resulting in extra image height. Note that the “under” option will not overwrite any portion of the original image; it simply appends a rectangular band containing the annotation text below the image.

  * "Over" means that the annotation text will be watermarked onto the image. The watermark is transparent and meant to be unobtrusive.

_Text Color_

This is the color of the text you want to use in annotations.

_Background Color ("under" only)_

This is the color of the rectangular band itself when using the “under” option.

_Preview_ shows you the colors as they would appear when using the “under” option.

_Branding Text_

This large text box contains your annotation text for the images. Please note that due to current functionality limitations, the “over” setting cannot fit lengthy text properly; when using the “over” setting and you need the full annotation to be visible, ensure that your annotation text is of the appropriate length and format; i.e using line breaks when necessary as well as keeping the amount of text as low as possible.

_Processing Images_

For detailed information on how MetaDB works with processing your master files, consult the Appendix.

The “Save” button will save your current derivative settings.

The “Submit” button will process your master files according to one of three settings (note that sequencing matters—if there is an incorrect item sequence, MetaDB will stop processing):

  * All: MetaDB will process all of the master files it can find.
  * These: You can enter comma-delimited numbers and number ranges (for ex, to process items 1, 2-5, and 8, you would enter “1, 2-5, 8”) , which are the item numbers of the master files you want to process.

## Controlled Vocabulary ##

Controlled vocabulary is used to limit the data that users can input when editing metadata. Controlled vocabulary is global to all projects and can be tied to individual fields. A controlled vocabulary consists of a newline-delimited list of words or phrases that can be used throughout MetaDB. They can be edited at any time through the “Edit Project” or the “Controlled Vocabulary” sections in Project Management.

The proper use of controlled vocabulary can be extremely useful when handling data that contains multiple references to the same thing. For example, if you have a project that refers repeatedly to the name “Marquis de Lafayette”, you can specify a vocabulary that contains this string, but allow the user to use additional names if necessary through the “Allow New Terms” setting.

## Data Management ##

_View Metadata_

This option allows you to view all of the metadata in a project in a convenient, Excel-like table. You can select the attributes from the list, and click "View Table." You will see a table containing all of the attributes you selected for each record in the selected project. You can also edit the metadata directly on the page by clicking the text--an input box should appear. (Note: Some of the metadata is not editable, namely the technical attributes.)

_Import Metadata_

On this screen you may import T/CSV files into MetaDB’s database.

To choose the project you would like to import data into, choose it from the upper right hand menu.

The “Dataset” option currently only has administrative/descriptive data and may be changed in future versions. The “Choose delimiter” specifies the type of import; that is, CSV or TSV.

The “Browse” box lets you choose a T/CSV file from the computer you are using (or over the network), which will actually be imported.

The “Import” button will commit the import. MetaDB will process the CSV/TSV file and the data will be put into the project you select. Go to the metadata pages to see the data you imported. If any anomalies, specifically invalid field names, are found, MetaDB will alert you of these problems both on this screen and in "Edit Project" after import.

_Export Metadata_

On this screen you may export T/CSV files from the existing metadata. Like on the Import page, select the project with the menu on the upper right hand corner. Once you have selected the delimiter and range of record numbers to export, hit "Export" to receive a download prompt with the generated T/CSV file.

_Controlled Vocabulary_

This is a similar interface to the one found in the "Edit Project" page. Unlike the "Edit Project" version, regular users may be granted permissions to use this feature. However, administrator privileges are still required to tie a field to a controlled vocabulary list.

## Item Metadata ##

This is the main metadata editing screen that you will be interacting with in using MetaDB to catalogue data. At the top you will see the navigation buttons for accessing different records in the project. The fast-rewind button will take you to the first record, the rewind to the previous. The skip button will take you to the next record, and the fast-forward button will take you to the last. You can also enter a number in the box and hit "enter".

On the left side, you will see links to derivative images. Notice that if you haven't generated them, they will be unavailable (for obvious reasons). Below that you will see a thumbnail of the master file, and the file name.

On the right side you will see the attributes for the item and the data contained in them, separated into three tabs for the different types of metadata. Of these, you may edit the data in the "Descriptive" and "Administrative" tabs.

Note that if controlled vocabulary is enabled for any attribute, you will need to input data based on the controlled vocabulary. If the "allow multiple terms" option is set to true, additional terms may be added. If the "allow new terms" option is set to true, new terms may be entered in the field.

The "Update" button will commit any changes so far.

Each attribute has a check box next to it. This is the 'apply to multiple' option. Once you click on at least one check box, a new option will appear next to the "Update" button containing "All" or "These".

"All" will apply the changes you make to the field to ALL records in the project, overwriting any existing data.

For "These" You can enter comma-delimited numbers and number ranges (for ex, to process items 1, 2-5, and 8, you would enter “1, 2-5, 8”) , which are the item numbers of the records you want to apply the change to.

If you have multiple check boxes selected, then that means the data contained in all of the checked attributes will be reflected in the range you specify. You can also select all by clicking the topmost check box.

## Search ##

MetaDB has a standard search function. Exact phrases can be specified by a pair of double quotes (" "). You can select whether to search from all projects or search a single project. Hit "Search" to perform the query. Should any results be found, you will see the thumbnail of the master records the query found, the item number of the records, and the surrounding text of the search query with the key words highlighted.

## Appendix ##

**Master File Processing**

_File organization_

MetaDB follows a very strict organization of master files for the purpose of preserving data integrity and orderliness.

Each master file can be named as desired; however, it is advisable to use a file name structure that makes it clear what project the master file is part of, under what organization; for example, from a file name like lafcol-history-taiwan-0001.tif it is quite obvious that the collection belongs to the Lafayette College History department, and has something to do with Taiwan.

Aside from the consistency in prefixing the images, master files also must be named in a particular ascending order, starting from {prefix}-0001.{extension} and going up to a maximum of {prefix}-9999.{extension}. This is the order in which MetaDB will look for records and the order in which they will be organized within MetaDB. Gaps are not allowed; that is you cannot have something like

..0001.tif
..0002.tif
..0099.tif

If this is detected, MetaDB will refuse to process the third file unless corrective action is taken and the master files are organized properly.

## FAQ ##

## Support/Contact Information ##

MetaDB developers can be contacted via email.

Eric Luhrs, supervisor: luhrse@lafayette.edu
Long Ho, UI and Javascript developer: hol@lafayette.edu
Miguel Haruki Yamaguchi, database and Java backend developer: yamagucm@lafayette.edu