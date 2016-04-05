Crossknowledge - Content Provider Data Feed
===========================================

This resource is targeted at content providers wanted to integrate with our
content management system.


Format of the content
---------------------

At the moment, we accept these different formats:
* Static Files : pdf, docx, xlsx, images etc.
*  Video Files : mp4, with subtitles in srt format;
*  Scorm Packages : 1.2 and 2004.

Metadata and presentation
-------------------------

The metadata should be presented as an XML file. You'll find the XML Schema in this repository (catalog\_import.xsd)

### Presentation
```xml
<?xml version="1.0" encoding="UTF-8"?>
<catalog>
	<provider>
		<name>CrossKnowledge Library</name>
		<description>Content from LCMS Content</description>
		<picture>http://example.ck/crossknowledge.gif</picture>
		<defaultThumbnail>
			<content>crossknowledge.gif</content>
		</defaultThumbnail>
	</provider>
	<contents>
		<content>
			<refId>OJMH390</refId>
			<refIdVersion>OJMH390_v1</refIdVersion>
			<title>How to Give a Constructive Feedback</title>
			<locale></locale>
			<description>Feedback can help staff members to progress and develop their skills provided it is given in the right way. This session will show you how to identify common errors and the principles of constructive feedback.</description>
			<summary/>
			<type>See description</type>
			<subtype>See description</subtype>
			<runtime>See description</runtime>
			<thumbnail></thumbnail>
			<url>http://path/to/object/OJMH390.zip</url>
			<tags>
				<tag>Skills Management</tag>
				<tag>Training</tag>
				<tag>Evaluation</tag>
				<tag>Learning</tag>
			</tags>
			<themes>
				<theme>Developing Autonomy</theme>
			</themes>
			<duration>30</duration>
			<audiences></audiences>
			<level>1</level>
			<objectives></objectives>
			<additionalData></additionalData>
		</content>
	</contents>
</catalog>
```

XML content description
------- 

