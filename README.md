# UiPath_Document_Understanding

The UiPath Studio package that contains all the activities needed to enable information extraction is called Intelligent OCR

OCR is a method that reads text from images, recognizing each character and its position. It comes handy in the Digitize step of the process when dealing with non-native documents, like scanned files.

OCR is a method that helps in the Digitize step of the Document Understanding process. 

Document Understanding is a process enabled by UiPath's Intelligent OCR package, making full document processing possible. 

Depending on the category and the context of the information targeted for extraction, different approaches are recommended: rule-based or model-based.

Order of Document Understanding Framework steps
  Taxonomy
  Digitization
  Classification
  Extraction
  Valiation
  Export
  Training Classififers and Extractors
  
 Note: If you are working with multiple documents types in the same project, to extract data properly you need to know what type of document you're facing. If you work with just one type of document, then classification is not needed.
 
 Activities in the Intelligent Package OCR
 
 Taxonomy Manager

Once the package is installed, a Taxonomy Manager button appears on the Ribbon, in the Wizards section. 

With the Taxonomy Manager Wizard, you can create the Taxonomy for your document understanding project, meaning the information that you want to extract and the type of that information (Ex: date, table, etc.)


Load Taxonomy

Loads the taxonomy created with the help of the Taxonomy Manager into a variable that can be further used with other activities. 


Digitize Document

For scanned documents or images, this activity will use OCR to extract the text and the Document Object Model, a JSON object containing information regarding the positions of the words on the document. 

For digital documents, the text will be extracted without the use of the OCR engine.


Classify Document Scope 

The scope allows multiple classifiers to be used in order to classify the documents. You can find classifiers in the Intelligent OCR activity package, as well as in other UiPath or third-party packages (e.g.,  UiPath.Abbyy.Activities.).
  
  
 Configure Classifiers Wizard 

With the Configure Classifiers Wizard, you can configure the Classify Document Activity. 

It allows multiple classifiers to be used in order to classify the documents. You can also establish a confidence threshold for each type of classifier. 


Data Extraction Scope 

The scope allows multiple extractors to be used in order to extract the data from the documents.

You can use any extractor that is available in the IntelligentOCR package, in other UiPath or third-party packages (e.g., UiPath.DocumentUnderstanding.ML.Activities, UiPath.Abbyy.Activities) or you can create your own extractor. 


Configure Extractors Wizard

With this Wizard, you can customize which extractors will be used for each individual field, of each document type.  

You can mix and match extractors as well as use extractors in a hybrid approach. In this case, the extraction method would be chosen based on which extractor has the highest confidence level. 


Present Validation Station

Opens the Validation Station, which enables you to review and correct document classification and automatic data extraction results. 


Integrated Validation Station 

This activity pair allows for the creation of Validation Station human tasks in a web-based environment, through UiPath's Actions (in Orchestrator or the Actions Apps). 


Validation Station

The extracted data can be corrected and confirmed by a human user through the Validation Station. 

Export Extraction Results

Once you have your extracted information, you can use it as it is, or save it in a DataTable format that can be converted very easily into an Excel file. 


Train the Classifiers and Extractors used

Sometimes, the workflow may fail to recognize the document or extract the correct data. 

To improve the classifiers and extractors' performance, even if they recognized the correct data, you should train them.

Note: 
The Taxonomy is automatically created when you first open the Taxonomy Manager. It is saved in the project folder, under Document Processing. It takes the form of a JSON file and it's important to remember that you can have only one taxonomy file per project.




What is Taxonomy 

It all starts with categorizing the documents and defining the information you want to extract. You can work with invoices, governmental forms, contracts, ID documents, employee resumes, and so on, at the same time. 

After installing the Intelligent OCR package, you will notice that in the Design ribbon you have a new icon.

By selecting it, a new window will be displayed.


Working with Taxonomy - Load taxonomy
Turning the JSON file into a variable is done with the Load Taxonomy activity. The activity automatically recognizes the input file, as it has a standard location inside the project folder. 

The only parameter to be set is the output variable, which will later be used with other Document Understanding activities.

Note:
The contents of a Taxonomy file sometimes need to be stored outside of the project.  In such cases, once the JSON content is retrieved (for example from a database or other central storage locations) using the appropriate activities, it can be de-serialized into a Taxonomy object.  For more in-depth information about how to accomplish this, see this documentation page.https://docs.uipath.com/activities/docs/document-taxonomy-class

 Note: The fields needed for extraction are the fields you will need to define in the Taxonomy.
 
 Tip: Practice - Adding a new document type section is where the actual hands on session starts
