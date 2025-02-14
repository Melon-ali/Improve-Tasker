# Improve-Tasker-App
## Live Link: https://tasker-app-umber.vercel.app

✓ এই প্রজেক্টে State Management এর ক্ষেত্রে Context API এবং useReducer ব্যবহার করা হয়েছে । । 

✓ প্রজেক্টে "Add Task" বাটনে ক্লিক করলে একটি popup দেখানো হয়েছে এবং সেই popup-এ প্রয়োজনীয় তথ্য প্রদান করে "Create New Task" বাটনে ক্লিক করে Task List এ নতুন Task হিসেবে যুক্ত হয়েছে । 

✓ নতুন Task তৈরি করার ক্ষেত্রে বেসিক কিছু ভ্যালিডেশন করা হয়েছে । অর্থাৎ যদি Title, Description, Tags বা Priority সেট না করেই "Create New Task" বাটনে ক্লিক করে, তাহলে সাবমিট না হয়ে একটি warrning দেখাবে । তবে warning এর জন্যে  [React Toastify](https://www.npmjs.com/package/react-toastify) প্যাকেজ ব্যবহার করা হয়েছে । 

✓ নতুন Task তৈরির, এডিট করারও অপশন আছে, এডিট এর ক্ষেত্রেও ভ্যালিড্যেছ করা হয়েছে । 

✓ Task ডিলিট বাটনে ক্লিক করলে, Task টি Task List থেকে রিমুভ হয়ে যাবে । 

✓ "Delete All" বাটনে ক্লিক করলে সব গুলো Task Delete হয়ে যাবে ।

✓ বেসিক সার্চ ফিচার Add করা হয়েছে । সার্চবার-এ কোন কিছু লিখলে সেটি Task List এই ফিল্টার করে দেখাবে এবং সার্চ বার ফাকা থাকলে, সব গুলো Task-ই Task List-এ দেখাবে । এক্ষেত্রে, সার্চ শুধু Task Title দিয়েই করা হয়েছে । 

✓ Task গুলো Favourite এবং Unfavourite-এ toggle করা যাবে । 

✓ Task add করার সময় Tag ইনপুট নেয়ার সময় কমা সেপারেটেড করে ইনপুট নিতে হবে। যেমন "python,javascript,java" - এরকম।

✓ TaskList এ Task গুলো দেখানোর সময় tag গুলোকে  tag list এ দেখানোর সময় random color দিয়ে tag box গুলো ডিসাইন করা হয়েছে ।

✓ Task লিস্টে যখন কোন Task থাকবে না, তখন সেখানে - "Task List is empty!" দাখানো হয়েছে ।

✓ State Management: This project uses the Context API and useReducer for state management.

✓ Add Task Feature: Clicking the "Add Task" button displays a popup. By providing the required information in the popup and clicking the "Create New Task" button, a new task is added to the Task List.

✓ Validation: Basic validation is implemented when creating a new task. If the "Create New Task" button is clicked without setting the Title, Description, Tags, or Priority, the task won't be submitted, and a warning message is displayed. React Toastify is used for the warning notifications.

✓ Task Edit Option: Tasks can also be edited, and validation is applied during the edit process as well.

✓ Delete Task: Clicking the delete button removes the task from the Task List.

✓ Delete All Feature: Clicking the "Delete All" button removes all tasks from the list.

✓ Search Feature: A basic search feature is implemented. Typing in the search bar filters the Task List based on the input. If the search bar is empty, all tasks are displayed. The search is performed using the Task Title only.

✓ Favorite/Unfavorite Toggle: Tasks can be toggled between Favorite and Unfavorite states.

✓ Comma-Separated Tags: When adding a task, tags must be input as a comma-separated list, e.g., "python,javascript,java."

✓ Tag Styling: While displaying tasks in the Task List, tags are styled with random colors in tag boxes.

✓ Empty Task List: If there are no tasks in the Task List, the message "Task List is empty!" is displayed.

```mermaid
graph TB
    subgraph "UI_Layer"
        addTaskBtn["Add Task Button"]
        searchBar["Search Bar"]
        deleteAllBtn["Delete All Button"]
        taskList["Task List Display"]
    end

    subgraph "State_Management"
        contextAPI["Context API"]
        reducer["useReducer"]
        taskState["Task State"]
    end

    subgraph "Task_Operations"
        subgraph "Creation_Validation"
            inputValidation["Input Validation"]
            toastNotification["Toast Notification"]
        end
        
        subgraph "Task_Actions"
            taskCreation["Task Creation"]
            taskEdit["Task Editor"]
            taskDelete["Task Deletion"]
            taskToggle["Favorite Toggle"]
        end

        subgraph "Tag_Processing"
            tagParser["Tag Parser"]
            tagStyler["Tag Styler"]
        end
    end

    %% UI Interactions
    addTaskBtn -->|"opens"| taskCreation
    searchBar -->|"filters"| taskList
    deleteAllBtn -->|"triggers"| taskDelete

    %% Task Creation Flow
    taskCreation -->|"validates"| inputValidation
    inputValidation -->|"shows errors"| toastNotification
    inputValidation -->|"if valid"| tagParser
    tagParser -->|"processes"| taskState
    
    %% State Management
    taskState -->|"updates via"| reducer
    reducer -->|"updates"| contextAPI
    contextAPI -->|"renders"| taskList

    %% Task Actions
    taskEdit -->|"modifies"| taskState
    taskDelete -->|"removes from"| taskState
    taskToggle -->|"updates"| taskState

    %% Tag Handling
    tagParser -->|"splits comma-separated"| tagStyler
    tagStyler -->|"applies random colors"| taskList
```