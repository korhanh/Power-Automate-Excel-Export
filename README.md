# SharePoint to Excel: Free and Unlimited Data Export with Power Automate

This project provides a solution for exporting data from a SharePoint list to Excel using Microsoft Power Automate, allowing you to perform unlimited exports effortlessly. Follow the steps below to set up and use this solution:

## How It Works

1. **Create a SharePoint List**:
   - Set up your SharePoint list with the necessary columns such as ID, Musteri_Name, Sip_No, and DHL.
     
![image-1](https://github.com/korhanh/Power-Automate-Excel-Export/blob/main/1.PNG)

2. **Create a Power Automate Flow**:
   - Log in to Power Automate and create a new flow.

3. **Set Up the Trigger**:
   - Select the SharePoint trigger "Recurrence" to schedule the flow at your desired intervals (e.g., daily, weekly).

![image-2](https://github.com/korhanh/Power-Automate-Excel-Export/blob/main/2.PNG)

4. **Get Items**:
   - Add the SharePoint action "Get items" to retrieve the data from your list.

![image-3](https://github.com/korhanh/Power-Automate-Excel-Export/blob/main/3.PNG)


5. **Send Data to API**:
   - Add an HTTP action to send the data to an API service:
     - **Method**: POST
     - **URI**: https://zetaleap.com/process_excell/
     - **Headers**: Authorization Bearer (Visit : https://zetaleap.com/)
     - **Body**:
       ```json
       {
         "allowed_columns": [
           {
             "ID": "ID"
           },
           {
             "Musteri_Name": "Customer Name"
           },
           {
             "Sip_No": "Order Number"
           },
           {
             "DHL": "DHL Code"
           }
         ],
         "value": @{outputs('Get_items')?['body/value']}
       }
       ```
     - **Important**: Ensure that the column names in the `allowed_columns` section of the JSON body exactly match the column names in your SharePoint list. For instance, if your SharePoint list has a column named "Customer Name," it must be specified as `"Musteri_Name": "Customer Name"` in the JSON.

![image-4.1](https://github.com/korhanh/Power-Automate-Excel-Export/blob/main/4.1.PNG)


6. **Receive and Send Excel File**:
   - After receiving the data from the API, add an action to compose the Excel file content and then send it via email.

   - **Create File**: Use the output from the API to create an Excel file.

![image-5.1](https://github.com/korhanh/Power-Automate-Excel-Export/blob/main/5.1.png)

![image-6](https://github.com/korhanh/Power-Automate-Excel-Export/blob/main/6.PNG)

   - **Send Email**: Add the "Send an email" action to email the Excel file.

![image-6](https://github.com/korhanh/Power-Automate-Excel-Export/blob/main/7.PNG)

## Features

- **Unlimited Exports**: Export as much data from SharePoint to Excel as needed without any restrictions.
- **Easy Setup**: Follow the step-by-step guide to create the flow and configure it according to your requirements.
- **Seamless Automation**: Automate the data export process effortlessly within SharePoint.

## Requirements

- Microsoft Power Automate subscription
- Basic knowledge of SharePoint and Power Automate flow creation
- API endpoint and authorization details

## Getting Started

- Follow the steps outlined above to create and configure your Power Automate flow.
- Customize the SharePoint list and API details as needed.
- Use the output from the API to generate and email Excel files.

## Contributions and Feedback

Contributions to this project are welcome! If you encounter any issues or have suggestions for improvement, feel free to open an issue or submit a pull request.

## License

This project is licensed under the [MIT License](https://github.com/korhanh/Power-Automate-Excel-Export/blob/main/LICENSE).

Feel free to use, modify, and distribute this project according to the terms specified in the license.

## Credits

This project is created and maintained by [korhanh]([link_to_your_github_profile](https://github.com/korhanh)).

If you use this project or find it helpful, consider giving it a star on GitHub!
