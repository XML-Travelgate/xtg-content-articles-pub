---
title: MealPlanList
keywords: hotel, data structure, meal plan list , meal, list
search: Hotel - Data Structure - MealPlanList
sidebar: mydoc_sidebar
permalink: /docs/hotel/DSF/MealPlanList
---



### Method Goals


This method aims to return a list of the available MealPlans, which will
be used in the availability response.



### Request Format


The request does not require any elements - empty request.



### Response Format


The result returns a list of *MealPlan*.



### Remarks


The maximum time permitted in our system before the connection is closed is  **240000** milliseconds.

If the supplier has more than 100 mealplan codes, or more than 20 codes for one single mealplan, this code will be mapped depending on the supplier.



### MealPlanRQ Example


~~~xml
    <MealPlanListRQ>
    </MealPlanListRQ>
~~~


### MealPlanListRQ Description




| **Element**		| **Number** | **Type** | **Description**		|
| --------------------- | ---------- | -------- | ----------------------------- |
| MealPlanListRQ	| 1          |		| Root node.			|



### MealPlanListRS Example


~~~xml
    <MealPlanListRS>
        <MealPlans>
            <MealPlan>
                <Code>BB</Code>
                <Name>Bed and breakfast.</Name>
            </MealPlan>
            <MealPlan>
                <Code>HB</Code>
                <Name>Half board./Name>
            </MealPlan>
            …
            <MealPlan/>
        </MealPlans>
    </MealPlanListRS>
~~~


### MealPlanListRS Description




| **Element**		| **Number** | **Type** | **Description**	|
| --------------------- | ---------- | -------- | --------------------- |
| MealPlanListRS/MealPlans	| 1          |		| Root node, list of mealplans.		|
| MealPlan	| 1..n          	| 		| MealPlan.			|
| MealPlan/Code	| 1         	| String		| Code.			|
| MealPlan/Name	| 1          	| String		| Name.			|

                       

