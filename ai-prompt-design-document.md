# AI Prompt Design Document

## Introduction:
* Purpose of the Document: This document outlines the design and planning of AI prompts for a project aimed at evaluating the capabilities of AI in generating functional code, specifically for a mobile application. The primary goal is to demonstrate the process of "vibe coding" -- using natural language prompts to bring a software idea to life through AI-assisted code generation.
* Project/Task Overview: The project involves the creation of a React Native mobile application for Android devices to manage a tool shed inventory. The app will allow users to track their tools, including key details such as name, image, and quantity. A core aspect of this project is to use AI prompts to generate the necessary React Native code for the application's development.
* Target AI Model: While a specific AI model isn't explicitly stated at this stage, the prompts will be designed for a large language model (LLM) with strong code generation capabilities, capable of understanding detailed instructions and producing React Native code (JSX, styling, and logic). The experiment aims to test the practical application of such AI in generating a usable mobile application from a high-level concept.

## Objectives of the Prompts:
The primary objective of these prompts is to leverage AI to generate the foundational React Native code for an Android application designed to manage a tool shed inventory.
Specifically, the prompts will aim to achieve the following coding outcomes:
* Basic Application Structure: Generate the initial React Native project setup and the fundamental file structure.
* User Authentication (Google SSO): Implement a single sign-on mechanism using Google for user authentication. This will involve:
    * Integrating with Google Sign-In for React Native.
    * Securely handling user credentials.
* Item Listing with Key Details: Create a main screen that displays an organized list of inventory items. Each item in the list should show:
    * The item's name.
    * An image of the item.
    * The quantity of the item.
    * The username (email) of the user who originally added the item.
* Sortable List: Implement functionality to sort the item list alphabetically (A-Z, Z-A) and by quantity (most to least, least to most).
* Navigation Menu: Develop a navigation menu (e.g., a drawer or a modal) that the user can access to:
    * Navigate to an "Add New Item" screen.
    * Initiate the sign-out process.
* MongoDB Atlas Integration: Implement the necessary code to connect the React Native application to a MongoDB Atlas collection via a web service. This includes:
    * Configuring the application to interact with the MongoDB Atlas database.
    * Storing item details (name, image URL, quantity, and the email of the adding user) in the database.
* Add New Item Feature: Create a screen and logic to allow a signed-in user to add a new item to the inventory. This will involve:
    * Input fields for the item's name and quantity.
    * Functionality to capture an image using the device's camera.
    * Saving the item's details, including the current user's email, to the MongoDB Atlas database.
* Edit and Delete Item Functionality: Enable users to select an item from the list to view its details and provide options to edit or delete the item.
    * Conditional Access: Crucially, the ability to edit or delete an item must be restricted to the user who originally created (added) the item.
    * Editing an Item: Implement a feature that allows the creator of an item to:
        * Capture a new image using the camera, overwriting the existing one.
        * Modify the item's name.
        * Change the item's quantity.
        * Update the item's details in the MongoDB Atlas database.
    * Deleting an Item: Implement a feature that allows the creator of an item to remove it from the MongoDB Atlas database.
* Desired Code Output: The prompts should aim to generate full React Native components, including JSX for the UI and styling, and the necessary TypeScript logic for the functionalities described above.
* Evaluation Criteria for Code Generation Success:
    * Functional Application: The generated code should, when integrated, result in a functional Android application that meets all the described features when tested on an emulator and later on a physical Android device.
    * Code Quality: The generated code should adhere to ESLint standards with Google's guidelines.
    * Code Organization: Individual files should ideally not exceed 500 lines of code and placed into well structured folders.
    * Code Documentation: The code should be well-commented throughout to explain its logic and structure.
    * Testing: The generated code should include unit and integration tests providing 100% test coverage.
    * README File: A comprehensive README file that meets industry standards for providing information about the project, setup instructions, and usage, should also be generated or the prompts should guide its creation.

