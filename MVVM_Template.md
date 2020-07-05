# Model - View - ViewModel ( MVVM ) Architecture

## Introduction

MVVM is one of simple and very useful architecture. It's being used in various commercial applications with great success. To understand success of MVVM we will have "Start With Why" just like [Simon Sinek](1) said. We will have to understand why do we need software architecture and how MVVM is useful. Main intension of this article is to give head-start to reader.

## "What is architecture?"

Software architecture is fundamental structure for code which will define elements and relations between them. To read more in depth start from [Software architecture Wiki](3) definition. If you have architecture well defined it gets really simple to write code.

## "What is MVVM?"

Model - View - ViewModel is architecture with 3 distinct areas isolated but directly dependent on lower module.

![MVMM Diagram](MVVM_images/MVVMPattern.png)

For more information you can start from [MVVM Wiki](2).

I have created very simplified version of [MVVM Template code](4) that can be copied and modified for required application.

## View

This is presentation module or for visual representation of main data. In multilayer view can be display of data for next layer. For example user inputs like text in a textbox, or graph created from data are example of View module. You have to take care that there is no code which is taking action on data or modifying data in any way.

This module changes only when there is changes for presentation of data, like placement of controls, font colors.

To pass data from View to VM direct function calls can be used but to pass data from VM to view dependency property or event bindings are used.

## View - Model (VM)

View - Model is module for interpretation of user data. In this module all action on data for conversion is taken. There should be nothing related to rendering or presentation.

This module changes when there are changes in interpretation of data, like user wants to change unit system in view then data conversion is added in VM. So making change in VM we can keep Model module unchanged as final unit for data is kept constant. Also there are very few changes in view-model to add options for view.

To pass data from VM to model direct function calls can be used but to pass data from model to VM events delegates are used.

## UI Services

In many cases there are user actions required for completing action. For some things user needs to be shown some dialog which are initialized from view-model. In such case UI services can be used. UI services are request for user intervention, or updating user with current state of operation. But as view thread and view model threads can be different, UI service can help VM to pass query across threads.

## Model

Model module is main business logic module. Any logic specific to business like business rules or creating results from user inputs is created here in Model.

This module is modified only when there are fundamental changes in business logic.

### Benefits

- Single responsibility : Each module have single responsibility only.
- Isolated code : Code is isolated in different modules.
- Maintainability : Code is simple to maintain.

## Conclusion

MVVM is simple segregation of code in three different modules, with rules of engagement between each module. Due to these simple rules, code created is very easy to maintain. These simple rules can be extended to any big or small application and still it will perform very well.

## References

[1] `https://twitter.com/simonsinek`  
[2] `https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93viewmodel`  
[3] `https://en.wikipedia.org/wiki/Software_architecture`
[4] `https://github.com/deorerohan/MVVM_Template`