|Field/Node                                                         |Type/Format            |Size       |Required       |Description        |
| :-------                                                          | :----                 | :---:     | :---:         |:---               |
|**catalog**                                                        |Main node              |           |YES            |                   |
|&nbsp; **provider**                                                |   node                |           |YES            |   Informations block about provider   |
|&nbsp; &nbsp; name                                                 |   text                |           |YES            |                   |
|&nbsp; &nbsp; description                                          |   text                |   256     |YES            |   Short description about company, content, etc
|&nbsp; &nbsp; picture                                              |   url                 |suggestion: 250px X 60px. |YES |   Absolute or relative url. To relative url, the url should be relative to this XML. Eg. XML url: http://somesite.com/PATH_TO_XML/catalog.xml, the url for this image should be PATH_TO_XML/someimage.png
|&nbsp; &nbsp; thumbnail                                            |   url                 |           |              |    |	Image which represent the provider, like logo, symbol, etc. There is no limit to the thumbnail size, but we recommend a proportional image to 640x320px.
|&nbsp; **contents**                                                |   node                |           |YES            |
|&nbsp; &nbsp; content                                              |   node                |           |YES            |   For each content
|&nbsp; &nbsp; &nbsp; refId                                         |   text                |   45      |YES            |   Reference ID. Must be unique for all versions of content. Eg: AB22 . The refId represents the content in all languages and versions available.
|&nbsp; &nbsp; &nbsp; refIdVersion                                  |   text                |   45      |YES            |   Reference ID Version. Represent version of content. Eg: AB22 English v1, AB22 Spanish v2, etc.
|&nbsp; &nbsp; &nbsp; firstPublicationDate                          |   date (YYYY-mm-dd)   || No (highly recommended)  |   First publication date. Creation date to help versions control.
|&nbsp; &nbsp; &nbsp; title                                         |	text				|           |	YES			|	Do not must be unique, but highly recommended
|&nbsp; &nbsp; &nbsp; subtitle                                      |	text				||							|
|&nbsp; &nbsp; &nbsp; locale                                        |	text				||							|	Language of content. Better if uses the language&nbsp;Country format. Eg: en&nbsp;US, fr&nbsp;FR, etc.
|&nbsp; &nbsp; &nbsp; description                                   |	text				||							|
|&nbsp; &nbsp; &nbsp; summary                                       |	text				||							|   Summary should be empty. Use **description** instead 
|&nbsp; &nbsp; &nbsp; type                                          |	text				||							|   Use "a" => Audio, "d" => Document to download, "p" => Image, "i" => Interactive content (Scorm), "r" => Reading document, "v" => Video, "w" => Website, Url, etc.
|&nbsp; &nbsp; &nbsp; subtype                                       |	text				|           |   YES			|   If the content is categorized, put category here
|&nbsp; &nbsp; &nbsp; runtime                                       |	text				||							|   Use "CKLM_SCORM" => Scorm, "CKLM_FILE" => Reading document LIKE PDF, Image, DOC, "link_lo_guid" => Website, url
|&nbsp; &nbsp; &nbsp; url                                           |	text				||							|
|&nbsp; &nbsp; &nbsp; alternateUrl                                  |	url					||							|
|&nbsp; &nbsp; &nbsp; thumbnail                                     |	url					||							|
|&nbsp; &nbsp; &nbsp; audience                                      |	text				||							|
|&nbsp; &nbsp; &nbsp; objectives                                    |	text				||							|
|&nbsp; &nbsp; &nbsp; duration                                      |	int					||							|	In minutes Eg. 10,20,etc.
|&nbsp; &nbsp; &nbsp; course                                        |	text				||							|
|&nbsp; &nbsp; &nbsp; **tags**                                      |						||							|	One or more, one per tag
|&nbsp; &nbsp; &nbsp; &nbsp; tag(1)                                 |	text				||							|
|&nbsp; &nbsp; &nbsp; &nbsp; tag(n)                                 |	text				||							|
|&nbsp; &nbsp; &nbsp; **themes**                                    |						||							|
|&nbsp; &nbsp; &nbsp; &nbsp; theme(1)                               |	text				||							|
|&nbsp; &nbsp; &nbsp; &nbsp; theme(n)                               |	text				||							|
|&nbsp; &nbsp; &nbsp; **authors**                                   |						||							|	One or more
|&nbsp; &nbsp; &nbsp; &nbsp; author                                 |	text				||							|
|&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; firstname                       |	text				||							|
|&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; lastname				        |	text				||							|
|&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; email                           |	text				||							|
|&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; jobtitle				        |	text				||							|
|&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; company                         |	text				||							|
|&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; phone                           |	text				||							|
|&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; authorThumbnail                 |	text				||							|
|&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; customGuid                      |	text				||							|
|&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; competencies			        |	text				||							|
|&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; authorThumbnail                 |	text				||							|
|&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; **biographies**                 |						||							|
|&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; biography                |						||							|	One or more
|&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; locale            |						||							|	Language of biography. Should be in this format: language-COUNTRY. Eg: en-US, fr-FR, etc.
|&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; biographyFull     |						||							|
|&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; biographyShort    |						||							|
|&nbsp; &nbsp; &nbsp; additionalData                                |	text				||							|
|&nbsp; &nbsp; &nbsp; videoSubtitles                                |						||							|
|&nbsp; &nbsp; &nbsp; &nbsp; subtitle (en&nbsp;US)                  |	text				||							|	Eg: legend_en-US.srt
|&nbsp; &nbsp; &nbsp; &nbsp; subtitle (fr&nbsp;FR)                  |	text				||							|	Eg: legend_fr-FR.srt
|&nbsp; &nbsp; &nbsp; audiences                                     |						||							|	One or more audience. Eg: Leader, Senior manager, project manager, etc. One audience pe tag.
|&nbsp; &nbsp; &nbsp; &nbsp; audience (1)                           |	text				||							|
|&nbsp; &nbsp; &nbsp; &nbsp; audience (2)                           |	text				||							|
|&nbsp; &nbsp; &nbsp; level                                         |	int					|  1,2 or 3     |	        |
|&nbsp; &nbsp; &nbsp; scoreinprogress                               |	text				||							|
|&nbsp; &nbsp; &nbsp; detailedcontent                               |	text				||							|


How do I test my catalog.xml ?
------------------------------

We've included a simple python tool to test that

### Requirements

To use our tool you need to make sure that you have python-lxml installed:
```bash
pip install -r requirements.txt
```

### Check my catalog

Once you have the requirements installed you can check your datafeed like this:
```bash
python ./check.py my_catalog.xml
```