## Target Audience (of the AI's Output):
The intended audience for the tool shed inventory management application will be a small, closed group including the user (yourself) and a few friends and family members. The primary shared goal among this group is to facilitate the sharing of tools rather than each individual having to purchase the same items.
It is assumed that the technical expertise of this audience regarding mobile applications is very limited to none. Therefore, the application's user interface should prioritize simplicity, intuitiveness, and ease of use to ensure a positive experience for all users, regardless of their technical background.

## Prompt Design Principles:
The following principles will guide the design of the AI prompts for this project:
* Provide Examples: Where feasible, prompts will include relevant code examples or descriptions of desired output to provide the AI with a clear reference.
* Be Detailed: Prompts will be as detailed and specific as necessary to ensure the AI fully understands the task and the desired outcome. Ambiguity will be minimized.
* Instructional Tone: The prompts will use a clear and direct instructional tone to provide unambiguous directions to the AI.

## Prompt Categorization and Examples:

### a. Setup and Configuration Prompts:
#### Prompt Example 1.1: Initial React Native Project Setup
Prompt Text: Your primary task is to generate the precise command-line instructions needed to create a new React Native project using the React Native CLI. Please ensure the project is named ToolShed. Given that the target devices are Android, configure the command specifically for the Android platform. Additionally, provide the subsequent command to navigate into the newly created project's root directory. Assume that the React Native CLI is already installed on the system globally. For this project, we will be using TypeScript, so please include the appropriate template flag in the initialization command.

### b. Authentication Prompts:
#### Prompt Example 2.1: Google Single Sign-On Implementation
Prompt Text: Your task is to generate the React Native code and comprehensive instructions for implementing Google Single Sign-On (SSO) within the ToolShed project. Assume the project has been initialized using the React Native CLI and the TypeScript template. Specifically, I require the following:
* Precise npm installation command for the recommended Google Sign-In package for React Native.
* Step-by-step configuration guide for both the Google Cloud Project (including obtaining the google-services.json file) and the Android-level and app-level build.gradle files to successfully integrate Google Sign-In.
* Complete React Native component code for a login screen. This component must include a button that triggers the Google Sign-In process. The associated logic should handle the full sign-in flow, including capturing the user's ID token and, critically, their email address.
* A clear and functional code snippet for the sign-out process.
* Explicit instructions within the code or a separate note on how to reliably access the signed-in user's email address after a successful login. This email is essential for the application's functionality to track the user who adds each inventory item.
* Crucial Considerations for the Output:
    * Assume I have a basic Google Cloud Project established, but I need the exact configuration steps specific to React Native integration.
    * All provided code should be in TypeScript.
    * Include thorough inline comments within the code to explain the purpose of each section and the logic.
    * Prioritize using the \@react-native-google-signin/google-signin library due to its widespread use and reliability in the React Native community.
    * Ensure the generated code for the login process is designed to be as straightforward and user-friendly as possible from the end-user's perspective, given their limited mobile app experience.
* Please provide the installation command, configuration steps, and code in a well-organized and easy-to-understand format.

### c. UI Component Prompts:
#### Prompt Example 3.1: Main Item List Screen UI
Prompt Text: Your task is to generate the React Native code for the main screen of the ToolShed application. This screen will display a list of the tools in the inventory. Here are the specific requirements for the ItemListComponent:
* Display an organized list of items. Each item in the list should clearly show the following details:
    * Item Name: The name of the tool (as a text element).
    * Item Image: A small, clear image of the tool. This will likely be an image loaded from a URL.
    * Quantity: The current quantity of the tool in the inventory (as a text element).
    * Added By: The email address of the user who initially added the item to the inventory (as a text element).
