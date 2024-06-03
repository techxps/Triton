## Table of Contents
1. [API Authentication](#api-authentication)
2. [Hospital Management](#user-management)
   - [Get All Departments](#get-all-departments)  <!-- Updated -->
   - [Get Wards By Department](#get-wards-by-department)  <!-- Updated -->
   - [Get Designations By Hospital](#get-designations-by-hospital)  <!-- Updated -->
3. [JML Leaving Process](#joining-nurses)
   - [Joining Nurses](#joining-nurses)  <!-- Updated -->
   - [Moving Nurses](#moving-nurses)  <!-- Updated -->
   - [Leaving Nurses](#leaving-nurses)  <!-- Updated -->
4. [Shift Management](#shift-management)
   - [Off-duties / Duty Roster](#off-duties--duty-roster)  <!-- Updated -->
   - [Clock-in](#clock-in)  <!-- Updated -->
5. [Update Rates](#update-rates)
   

## API Authentication

### Authorization Token

**Endpoint**: `POST /api/Account/checkuser`

**URL**: `https://tritonclientapi.converge-solutions.com/api/Account/checkuser`

**Parameters**:

| Parameter  | Type   | Description                |
|------------|--------|----------------------------|
| UserName   | string | EmailId/Username           |
| Password   | string | Password                   |
| HospitalId | int    | Unique Id                  |

![image](https://github.com/techxps/Triton/assets/169183598/e7c06213-358d-4bd6-b9a4-8b153d4ca919)



---

## Master API
## Get All Hospitals

To retrieve all hospitals, make a POST request to the following API endpoint:

**Endpoint**: `POST /api/Account/GetAllHospitals`

**URL**: `https://tritonclientapi.converge-solutions.com/api/Account/GetAllHospitals`

### Parameters:

| Parameter  | Type   | Description                |
|------------|--------|----------------------------|
| CityId   | Integer |use "2" in CityId           |


## Get All Departments

To retrieve all departments related to a particular hospital, make a POST request to the following API endpoint:

**Endpoint**: `POST /api/Admin/GetAllDepartments`

**URL**: `https://tritonclientapi.converge-solutions.com/api/Admin/GetAllDepartments`

### Parameters:

| Parameter  | Type   | Description                |
|------------|--------|----------------------------|
| HospitalId   | Integer |Hospital Id           |


You can get all the hospital ID by using the hospital API.

---

## Get Wards By Department

To get all the wards related to a particular department and hospital, use the following API endpoint:

**Endpoint**: `POST /api/Admin/GetWardsByDepartment`

**URL**: `https://tritonclientapi.converge-solutions.com/api/Admin/GetWardsByDepartment`


### Parameters:

| Parameter  | Type   | Description                |
|------------|--------|----------------------------|
| HospitalId   | Integer |Hospital Id           |
| DepartmentId   | Integer |Department Id           |


You can obtain the hospital ID and department ID by using the relevant APIs.

---

## Get Designations By Hospital

To retrieve all designations related to a particular hospital, make a POST request to the following API endpoint:

**Endpoint**: `POST /api/Admin/GetDesignationByHospital`

**URL**: `https://tritonclientapi.converge-solutions.com/api/Admin/GetDesignationByHospital`

### Parameters:

| Parameter  | Type   | Description                |
|------------|--------|----------------------------|
| HospitalId   | Integer |Hospital Id           |



### JML Leaving Process

## Joining Nurses

When a nurse joins your organization and their details are captured in your HR system, you can follow this process to create the nurse automatically in Triton.

**Endpoint**: `POST /api/Roaster/CreateUserByEmployeeNumber`

**URL**: `https://tritonclientapi.converge-solutions.com/api/Roaster/CreateUserByEmployeeNumber`


**Parameters**:

| Parameter  | Type   | Description                |
|------------|--------|----------------------------|
| UserName   | String  |  Name of User   (Required)        |
| Password   | String  |  Password  (Required)         |
| RoleId     | Integer | //4 Please use role id 4 for nurse role           |
| HospitalId | Integer | Hospital Id           |
| EmailId    | String  | Email Id          |
| DepartmentId | Integer | Deparrment Id           |
| WardId | Integer | Ward Id           |
| DesignationId | Integer | Designation Id           |
| EmployeeNumber | Integer | EmployeeNumber Id           |
| CreatedBy     | Integer | //1 Please use  id 1           |


---

## Request Formats

### Sample:

```json
{
  "CreatedBy": 1,
  "Password": "sample string 1",
  "qualification": "sample string 3",
  "Image": "sample string 5",
  "UserName": "sample string 6",
  "Name": "sample string 7",
  "LastName": "sample string 8",
  "EmailId": "sample string 9",
  "Address": "sample string 10",
  "EmployeeNumber": "sample string 11",
  "Country": "sample string 12",
  "Mobile": "sample string 13",
  "RoleId": 4,
  "DepartmentId": 1,
  "HospitalId": 1,
  "DesignationId": 1,
  "ReportTo": 1,
  "WardId": 1
}
```

## Moving Nurses

When a nurse movings their designation , department, ward 

**Endpoint**: `POST /api/Roaster/UpdateUserByEmployeeNumber`

**URL**: `https://tritonclientapi.converge-solutions.com/api/Roaster/UpdateUserByEmployeeNumber`


**Parameters**:

| Parameter  | Type   | Description                |
|------------|--------|----------------------------|
| UserName   | String  |  Name of User   (Required)        |
| Password   | String  |  Password  (Required)         |
| RoleId     | Integer | //4 Please use role id 4 for nurse role           |
| HospitalId | Integer | Hospital Id           |
| EmailId    | String  | Email Id          |
| DepartmentId | Integer | Deparrment Id           |
| WardId | Integer | Ward Id           |
| DesignationId | Integer | Designation Id           |
| EmployeeNumber | Integer | EmployeeNumber Id           |
| ModifiedBy     | Integer | //1 Please use  id 1           |



## Request Formats

### Sample:

```json
{
  "ModifiedBy": 1,
  "Password": "sample string 1",
  "qualification": "sample string 3",
  "Image": "sample string 5",
  "UserName": "sample string 6",
  "Name": "sample string 7",
  "LastName": "sample string 8",
  "EmailId": "sample string 9",
  "Address": "sample string 10",
  "EmployeeNumber": "sample string 11",
  "Country": "sample string 12",
  "Mobile": "sample string 13",
  "RoleId": 4,
  "DepartmentId": 1,
  "HospitalId": 1,
  "DesignationId": 1,
  "ReportTo": 1,
  "WardId": 1
}
```

## Leaving Nurses

**Endpoint**: `POST /api/Roaster/LeavingUserByEmployeeNumber`

**URL**: `https://tritonclientapi.converge-solutions.com/api/Roaster/LeavingUserByEmployeeNumber`


**Parameters**:

| Parameter  | Type   | Description                |
|------------|--------|----------------------------|
| ModifiedBy | Integer |1           |
| IsActive | Boolean | False           |
| EmployeeNumber | string | EmployeeNumber           |




---
## Off-duties / Duty Roster

To manage off-duties or duty roster, you need to call the following API with the requested parameters:


**URL**: `https://tritonclientapi.converge-solutions.com/api/Roaster/CreateUserShiftByEmployeeNumber`

**API Endpoint**: `POST api/Roaster/CreateUserShiftByEmployeeNumber`

### Parameters:

**Parameters**:

| Parameter  | Type   | Description                |
|------------|--------|----------------------------|
| EmployeeNumber   | String  |  Unique identification   (Required)        |
| DepartmentId   | Integer  |  Required         |
| ShiftMasterId     | Integer | Shift Type           |
| ShiftDate | DateTime | Required (DateTime Format: mm/dd/yyyy)          |
| CreatedBy    | Integer  | 1         |


To get the `ShiftMasterId`, use the following enum class:

- For "Day" shift, use 1.
- For "Night" shift use 2.

### Sample Request:

```json
[
  {
    "$id": "1",
    "UserId": 1,
    "DepartmentId": 2,
    "ShiftMasterId": 3,
    "ShiftDate": "2024-05-29T13:49:43.3481105+00:00",
    "ShiftStartDate": "2024-05-29T13:49:43.3481105+00:00",
    "ShiftEndDate": "2024-05-29T13:49:43.3481105+00:00",
    "ShiftId": "sample string 4",
    "EmployeeNumber": "sample string 5",
    "CreatedBy": 1
  },
  {
    "$ref": "1"
  }
]
```
---
## Clock-in

When a staff member physically clocks in on-site, you can push that information to the Surveillance environment on Triton using the Clock-in API. This allows you to populate the existing column for clock-in data and enables reporting from Triton as a single source. Reporting can still be combined without integration by including two reporting sources – one for planning (Triton) and one for actuals (your clock-in system).

### API Endpoint

**URL**: `https://tritonclientapi.converge-solutions.com/api/Roaster/UserShiftClockIn`

**API Endpoint**: `POST api/Roaster/UserShiftClockIn`


### Parameters

| Parameter  | Type   | Description                |
|------------|--------|----------------------------|
| EmployeeNumber   | String  |  Unique identification   (Required)        |
| DepartmentId   | Integer  |  Required         |
| ShiftMasterId     | Integer | Shift Type           |
| ShiftDate | DateTime | Required (DateTime Format: mm/dd/yyyy)          |
| CreatedBy    | Integer  | 1         |

### Sample Request:

```json
[
  {
    "$id": "1",
    "UserId": 1,
    "DepartmentId": 2,
    "ShiftMasterId": 3,
    "ShiftDate": "2024-05-29T13:49:43.3481105+00:00",
    "ShiftStartDate": "2024-05-29T13:49:43.3481105+00:00",
    "ShiftEndDate": "2024-05-29T13:49:43.3481105+00:00",
    "ShiftId": "sample string 4",
    "EmployeeNumber": "sample string 5",
    "CreatedBy": 1
  },
  {
    "$ref": "1"
  }
]



```
## Update Rates

### API Endpoint

**URL**: `https://tritonclientapi.converge-solutions.com/api/Admin/UpdateNurseWiseCTC`

**API Endpoint**: `POST api/Admin/UpdateNurseWiseCTC`


### Parameters

| Parameter  | Type   | Description                |
|------------|--------|----------------------------|
| NightShiftList   | String  |  Required        |
| DayShiftList   | String  |  Required         |
| EmployeeNumber     | Integer | Required           |

### Sample Request:

```json
[

{
   "EmployeeNumber":"",
  "NightShiftList": [
    {
      
   
      "AveragePerhourCost": 1.0,
      "SpecialPerhourCost": 1.0,
      "OverTimePerhourCost": 1.0,
      "ShiftType": 5,
      "RateWise": 1,
      "HospitalId": 1,
      "DesignationId": 1,
      "Name":"Monday"
    },

{
      
     
      "AveragePerhourCost": 1.0,
      "SpecialPerhourCost": 1.0,
      "OverTimePerhourCost": 1.0,
      "ShiftType": 5,
      "RateWise": 1,
      "HospitalId": 1,
      "DesignationId": 1,
      "Name":"Tuesday"
    },
   
  ],
  "DayShiftList": [
    {
     
      "AveragePerhourCost": 1.0,
      "SpecialPerhourCost": 1.0,
      "OverTimePerhourCost": 1.0,
      "ShiftType": 5,
      "RateWise": 1,
      "HospitalId": 1,
      "DesignationId": 1,
      "Name":"Monday"
       },
    {
     
      "AveragePerhourCost": 1.0,
      "SpecialPerhourCost": 1.0,
      "OverTimePerhourCost": 1.0,
      "ShiftType": 5,
      "RateWise": 1,
      "HospitalId": 1,
      "DesignationId": 1,
      "Name":"Tuesday"
       },
   
  ]
  
}
]
