## Table of Contents
1. [API Authentication](#api-authentication)
2. [User Management](#user-management)
   - [Check Users API](#check-users-api)
   - [Forgot Password](#forgot-password)
3. [Hospital Management](#user-management)
   - [Get All Departments](#get-all-departments)  <!-- Updated -->
   - [Get Wards By Department](#get-wards-by-department)  <!-- Updated -->
   - [Get Designations By Hospital](#get-designations-by-hospital)  <!-- Updated -->
4. [Shift Management](#shift-management)
   - [Off-duties / Duty Roster](#off-duties--duty-roster)  <!-- Updated -->
   - [Clock-in](#clock-in)  <!-- Updated -->

## API Authentication

### Authorization Token

**Endpoint**: `POST /api/Account/AuthorizationToken`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Account/AuthorizationToken`

**Parameters**:

| Parameter  | Type   | Description                |
|------------|--------|----------------------------|
| UserName   | string | EmailId/Username (Required)|
| Password   | string | Password (Required)        |
| HospitalId | int    | Unique Id (Required)       |

---

## User Management

### Check Users API

**Endpoint**: `POST /api/Account/admincheckuser`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Account/admincheckuser`

**Parameters**:

| Parameter  | Type   | Description                |
|------------|--------|----------------------------|
| UserName   | string | Email Id/Username (Required)|
| Password   | string | Password (Required)        |
| HospitalId | int    | Unique Id (Required)       |

---

### Forgot Password

**Endpoint**: `POST /api/Account/ForgotPassword`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Account/ForgotPassword`

**Parameters**:

| Parameter  | Type   | Description                |
|------------|--------|----------------------------|
| Email      | string | Email Id/Username (Required)|

---


## Check Users API
## Get All Departments

To retrieve all departments related to a particular hospital, make a POST request to the following API endpoint:

**API Method**: `POST`
**URL**: `baseurl/api/Admin/GetAllDepartments`

### Parameters:

- **HospitalId**: Required
  - Type: Integer
  - Description: Unique identifier for the hospital.

You can obtain the hospital ID by using the hospital API.

---

## Get Wards By Department

To get all the wards related to a particular department and hospital, use the following API endpoint:

**API Method**: `POST`
**URL**: `baseurl/api/Admin/GetWardsByDepartment`

### Parameters:

1. **HospitalId**: Required
   - Data Type: Integer
   - Description: Unique identifier for the hospital.

2. **DepartmentId**: Required
   - Data Type: Integer
   - Description: Unique identifier for the department.

You can obtain the hospital ID and department ID by using the relevant APIs.

---

## Get Designations By Hospital

To retrieve all designations related to a particular hospital, make a POST request to the following API endpoint:

**API Method**: `POST`
**URL**: `baseurl/api/Admin/GetDesignationByHospital`

### Parameters:

- **HospitalId**: Required
  - Data Type: Integer
  - Description: Unique identifier for the hospital.



### JML Leaving Process

#### Joining

When a nurse joins your organization and their details are captured in your HR system, you can follow this process to create the nurse automatically in Triton.

- **API Url**: `POST api/Admin/CreateUser`

**Parameters**:

| Parameter | Details                                   |
|-----------|-------------------------------------------|
| UserName  | Required, Data Type: String               |
| Password  | Required, Data Type: Password             |
| RoleId    | Required, Data Type: Integer (4 for general user/nurse) |
| HospitalId| Required, Data Type: Integer              |
| EmailId   | Required, Data Type: Email Id             |


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
  "Email": "sample string 9",
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
---
### Update Plan

**Endpoint**: `PUT /api/Plan/UpdatePlan`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Plan/UpdatePlan`

**Parameters**:

| Parameter              | Type    | Description                        |
|------------------------|---------|------------------------------------|
| PlanningId             | int     | Required                           |
| PlanningHistoryId      | int     | Required                           |
| ModifiedBy             | int     | UserId of modified User (Required) |
| DepartmentId           | int     | Unique Id                          |
| WardId                 | int     | Unique Id                          |
| TotalBeds              | int     | Number                             |
| StandardAcquity        | int     | Number                             |
| RegisteredNurse        | int     | Number                             |
| EnrolledNurse          | int     | Number                             |
| EnrolledNurseAuxillary | int     | Number                             |
| DependencyCategory1    | int     | Number                             |
| DependencyCategory2    | int     | Number                             |
| DependencyCategory3    | int     | Number                             |
| DependencyCategory4    | int     | Number                             |
| DayShift               | int     | Number                             |
| NightShift             | int     | Number                             |
| TargetCostPerDay       | string  | String                             |
| PlanForDate            | DateTime| Specify date for the particular plan|
| IsRoundUpDown          | bool    | Optional                           |
| RoundUp                | decimal | Decimal Number                     |
| RoundDown              | decimal | Decimal Number                     |
| MinimumSuggestedStaff  | int     | Integer                            |

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
  "Email": "sample string 9",
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
---
## Off-duties / Duty Roster

To manage off-duties or duty roster, you need to call the following API with the requested parameters:

**API Endpoint**: `POST api/Roaster/CreateNurseShift`

### Parameters:

1. **EmployeeNumber**: Required
2. **DepartmentId**: Required (Data Type: Integer)
3. **ShiftMasterId**: Required (Data Type: Integer)
4. **ShiftDate**: Required (DateTime Format: mm/dd/yyyy)
5. **CreatedBy**: Required (Value: 1 for admin HR system)

To get the `ShiftMasterId`, use the following enum class:

- For "Day" shift, use 1.

### Sample Request:

```json
[
  {
    "$id": "1",
    "UserId": 1,
    "DepartmentId": 2,
    "ShiftMasterId": 3,
    "ShiftDate": "2024-05-26T09:55:48.0096806+00:00",
    "CreatedBy": 4,
    "ShiftId": "sample string 5"
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

**API Url**: `POST api/Roaster/ClockIn`

### Parameters

1. **EmployeeNumber**: Required
2. **DepartmentId**: Required (Data Type: Integer)
3. **ClockInDate**: Required (DateTime Format: dd/mm/yyyy)

Request the following information regarding an employee's punch-in activity in your offline system:
- Employee Number: [Insert Employee Number]
- Department: [Insert Department]
- Date of Punch-In: [Insert Date]
 -->
