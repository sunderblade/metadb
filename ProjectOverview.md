# Introduction #

Here you will find a detailed description of MetaDB. Note: this document is a work in progress as of August 4, 2009.

# Details #

**MetaDB 3.0.0 Detailed Project Overview**

**_Project Summary and Brief History_**

MetaDB is a distributed metadata collection tool developed by Lafayette College Libraries. It allows institutions to use a web-based interface to split digital collection building tasks among several people.

For example, at Lafayette, a librarian creates new projects, defines metadata requirements, supplies data for administrative fields, and imports high-resolution master TIF images into the system. Subject specialists then access the system remotely and enter descriptive data about each item. Once all metadata has been collected, projects are exported as CSV or tab-delimited data files that are easily ingested into most repository systems.

MetaDB supports several features that strengthen digital collection building efforts, including the use of controlled vocabularies, the ability to search, browse, sort, and edit records in different ways, and support for concurrent access by multiple users. The application extracts technical metadata from images, and automatically creates JPG access derivatives that can include branded or banded text, as well as zoomable high-resolution images for close study.

MetaDB version 3 was developed by Eric Luhrs, Digital Initiatives Librarian at Lafayette College, and Computer Science students Long Ho ’10 and Haruki Yamaguchi ’11.

**_Past/Current Concerns in MetaDB_**

_Division of Metadata Creation_

One of the major hassles when dealing with metadata is that different people working on a project have different levels of experience or knowledge about the subject matter. Therefore, it is essential that the right person apply the right data to the right place. MetaDB seeks to solve this problem by having a natural division of responsibilities. For example, all of the import work is handled automatically or by scanning personnel, the data input is mainly handled by specialists with the necessary expertise, and data-wide/system-wide changes are the responsibility of the administrator.

Generally, MetaDB divides metadata into three types.

**Technical metadata**: information that comprises mostly the physical aspects of the record being examined—for example, the dimensions of an image, its original DPI, or import format.

**Administrative metadata**: information not directly related to the content of the records but important for administrative purposes; for example, captions on the physical archive, the contributor(s) of the original records, any pertinent dates, as well as archival information necessary for the proper cataloguing of data.

**Descriptive metadata**: subject and record-specific information that is provided by specialists with the necessary expertise, such as historical context and significance or analysis of a document.

_Concurrent Work_

Many collections consist of hundreds of records, making it impractical to have just one or a few people working on them. The design of MetaDB is such that multiple users can work concurrently without conflicts.

_Remote Access_

MetaDB is a stand-alone web application that runs on any platform as described in the deployment manuals. Thus, the proper web server configurations should yield a system that is accessible from wherever necessary.

_Automation_

MetaDB seeks to eliminate tedious and repetitive tasks through automation. This includes but is not limited to: support of controlled vocabulary (the incorporation of commonly used data into a single entity, which can then be applied to any other data), setting a field to some project-wide global (for example, if there is a field called “contributor” and the value should be “Yamaguchih” for all items, you can simply hit “apply to all” instead of having to go through every single record), thumbnail and scaled-image generation for desired records, and automatic technical metadata (see below) parsing.

_Security_

Permission management was a must from the beginning given that not all users of MetaDB would have access to all of its features. Currently MetaDB supports two types of users: regular users, who can be granted appropriate read or write privileges, and administrators, who have full access to all projects and can also change system settings.

MetaDB uses encryption for the storage of user data and file information.

**Main Component Features**

_User Interface_

MetaDB uses a streamlined, full AJAX user interface. MetaDB was developed on a system running Apache Tomcat 5.5.2.7 and PostgreSQL 8.1, although other database management systems may be used with some code modification. Please refer to the deployment manual for a full technical overview of deployment and software used.

_User and Permission Management_

Through the user management component, administrators may create or delete users, as well as grant, revoke, and change access rights of different users existing in the system. Users can be fine-tuned to have different access levels to the different types of metadata. Administrators automatically have full access to all projects, and should be created with discretion.

_Project Management_

The basis for any work done in MetaDB lies in a project, which is basically a collection of related records (for example, a post card collection or yearbook photographs from a specific year). Projects are given a name, followed by the metadata specification for administrative and descriptive metadata fields. Currently, technical metadata fields are predetermined as to make automatic parsing easier.

_Setting up the project for metadata creation_

Once a project has been created, it will be possible to process the master images for that project into the MetaDB system. MetaDB has the ability to automatically gather technical data from processed master files and generate them for online viewing. MetaDB also handles all of the thumbnail generation. In addition, users have access to a predetermined number of slots for ''derivative images'', which are custom-sized replicas of master files that may be created for any purpose including print publication.

At the time of image processing, users also have the option of adding text watermarks or annotation for informational or legal purposes, with customizable options. These are directly handled by MetaDB and written to disk.

_Import (optional)_

Now that the master files have successfully been incorporated into MetaDB, users can choose to import existing data in CSV/TSV format into the system. Incoming imported data is automatically parsed and applied to the appropriate records in MetaDB.

_Data Management_

As previously mentioned, users may export metadata from projects as well as import. The specific export-import rights are determined by the user’s permission.

The data management component also has a feature we call the “table view”, which basically allows users to select any number of fields in any project and view them at a glance, like a spreadsheet. This is particularly useful when detecting errors such as missing metadata, improper formatting, spelling/grammar mistakes, etc.

_Viewing Item Metadata_

The item metadata viewing system is the main interface that most users of MetaDB will be working with. It consists of a preview of the master file along with all of its associated metadata editing windows. Depending on permissions, users can view metadata as well as edit the contents. From the item views, users also have access to any derivative images created, including a zoom interface for files with large dimensions.

_Controlled Vocabulary_

Controlled vocabulary refers to a predetermined set of words that may be associated with any field in a MetaDB project. For example if a project has a field for the name of the contributor of a master image, say, “contributor”, and there are only four possible contributors, the project manager can create a vocabulary named “contributors” containing those values, set the “contributor” field to “controlled”, tie it to that vocabulary and make it so that whoever is editing the metadata can only choose from those specific options. This is immensely helpful to prevent input errors and to automate tedious tasks. It is also possible to use a ‘suggestion’ mode, where the vocabulary will be visible to the user editing the field but the user is still able to add new terms to the vocabulary if necessary. Please refer to the detailed documentation for further information.