* The list should be visually appealing and easy to read, even for users with limited mobile app experience. Consider using a FlatList component for efficient rendering of a potentially long list.
* Implement basic styling for the list items, including a clear separation between items. You can use either StyleSheet.create for the styling.
* Make each list item pressable. When an item is pressed, it should ideally trigger an action (we'll define the navigation in a later prompt, but for now, just include a placeholder function like onItemPress).
* The component should be written in TypeScript.
* Include clear and concise comments within the code explaining the purpose of different sections (e.g., the structure of a list item, the FlatList configuration).
* Consider a placeholder for a "Loading..." indicator while the data is being fetched (although the data fetching logic will be handled in a "Data Management" prompt).
Assume the following:
* You will be provided with an array of Item objects, each having properties like name: string, imageUrl: string, quantity: number, and addedBy: string (representing the user's email).
* You do not need to implement the data fetching logic in this component; focus on the UI structure and styling for displaying the list.
* Think about the user experience for someone who is not tech-savvy. The information for each item should be easily scannable.
* Please provide only the React Native TypeScript code for the ItemListComponent.

### d. Data Management Prompts:
#### Prompt Example 4.1: MongoDB Atlas Connection and Basic Operations
Prompt Text: Your task is to generate the TypeScript code for a module or set of functions in the React Native project (ToolShed) that will handle the application's data management by interacting with a MongoDB Atlas database. 
Specifically, I need the code to be able to perform the following operations on a collection (let's call it tools):
* Connect to the MongoDB Atlas database. You'll need to specify how to securely handle the connection string (e.g., using environment variables -- suggest a method for this in React Native).
* Fetch (read) all items from the tools collection. This function should return an array of Item objects. Assume the Item object has the following structure:T {\_id: string, name: string, imageUrl: string, quantity: number, addedBy: string}
* Add (create) a new item to the tools collection. This function should take an Item object as input (without the \_id for a new item).
* Update an existing item in the tools collection. This function will need the \_id of the item to update and the updated Item object (or the fields to update).
* Delete an item from the tools collection. This function will need the \_id of the item to delete.
Important Considerations:
* The code should be written entirely in TypeScript.
* Use a widely-used and well-documented JavaScript/TypeScript library for interacting with MongoDB (e.g., mongoose for a more ORM-like approach if suitable for React Native, or the native MongoDB driver if more appropriate). Please suggest and justify the library choice.
* Include comprehensive error handling for all the database operations (connection errors, read/write errors, etc.).
* Include clear and informative comments within the code explaining each function and the overall structure of the data management module.
* Consider the asynchronous nature of database operations and use async/await for cleaner code.
* Think about reusability: Design the module or functions in a way that they can be easily imported and used by different parts of the React Native application.
* Please provide only the TypeScript code for this data management module/functions. Assume I will handle the MongoDB Atlas setup and security of the connection string based on your suggestions for environment variables.

### e. Logic and Functionality Prompts:
#### Prompt Example 5.1: Item List Sorting and Conditional Actions Logic
Prompt Text: Your task is to generate the TypeScript code for the logic and functions to handle two key functionalities within the ToolShed React Native application, specifically related to the item list:
* Sorting the Item List: Provide the functions necessary to sort the list of Item objects. The list should be sortable in the following ways based on user selection:
    * Alphabetical order by item name: Both A-Z (ascending) and Z-A (descending).
    * By quantity: From most to least (descending) and least to most (ascending).
    * The sorting functions should be pure functions, meaning they take the array of Item objects as input and return a new sorted array without modifying the original.
* Conditional Edit/Delete Logic: Implement the TypeScript logic for determining whether a user has the permission to edit or delete a specific Item. The rule is that only the user who originally added the item (i.e., the addedBy email of the item matches the currently signed-in user's email) should be allowed to edit or delete it.
    * Provide a function, let's call it canModifyItem(item: Item, currentLoggedInUserEmail: string): boolean, that takes an Item object and the current logged-in user's email as input and returns true if the user can modify the item, and false otherwise.
    * Clearly demonstrate how to use the addedBy property of the Item object for this check.
Assume the following:
* You have the Item interface defined as follows: TypeScript interface Item { \_id?: string, name: string, imageUrl: string, quantity: number, addedBy: string}
* You will have access to the currently signed-in user's email address within the application (this would have been handled by the Authentication prompts).
* The code should be written in TypeScript and be well-commented to explain the sorting logic and the conditional check.
* Think about reusability and clarity: The logic should be easy to understand and integrate into the UI components where the sorting and the edit/delete options are presented.
Please provide only the TypeScript code for the sorting functions and the canModifyItem function.

### f. Testing Prompts:
#### Prompt Example 6.1: Unit and Integration Tests for Item Management
Prompt Text: Your task is to generate TypeScript code for both unit tests and integration tests for the core functionality related to item management in the ToolShed React Native application. We need to ensure the reliability and correctness of the code that will handle the adding, retrieving, updating, and deleting of items, as well as the conditional logic for editing and deleting.
Specifically, generate tests for the following aspects:
* Data Management Functions:
    * Unit tests for the functions you would generate based on Prompt Example 4.1 (MongoDB Atlas Connection and Basic Operations). These tests should mock the database interactions to test the logic of the functions in isolation (e.g., addItem, WorkspaceItems, updateItem, deleteItem).
    * Ensure the tests cover different scenarios, including successful operations and potential error handling.
* Logic and Functionality (Conditional Modification):
    * Unit tests for the canModifyItem(item, currentLoggedInUserEmail) function that would be generated based on Prompt Example 5.1 (Item List Sorting and Conditional Actions Logic).
    * Test cases should include scenarios where the currentLoggedInUserEmail matches the addedBy email of the item, and scenarios where it does not.
* Integration Tests (High-Level):
    * Describe high-level integration tests that would verify the interaction between the UI components (from Prompt Example 3.1 - Main Item List Screen UI) and the data management functions.
    * For these integration tests, you don't need to generate the full test code at this moment. Instead, describe the scenarios you would test to ensure that:
        * New items can be added through the UI and are correctly stored in the database.
        * The item list displayed in the UI accurately reflects the data in the database.
        * Editing an item through the UI correctly updates the item in the database, and the changes are reflected in the list.
        * Deleting an item through the UI correctly removes it from the database.
        * The "Edit" and "Delete" options are only visible and functional for items added by the currently logged-in user in the UI.
Important Considerations for the Output:
* The generated test code for unit tests should be in TypeScript and use a common testing framework for React Native (e.g., Jest with ts-jest for TypeScript).
* Include clear and informative comments in the test code explaining the purpose of each test case.
* For the integration tests, the descriptions of the scenarios should be clear and comprehensive, outlining the steps to test the integration.
* Assume I have a basic understanding of unit and integration testing in React Native.
* Please provide only the TypeScript code for the unit tests and the descriptions of the integration test scenarios as requested.

### g. Documentation Prompts:
#### Prompt Example 7.1: Project README and In-Code Comments
Prompt Text: Your task is to generate instructions and content that will help in creating comprehensive documentation for the ToolShed React Native project. This includes a README.md file that meets industry standards and the practice of including meaningful in-code comments.
Specifically, for the README.md file, you should provide a structure and content that includes (but is not limited to):
* Project Title and a brief, clear description of the ToolShed application's purpose and core functionality (managing a tool shed inventory, sharing among friends/family).
* Features Section: A bulleted list of the key features implemented in the application (e.g., Google SSO, item listing with details, sorting, adding/editing/deleting items with conditional access).
* Getting Started Guide:
    * Prerequisites: A list of software and tools users will need to have installed on their development environment to set up and run the project (e.g., Node.js, npm or yarn, React Native CLI, Android Studio, a Google Cloud Project for SSO). Include version recommendations if applicable.
    * Installation Steps: Clear, step-by-step instructions on how to:
        * Clone the repository (assuming it will be in a repository).
        * Install project dependencies.
        * Configure the Google Sign-In (mentioning the need for google-services.json and where to place it, referencing the steps that would be generated by the Authentication prompt).
        * Set up the MongoDB Atlas connection (mentioning the need for the connection string and referencing the setup discussed in the Data Management prompt).
        * Run the application on an Android emulator or device.
* Usage Section: A brief guide on how to use the main features of the application from a user's perspective (e.g., signing in, viewing the item list, adding a new item, editing and deleting items). Given the target audience's limited technical experience, keep this user-focused.
* Contributing Section (Optional but good practice): A brief note on how others could contribute to the project if it were open source (you can make this a general placeholder if not directly applicable now).
* License Information (Optional but important): A section to specify the license of the project.
For In-Code Comments:
* Provide general guidelines on the best practices for writing effective in-code comments within the TypeScript React Native code. Emphasize the importance of:
    * Explaining why a particular code choice was made, not just what the code does (for complex logic).
    * Commenting on functions, classes, and complex or non-obvious blocks of code.
    * Keeping comments concise and up-to-date with the code.
* You do not need to generate specific comments for all the code, but provide examples of good commenting style within the context of a React Native component or a data management function (you can use general, illustrative code snippets for this, not necessarily the full code from other prompts).
* Please provide the structure and content for the README.md and the guidelines and examples for in-code comments in a clear and organized manner. Remember to provide only the text content and instructions for this documentation.

### Testing and Evaluation:
To determine the effectiveness of the AI-generated code based on the prompts and the overall success of the "vibe coding" approach for this project, the following testing and evaluation methods will be employed:
* Testing Methodology:
    * Emulator Testing: The primary method of testing will involve running the React Native application on an Android emulator. This will allow for rapid iteration and testing of the generated code in a controlled environment.
    * Physical Device Testing: Once the application is stable on the emulator, it will be tested on physical Android mobile devices of the users (yourself, friends, and family). This will help identify any device-specific issues and evaluate the real-world user experience.
    * Iterative Testing and Prompt Refinement: The testing process will be iterative. The outputs from the AI for each prompt will be tested, and the prompts themselves will be refined based on the test results. If the generated code doesn't meet the requirements or has bugs, the prompts will be adjusted with more specific instructions or examples, and the code will be re-generated and re-tested.
* Evaluation Criteria:
    * Functional Requirements Met: The most critical evaluation criterion is whether the generated code results in an application that fully meets the functional requirements outlined in the "Objectives of the Prompts" section. This includes:
        * Successful Google Single Sign-On.
        * Accurate display of the item list with all key details.
        * Correct sorting functionality (A-Z, Z-A by name; most-least, least-most by quantity).
        * Smooth navigation.
        * Reliable adding, editing, and deleting of items.
        * Correct implementation of the conditional edit/delete logic (only the item creator can modify).
    * Code Quality: The generated code will be evaluated based on its quality, including:
        * Adherence to ESLint standards with Google's guidelines.
        * Code organization, ideally with individual files not exceeding 500 lines of code.
        * Clarity and readability, facilitated by well-commented code.
    * Test Coverage: The success will also be evaluated by the presence and effectiveness of the generated tests. A target of 100% unit and integration test coverage will be a key metric.
    * Usability for the Target Audience: Although the primary goal is the "vibe coding" experiment, the usability of the resulting application for the intended audience (users with limited technical experience) will also be considered a factor in the overall success.
    * Efficiency of "Vibe Coding": An informal evaluation will be made on the efficiency of using AI prompts for code generation compared to traditional manual coding for a project of this nature.

### Future Considerations/Improvements:
This AI Prompt Design Document is a starting point for the "vibe coding" experiment. As the project progresses, the following future considerations and potential improvements may be explored:
* More Advanced UI/UX: If the core functionality is successfully implemented, future prompts could focus on generating a more polished and user-friendly interface, perhaps exploring more advanced React Native UI patterns or animations.
* Additional Features: Potential future features for the application could include:
    * Search functionality to quickly find specific tools in the inventory.
    * Categorization of tools.
    * Borrowing/lending tracking among the users.
    * Push notifications for reminders (e.g., about borrowed tools).
* Backend Refinements: Depending on the scalability needs, the MongoDB Atlas setup could be further optimized.
* Cross-Platform Compatibility: Although the initial focus is Android, future iterations could explore generating code for iOS as well.
* Evaluation of Different AI Models: If the "vibe coding" experiment is successful with one LLM, future experiments could involve using different AI models to compare their code generation capabilities.
* Formal User Feedback: For future development, gathering more formal feedback from the target audience could help prioritize features and usability improvements.