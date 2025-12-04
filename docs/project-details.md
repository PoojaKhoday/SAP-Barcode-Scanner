SAP Build Apps – Mobile Barcode Scanner (Full Documentation)
Low-Code Development on SAP BTP



Platform: SAP Business Technology Platform (BTP)  
Project Type: Low Code App Development using SAP Build Apps (AppGyver)  
Business Scenario: Creating a Mobile Barcode Scanner Application using SAP Build Apps 



Step 1: Environment Setup
Before starting development, the SAP Build Apps environment was accessed through the SAP BTP Trial Account.
Key setup activities:
- Logged in to SAP BTP Cockpit  
- Opened SAP Build Lobby through “Instances and Subscriptions”  
- Confirmed that SAP Build Apps was available for project creation
<p align="center">
<img width="826" height="448" alt="image" src="https://github.com/user-attachments/assets/5f6deac1-2077-411c-878a-158cd294db78" />
</p>

<p align="center"><b>Fig1. SAP BTP Cockpit</b></p>

<img width="824" height="447" alt="image" align="center" src="https://github.com/user-attachments/assets/39cdec83-5ca4-4d5d-a0d2-928d34579608" />


<p align="center"><b>Fig1.1 SAP Build Lobby</b></p>



Step 2: Application Creation
Navigated to the SAP Build Lobby and created a new project:
- Name: Scanner Application  
- Description: Scanner app for reading food barcodes  
Path: Create Project -> Application -> Frontend -> Web & Mobile Application
Selected this option to create a responsive mobile friendly application.
Switched the device preview to Mobile View for designing mobile interfaces.
Screenshots:
<p align="center">
<img width="644" height="549" alt="image" align="center" src="https://github.com/user-attachments/assets/1049c27f-02b0-4eed-864f-ad7336ccd831" />
</p>

<p align="center"><b>Fig 2. Web & Mobile Application</b></p> 
<p align="center">
  <img width="194" height="334" alt="image" align="center" src="https://github.com/user-attachments/assets/f4b32601-bb49-49dc-9d46-209594ffc1eb" />
</p>
<p align="center"><b>Fig 2.1 Mobile View</b></p>
<p align="center">
  <img width="392" height="670" alt="image" align="center" src="https://github.com/user-attachments/assets/58eeb0d5-2585-4041-9b1e-5ed498ce135d" />
  </p>
<p align="center"><b>Fig 2.2 Mobile View Screen </b></p>



Step 3: Understanding the SAP Build Apps Interface
SAP Build Apps provides an intuitive visual builder. Key actions include:
- Designing user interfaces with drag and drop components  
- Configuring navigation and data bindings  
- Creating logic flows using visual programming  
- Integrating external APIs  
- Managing data entities  
This visual builder eliminates traditional coding, enabling rapid application development.
Screenshots:
<p align="center">
<img width="373" height="707" alt="image" src="https://github.com/user-attachments/assets/182dd180-12f8-435f-bc84-9141ecb0594c" />
</p>
<p align="center"><b>Fig 3. Core Components </b></p> 

<p align="center">
<img width="759" height="511" alt="image" src="https://github.com/user-attachments/assets/bfba6231-b1c8-4e32-a564-efda5431a118" />
</p>
<p align="center"><b>Fig 3.1 Data Binding</b></p>

<p align="center">
<img width="744" height="413" alt="image" src="https://github.com/user-attachments/assets/7e747496-9473-4e14-a894-e84fa2ae66dd" />
</p>
<p align="center"><b>Fig 3.2 Navigation</b></p> 
<p align="center">
<img width="696" height="187" alt="image" src="https://github.com/user-attachments/assets/323ca1b6-e22a-403e-bd5a-14110a32243b" />
</p>
<p align="center"><b>Fig 3.3 Logic Flow</b></p>  
<p align="center">
<img width="699" height="436" alt="image" src="https://github.com/user-attachments/assets/38431d93-d12f-4611-a95f-889f59bbe14a" />
</p>
<p align="center"><b> Fig 3.4 REST API Integration</b></p>  



Step 4: Designing the User Interface
Created a simple and clean mobile UI:
- Title: “MyFirstApp”  
- Description: “Scan a barcode of a food product using your smartphone”  
- Button: “Scan” (configured to open the device’s camera)  
This screen serves as the core interface for initiating barcode scanning.
Screenshot:
- Fig 4. Mobile UI


  
Step 5: Configuring Camera Access and Logic Flow
To make the Scan button functional:
- Added logic flow: Device → Scan QR/Barcode
- Connected the output to an Alert (initial testing step)  
- Alert dynamically displayed the scanned barcode value  
This validated integration with device hardware (camera).
Screenshots:
- Fig 5. Scan Button  
- Fig 5.1 Button Flow Logic



Step 6: Connecting to the Open Food Facts Public API  
Integrated the Open Food Facts API to fetch product details using scanned barcodes.
- Data Entity: OpenFoodFacts  
- Base URL: https://world.openfoodfacts.net/api/v0  
- Input Parameter: barcode (text type)  
Retrieve Request Formula:
"/product/" + query.additionalInputs.barcode + "?fields=product_name,nutriments,image_front_url"
Additional actions:
- Successfully tested with barcode 6416453061361
- Set schema from response for data mapping  
Screenshot:
- Fig6. Public OpenFoodFacts API



Step 7: Fetching API Data Based on Scanned Barcode  
Replaced the earlier Alert logic:
- Added Get Record to fetch API data  
- Added Set Data Variable to store API response  
- Bound the API response to a Single Data Record  
This enabled automatic retrieval of product information immediately after scanning.
Screenshots:
- Fig7. Mapping API response  
- Fig7.1 Mapping API response in logic flow  



Step 8: Displaying Product Information  
Enhanced the UI to display fetched data dynamically:
- Title Component: Product Information  
- Text Components: product_name, nutriments.energy  
- Image Component: Bound using:  
data.OpenFoodFacts1.product.image_front_url
Screenshots:
- Fig8. Binding product record  
- Fig8.1 Binding product output  
- Fig8.2 Product name binding  
- Fig8.3 Energy binding  
- Fig8.4 Image binding  
- Fig8.5 Expected UI  



Step 9: Testing the Application  
- Previewed the application using the SAP Build Apps Preview App
- Scanned multiple food barcodes  
- Verified that:  
- Product name  
- Calorie information  
- Product image  
all displayed correctly  
Screenshots: 
- Fig9. Preview QR Code  
- Fig9.1 Barcode to scan  
- Fig9.2 SAP Build Apps mobile preview  
- Fig9.3 Open Application  
- Fig9.4 Scan button  
- Fig9.5 Output with details  
- Fig9.6 Successful execution 1  
- Fig9.7 Successful execution 2  



Business Value and Benefits  
- Low Code Efficiency  
- Allows integration with public APIs  
- Provides a simple, intuitive interface for scanning and retrieving live product data  
- The same model can be extended for healthcare, retail, or inventory applications  



Outcome  
- Built a fully functional mobile application using SAP Build Apps with no manual coding  
- Enabled camera-based barcode scanning  
- Integrated public API for real time data retrieval  
- Implemented dynamic UI binding  



Conclusion  
This project demonstrates how SAP Build Apps can simplify the development of powerful, data-driven mobile applications using low-code tools.  
The Scanner Application integrates device functionality and live APIs, showcasing SAP Build Apps as a versatile platform for rapid innovation.
