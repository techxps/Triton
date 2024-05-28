## Triton
---
## Table of Contents

1. [API Authentication](#api-authentication)
2. [User Management](#user-management)
   - [Check Users API](#check-users-api)
   - [Forgot Password](#forgot-password)
3. [Plan Management](#plan-management)
   - [Create Plan](#create-plan)
   - [Get Plan](#get-plan)
   - [Update Plan](#update-plan)
   - [Get Plans](#get-plans)
   - [Get Staff List](#get-staff-list)
   - [Create Approved Plan](#create-approved-plan)
4. [Shift Management](#shift-management)
   - [Create Shift](#create-shift)
   - [Get Shift](#get-shift)
   - [Update Shift](#update-shift)
5. [Surveillance](#surveillance)
6. [Bed Management](#bed-management)
   - [Save Bed](#save-bed)
   - [Update Bed](#update-bed)
   - [Get All Beds](#get-all-beds)
   - [Get Bed By Id](#get-bed-by-id)
   - [Get Beds By Ward](#get-beds-by-ward)

---

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

## Plan Management

### Create Plan

**Endpoint**: `POST /api/Plan/CreatePlan`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Plan/CreatePlan`

**Parameters**:

| Parameter              | Type    | Description                        |
|------------------------|---------|------------------------------------|
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

### Get Plan

**Endpoint**: `GET /api/Plan/GetPlan`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Plan/GetPlan`

**Parameters**:

| Parameter         | Type   | Description                 |
|-------------------|--------|-----------------------------|
| PlanningHistoryId | int    | Mandatory                    |
| UserId            | int    | UniqueId of Particular User  |

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

### Get Plans

**Endpoint**: `GET /api/Plan/GetPlans`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Plan/GetPlans`

**Parameters**:

| Parameter    | Type   | Description                         |
|--------------|--------|-------------------------------------|
| DepartmentId | int    | Mandatory                           |
| WardId       | int    | UniqueId of Particular Ward (Required) |
| HospitalId   | int    | UniqueId of Particular Hospital (Required) |

---

### Get Staff List

**Endpoint**: `GET /api/Plan/GetStaffList`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Plan/GetStaffList`

**Parameters**:

| Parameter    | Type   | Description                         |
|--------------|--------|-------------------------------------|
| DepartmentId | int    | Mandatory                           |
| WardId       | int    | UniqueId of Particular Ward (Required) |
| PlanForDate  | DateTime| ShiftPlan (Required)                |

---

### Create Approved Plan

**Endpoint**: `POST /api/Plan/CreatePlanApproval`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Plan/CreatePlanApproval`

**Body Parameters**:

| Parameter                  | Type    | Description                |
|----------------------------|---------|----------------------------|
| CreatedBy                  | int     | Required                   |
| PlanList                   | array   | Collection of PlanUserModel|
| STD1                       | string  | None                       |
| STD2                       | string  | None                       |
| STD3                       | string  | None                       |
| STD4                       | string  | None                       |
| Acuity1Ns                  | string  | None                       |
| Acuity2Ns                  | string  | None                       |
| Acuity3Ns                  | string  | None                       |
| Acuity4Ns                  | string  | None                       |
| Acuity1Ds                  | string  | None                       |
| Acuity2Ds                  | string  | None                       |
| Acuity3Ds                  | string  | None                       |
| Acuity4Ds                  | string  | None                       |
| FTE1Ns                     | string  | None                       |
| FTE2Ns                     | string  | None                       |
| FTE3Ns                     | string  | None                       |
| FTE4Ns                     | string  | None                       |
| TotalFTENs                 | string  | None                       |
| FTE1Ds                     | string  | None                       |
| FTE2Ds                     | string  | None                       |
| FTE3Ds                     | string  | None                       |
| FTE4Ds                     | string  | None                       |
| TotalFTEDs                 | string  | None                       |
| DSDependencyCategory1Ns    | string  | None                       |
| DSDependencyCategory2Ns    | string  | None                       |
| DSDependencyCategory3Ns    | string  | None                       |
| DSDependencyCategory4Ns    | string  | None                       |
| DSDependencyCategory1Ds    | string  | None                       |
| DSDependencyCategory2Ds    | string  | None                       |
| DSDependencyCategory3Ds    | string  | None                       |
| DSDependencyCategory4Ds    | string  | None                       |
| TotalPPD                   | string  | None                       |
| ActualPPD                  | string  | None                       |
| PPDVariance                | string  | None                       |
| TotalBedsNs                | string  | None                       |
| AvailableBedsNs            | string  | None                       |
| PercentAvailableBedsNs     | string  | None                       |
| TotalBedsDs                | string  | None                       |
| AvailableBedsDs            | string  | None                       |
| PercentAvailableBedsDs     | string  | None                       |
| STDANs                     | string  | None                       |
| PGANs                      | string  | None                       |
| VarianceSTDNs              | string  | None                       |
| STDADs                     | string  | None                       |
| PGADs                      | string  | None                       |
| VarianceSTDDs              | string  | None                       |
| StandardAcquityNs          | string  | None                       |
| PatientGradedAcuityNs      | string  | None                       |
| VariancetoStandardAcuityNs | string  | None                       |
| WorkedAcuityNs             | string  | None                       |
| TotalOccupancyNs           | string  | None                       |
| StandardAcquityDs          | string  | None                       |
| PatientGradedAcuityDs      | string  | None                       |
| VariancetoStandardAcuityDs | string  | None                       |
| WorkedAcuityDs             | string  | None                       |
| TotalOccupancyDs           | string  | None                       |
| TargetPPDNs                | string  | None                       |
| PPDCostNs                  | string  | None                       |
| PPDVarianceNs              | string  | None                       |
| AbsenteeismHoursNs         | string  | None                       |
| TargetPPDDs                | string  | None                       |
| PPDCostDs                  | string  | None                       |
| PPDVarianceDs              | string  | None                       |
| AbsenteeismHoursDs         | string  | None                       |
| ProposedNursingHrsNs       | string  | None                       |
| PlannedNursingHrsNs        | string  | None                       |
| VariancetoProposedHrsNs    | string  | None                       |
| ProposedNursingHrsDs       | string  | None                       |
| PlannedNursingHrsDs        | string  | None                       |
| VariancetoProposedHrsDs    | string  | None                       |
| StandardSkillMixRNNs       | string  | None                       |
| StandardSkillMixENNs       | string  | None                       |
| StandardSkillMixENANs      | string  | None                       |
| StandardSkillMixTotalNs    | string  | None                       |
| NursesProposedRNNs         | string  | None                       |
| NursesProposedENNs         | string  | None                       |
| NursesProposedENANs        | string  | None                       |
| NursesProposedTotalNs      | string  | None                       |
| NursingHoursProposedRNNs   | string  | None                       |
| NursingHoursProposedENNs   | string  | None                       |
| NursingHoursProposedENANs  | string  | None                       |
| NursingHoursProposedTotalNs| string  | None                       |
| PlannedSkillMixRNNs        | string  | None                       |
| PlannedSkillMixENNs        | string  | None                       |
| PlannedSkillMixENANs       | string  | None                       |
| PlannedSkillMixTotalNs     | string  | None                       |
| StandardSkillMixRNDs       | string  | None                       |
| StandardSkillMixENDs       | string  | None                       |
| StandardSkillMixENADs      | string  | None                       |
| StandardSkillMixTotalDs    | string  | None                       |
| NursesProposedRNDs         | string  | None                       |
| NursesProposedENDs         | string  | None                       |
| NursesProposedENADs        | string  | None                       |
| NursesProposedTotalDs      | string  | None                       |
| NursingHoursProposedRNDs   | string  | None                       |
| NursingHoursProposedENDs   | string  | None                       |
| NursingHoursProposedENADs  | string  | None                       |
| NursingHoursProposedTotalDs| string  | None                       |
| PlannedSkillMixRNDs        | string  | None                       |
| PlannedSkillMixENDs        | string  | None                       |
| PlannedSkillMixENADs       | string  | None                       |
| PlannedSkillMixTotalDs     | string  | None                       |
| PlaningApprovalId          | int     | None                       |
| WardId                     | int     | None                       |
| DepartmentId               | int     | None                       |
| PlaningApprovalDayId       | int     | None                       |
| PlaningApprovalNightId     | int     | None                       |
| ApproverIdes               | string  | None                       |
| IsEdited                   | bool    | None                       |
| IsSaveAsDraft              | bool    | None                       |
| PlaningId                  | int     | Required                   |
| PlaningHistoryId           | int     | Required                   |
| ApproverId                 | int     | None                       |
| NightPatients              | int     | None                       |
| DayPatients                | int     | None                       |
| DayDependencyCategory1     | int     | None                       |
| DayDependencyCategory2     | int     | None                       |
| DayDependencyCategory3     | int     | None                       |
| DayDependencyCategory4     | int     | None                       |
| NightDependencyCategory1   | int     | None                       |
| NightDependencyCategory2   | int     | None                       |
| NightDependencyCategory3   | int     | None                       |
| NightDependencyCategory4   | int     | None                       |
| DependencyCategory1        | int     | None                       |
| DependencyCategory2        | int     | None                       |
| DependencyCategory3        | int     | None                       |
| DependencyCategory4        | int     | None                       |
| PlanForDate                | date    | None                       |
| PlanForDayDate             | date    | None                       |
| Remark                     | string  | None                       |

Sample:
```json
{
  "CreatedBy": 1,
  "PlanList": [
    {
      "$id": "2",
      "UserId": 1,
      "ForDate": "2024-05-19T16:44:45.1040017+00:00",
      "AssignmentType": 2,
      "WardId": 3,
      "ShiftMasterId": 1,
      "Agency": 1,
      "DesignationId": 1,
      "ActasDesignationId": 1
    },
    {
      "$ref": "2"
    }
  ],
  "STD1": "sample string 2",
  "STD2": "sample string 3",
  "STD3": "sample string 4",
  "STD4": "sample string 5",
  "Acuity1Ns": "sample string 6",
  "Acuity2Ns": "sample string 7",
  "Acuity3Ns": "sample string 8",
  "Acuity4Ns": "sample string 9",
  "Acuity1Ds": "sample string 10",
  "Acuity2Ds": "sample string 11",
  "Acuity3Ds": "sample string 12",
  "Acuity4Ds": "sample string 13",
  "FTE1Ns": "sample string 14",
  "FTE2Ns": "sample string 15",
  "FTE3Ns": "sample string 16",
  "FTE4Ns": "sample string 17",
  "TotalFTENs": "sample string 18",
  "FTE1Ds": "sample string 19",
  "FTE2Ds": "sample string 20",
  "FTE3Ds": "sample string 21",
  "FTE4Ds": "sample string 22",
  "TotalFTEDs": "sample string 23",
  "DSDependencyCategory1Ns": "sample string 24",
  "DSDependencyCategory2Ns": "sample string 25",
  "DSDependencyCategory3Ns": "sample string 26",
  "DSDependencyCategory4Ns": "sample string 27",
  "DSDependencyCategory1Ds": "sample string 28",
  "DSDependencyCategory2Ds": "sample string 29",
  "DSDependencyCategory3Ds": "sample string 30",
  "DSDependencyCategory4Ds": "sample string 31",
  "TotalPPD": "sample string 32",
  "ActualPPD": "sample string 33",
  "PPDVariance": "sample string 34",
  "TotalBedsNs": "sample string 35",
  "AvailableBedsNs": "sample string 36",
  "PercentAvailableBedsNs": "sample string 37",
  "TotalBedsDs": "sample string 38",
  "AvailableBedsDs": "sample string 39",
  "PercentAvailableBedsDs": "sample string 40",
  "STDANs": "sample string 41",
  "PGANs": "sample string 42",
  "VarianceSTDNs": "sample string 43",
  "STDADs": "sample string 44",
  "PGADs": "sample string 45",
  "VarianceSTDDs": "sample string 46",
  "StandardAcquityNs": "sample string 47",
  "PatientGradedAcuityNs": "sample string 48",
  "VariancetoStandardAcuityNs": "sample string 49",
  "WorkedAcuityNs": "sample string 50",
  "TotalOccupancyNs": "sample string 51",
  "StandardAcquityDs": "sample string 52",
  "PatientGradedAcuityDs": "sample string 53",
  "VariancetoStandardAcuityDs": "sample string 54",
  "WorkedAcuityDs": "sample string 55",
  "TotalOccupancyDs": "sample string 56",
  "TargetPPDNs": "sample string 57",
  "PPDCostNs": "sample string 58",
  "PPDVarianceNs": "sample string 59",
  "AbsenteeismHoursNs": "sample string 60",
  "TargetPPDDs": "sample string 61",
  "PPDCostDs": "sample string 62",
  "PPDVarianceDs": "sample string 63",
  "AbsenteeismHoursDs": "sample string 64",
  "ProposedNursingHrsNs": "sample string 65",
  "PlannedNursingHrsNs": "sample string 66",
  "VariancetoProposedHrsNs": "sample string 67",
  "ProposedNursingHrsDs": "sample string 68",
  "PlannedNursingHrsDs": "sample string 69",
  "VariancetoProposedHrsDs": "sample string 70",
  "StandardSkillMixRNNs": "sample string 71",
  "StandardSkillMixENNs": "sample string 72",
  "StandardSkillMixENANs": "sample string 73",
  "StandardSkillMixTotalNs": "sample string 74",
  "NursesProposedRNNs": "sample string 75",
  "NursesProposedENNs": "sample string 76",
  "NursesProposedENANs": "sample string 77",
  "NursesProposedTotalNs": "sample string 78",
  "NursingHoursProposedRNNs": "sample string 79",
  "NursingHoursProposedENNs": "sample string 80",
  "NursingHoursProposedENANs": "sample string 81",
  "NursingHoursProposedTotalNs": "sample string 82",
  "PlannedSkillMixRNNs": "sample string 83",
  "PlannedSkillMixENNs": "sample string 84",
  "PlannedSkillMixENANs": "sample string 85",
  "PlannedSkillMixTotalNs": "sample string 86",
  "StandardSkillMixRNDs": "sample string 87",
  "StandardSkillMixENDs": "sample string 88",
  "StandardSkillMixENADs": "sample string 89",
  "StandardSkillMixTotalDs": "sample string 90",
  "NursesProposedRNDs": "sample string 91",
  "NursesProposedENDs": "sample string 92",
  "NursesProposedENADs": "sample string 93",
  "NursesProposedTotalDs": "sample string 94",
  "NursingHoursProposedRNDs": "sample string 95",
  "NursingHoursProposedENDs": "sample string 96",
  "NursingHoursProposedENADs": "sample string 97",
  "NursingHoursProposedTotalDs": "sample string 98",
  "PlannedSkillMixRNDs": "sample string 99",
  "PlannedSkillMixENDs": "sample string 100",
  "PlannedSkillMixENADs": "sample string 101",
  "PlannedSkillMixTotalDs": "sample string 102",
  "PlaningApprovalId": 1,
  "WardId": 1,
  "DepartmentId": 1,
  "PlaningApprovalDayId": 1,
  "PlaningApprovalNightId": 1,
  "ApproverIdes": "sample string 103",
  "IsEdited": true,
  "IsSaveAsDraft": true,
  "PlaningId": 106,
  "PlaningHistoryId": 107,
  "ApproverId": 108,
  "NightPatients": 1,
  "DayPatients": 1,
  "DayDependencyCategory1": 1,
  "DayDependencyCategory2": 1,
  "DayDependencyCategory3": 1,
  "DayDependencyCategory4": 1,
  "NightDependencyCategory1": 1,
  "NightDependencyCategory2": 1,
  "NightDependencyCategory3": 1,
  "NightDependencyCategory4": 1,
  "DependencyCategory1": 1,
  "DependencyCategory2": 1,
  "DependencyCategory3": 1,
  "DependencyCategory4": 1,
  "PlanForDate": "2024-05-19T16:44:45.1195837+00:00",
  "PlanForDayDate": "2024-05-19T16:44:45.1195837+00:00",
  "Remark": "sample string 109"
}
```
---

### Update Plan Approval

**Endpoint**: `PUT /api/Plan/UpdatePlanApproval`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Plan/UpdatePlanApproval`

**Body Parameters**:

| Parameter              | Type    | Description                        |
|------------------------|---------|------------------------------------|
| PlaningApprovalId      | int     | Required                           |
| ModifiedBy             | int     | Required                           |
| IsApproved             | bool    | None                               |
| PlaningId              | int     | Required                           |
| PlaningHistoryId       | int     | Required                           |
| ApproverId             | int     | None                               |
| NightPatients          | int     | None                               |
| DayPatients            | int     | None                               |
| DayDependencyCategory1 | int     | None                               |
| DayDependencyCategory2 | int     | None                               |
| DayDependencyCategory3 | int     | None                               |
| DayDependencyCategory4 | int     | None                               |
| NightDependencyCategory1| int    | None                               |
| NightDependencyCategory2| int    | None                               |
| NightDependencyCategory3| int    | None                               |
| NightDependencyCategory4| int    | None                               |
| DependencyCategory1    | int     | None                               |
| DependencyCategory2    | int     | None                               |
| DependencyCategory3    | int     | None                               |
| DependencyCategory4    | int     | None                               |
| PlanForDate            | date    | None                               |
| PlanForDayDate         | date    | None                               |
| Remark                 | string  | None                               |

---

### WFI Users

**Endpoint**: `GET /api/Plan/WFIUsers`

**Body Parameters**:

| Parameter     | Type    | Description               |
|---------------|---------|---------------------------|
| ForDate       | date    | Required                  |
| Fetch         | int     | None                      |
| Offset        | int     | None                      |
| DepartmentId  | int     | None                      |
| WardId        | int     | None                      |
| RateWise      | int     | None                      |
| CreatedBy     | int     | None                      |
| ShiftType     | int     | None                      |

---

### Get History Plans

**Endpoint**: `GET /api/Plan/GetHistoryPlans`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Plan/GetHistoryPlans`

**Parameters**:

| Parameter    | Type   | Description                         |
|--------------|--------|-------------------------------------|
| DepartmentId | int    | Mandatory                           |
| WardId       | int    | UniqueId of Particular Ward (Required) |
| HospitalId   | int    | UniqueId of Particular Hospital (Required) |

---

## Shift Management

### Create Shift

**Endpoint**: `POST /api/Roaster/CreateShift`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Roaster/CreateShift`

**Parameters**:

| Parameter     | Type    | Description                       |
|---------------|---------|-----------------------------------|
| Name          | string  | Shift Name (Required)             |
| ShortName     | string  | Short Name                        |
| HospitalId    | int     | UniqueId of Particular Hospital (Required) |
| Duration      | int     | Integer (Required)                |
| ShiftDate     | DateTime| Shift Date when shift has been created in date time format (Required) |
| ShiftMasterId | int     | UniqueId of Particular Shift (Required) |
| CreatedBy     | int     | UniqueId of Particular user (Required) |
| IsActive      | bool    | Boolean  (True/False)             |

---

### Get Shift

**Endpoint**: `GET /api/Roaster/GetShift/{id}`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Roaster/GetShift/{id}`

**Parameters**:

| Parameter | Type | Description      |
|-----------|------|------------------|
| Id        | int  | Shift Id (Required) |

---

### Update Shift

**Endpoint**: `PUT /api/Roaster/UpdateShift`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Roaster/UpdateShift`

**Parameters**:

| Parameter     | Type    | Description                       |
|---------------|---------|-----------------------------------|
| Name          | string  | Shift Name (Required)             |
| ShortName     | string  | Short Name                        |
| HospitalId    | int     | UniqueId of Particular Hospital (Required) |
| Duration      | int     | Integer (Required)                |
| ShiftDate     | DateTime| Shift Date when shift has been created in date time format (Required) |
| ShiftMasterId | int     | UniqueId of Particular Shift (Required) |
| CreatedBy     | int     | UniqueId of Particular user (Required) |
| IsActive      | bool    | Boolean  (True/False)             |

---

### Get Shift Details by Hospital

**Endpoint**: `GET /api/Roaster/GetShiftByHospital`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Roaster/GetShiftByHospital`

**Parameters**:

| Parameter  | Type | Description       |
|------------|------|-------------------|
| HospitalId | int  | Hospital Id (Required) |

---

### Create User Shift

**Endpoint**: `POST /api/Roaster/CreateUserShift`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Roaster/CreateUserShift`

**Parameters**:

| Parameter     | Type    | Description                     |
|---------------|---------|---------------------------------|
| UserId        | int     | UserId (Required)               |
| DepartmentId  | int     | DepartmentId (Required)         |
| ShiftMasterId | int     | ShiftmasterId (Required)        |
| ShiftDate     | DateTime| Date of particular shift (Required) |

---

### Update User Shift

**Endpoint**: `PUT /api/Roaster/UpdateUserShift`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Roaster/UpdateUserShift`

**Parameters**:

| Parameter     | Type    | Description                       |
|---------------|---------|-----------------------------------|
| Name          | string  | Shift Name (Required)             |
| ShortName     | string  | Short Name                        |
| HospitalId    | int     | UniqueId of Particular Hospital (Required) |
| Duration      | int     | Integer (Required)                |
| ShiftDate     | DateTime| Shift Date when shift has been created in date time format (Required) |
| ShiftMasterId | int     | UniqueId of Particular Shift (Required) |
| CreatedBy     | int     | UniqueId of Particular user (Required) |
| IsActive      | bool    | Boolean  (True/False)             |

---

### Create User Availability

**Endpoint**: `POST /api/Roaster/CreateUserAvailability`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Roaster/CreateUserAvailability`

**Parameters**:

| Parameter     | Type    | Description                     |
|---------------|---------|---------------------------------|
| UserId        | int     | UserId (Required)               |
| CreatedBy     | int     | UserId (Required)               |
| ShiftMasterId | int     | ShiftmasterId (Required)        |
| ForDate       | DateTime| Date of particular shift (Required) |

---

### Update User Availability

**Endpoint**: `PUT /api/Roaster/UpdateUserAvailability`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Roaster/UpdateUserAvailability`

**Parameters**:

| Parameter         | Type    | Description                     |
|-------------------|---------|---------------------------------|
| UserAvailabilityId| int     | UserId (Required)               |
| ModifiedBy        | int     | UserId (Required)               |
| ShiftMasterId     | int     | ShiftmasterId (Required)        |
| ForDate           | DateTime| Date of particular shift (Required) |
| UserId            | int     | UserId (Required)               |

---

### Approve User Availability

**Endpoint**: `POST /api/Roaster/ApproveUserAvailability`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Roaster/ApproveUserAvailability`

**Parameters**:

| Parameter         | Type    | Description                     |
|-------------------|---------|---------------------------------|
| UserAvailabilityId| int     | UserId (Required)               |
| ModifiedBy        | int     | UserId (Required)               |
| ShiftMasterId     | int     | ShiftmasterId (Required)        |
| ApprovedDate      | DateTime| Date of Approval (Required)     |
| UserId            | int     | UserId (Required)               |
| ApprovedBy        | int     | UserId (Required)               |
| IsApproved        | bool    | Boolean True/False              |
| UserId            | int     | UserId (Required)               |

---

## Surveillance

### Get Plan Approval User

**Endpoint**: `GET /api/Surveillance/GetPlanApprovalUser`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Surveillance/GetPlanApprovalUser`

**Parameters**:

| Parameter     | Type    | Description
|---------------|---------|--------------------------------|
| HospitalId    | int     | HospitalId (Required)          |
| DepartmentId  | int     | DepartmentId (Required)        |
| WardId        | int     | ShiftmasterId (Required)       |
| PlanForDate   | DateTime| Date of Plan (Required)        |

---

### Save Surveillance

**Endpoint**: `POST /api/Surveillance/SaveSurveillance`

**Body Parameters**:

| Parameter                   | Type    | Description                         |
|-----------------------------|---------|-------------------------------------|
| GetPlanApprovalUserList     | array   | Collection of GetPlanApprovalUserList|
| SurveillanceExtraStaffList  | array   | Collection of SurveillanceExtraStaffModel |
| PatientChangesModel         | object  | PatientChangesModel                 |

---

### Surveillance Send Approval

**Endpoint**: `POST /api/Surveillance/SurveillanceSendApproval`

**Body Parameters**:

| Parameter                   | Type    | Description                         |
|-----------------------------|---------|-------------------------------------|
| PlanningApprovalId          | int     | None                                |
| UserId                      | int     | None                                |
| Username                    | string  | None                                |
| Designation                 | string  | None                                |
| Type                        | string  | None                                |
| Hrs                         | int     | None                                |
| Status                      | array   | Collection of string                |
| Allocation                  | array   | Collection of string                |
| Resus                       | array   | Collection of string                |
| AdditionalTask              | array   | Collection of string                |
| Disaster                    | array   | Collection of string                |
| TotalRecords                | int     | None                                |
| SurveillanceUserApprovedStatus | string| None                                |
| IsSurveillanceSentForApproval | bool  | None                                |
| SurveillanceRemarks         | string  | None                                |
| CreatedBy                   | int     | None                                |
| PlanningId                  | int     | None                                |
| RemarkPlanner               | string  | None                                |
| TotalBeds                   | int     | None                                |
| StandardAcquity             | int     | None                                |
| RegisteredNurse             | int     | None                                |
| EnrolledNurse               | int     | None                                |
| EnrolledNurseAuxillary      | int     | None                                |
| DependencyCategory1         | int     | None                                |
| DependencyCategory2         | int     | None                                |
| DependencyCategory3         | int     | None                                |
| DependencyCategory4         | int     | None                                |
| DayDependencyCategory1      | int     | None                                |
| DayDependencyCategory2      | int     | None                                |
| DayDependencyCategory3      | int     | None                                |
| DayDependencyCategory4      | int     | None                                |
| NightDependencyCategory1    | int     | None                                |
| NightDependencyCategory2    | int     | None                                |
| NightDependencyCategory3    | int     | None                                |
| NightDependencyCategory4    | int     | None                                |
| DayShift                    | int     | None                                |
| NightShift                  | int     | None                                |
| TargetCostPerDay            | decimal | None                                |
| AgencyCount                 | int     | None                                |
| ShiftName                   | string  | None                                |
| ShiftType                   | string  | None                                |
| CustomId                    | int     | None                                |
| WardId                      | int     | None                                |
| OtherAdditionalTask         | string  | None                                |
| IsOtherAdditional           | bool    | None                                |
| WorkShiftPlanningId         | string  | None                                |

---

### Get Users by Surveillance

**Endpoint**: `GET /api/Surveillance/GetUserSurveillance`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Surveillance/GetUserSurveillance`

**Parameters**:

| Parameter   | Type | Description                     |
|-------------|------|---------------------------------|
| HospitalId  | int  | Hospital Id (Required)          |
| UserId      | int  | User Id (Required)              |
| ForDate     | date | Date of surveillance approval   |

---

### Get Assign Staff by Planning Approval Id

**Endpoint**: `GET /api/Surveillance/GetJitAssignStaffbyPlanningApprovalId/{id}`

**Parameters**:

| Parameter | Type | Description     |
|-----------|------|-----------------|
| Id        | int  | Approval Id (Required) |

---

## Bed Management

### Save Bed

**Endpoint**: `POST /api/Beds/SaveBed`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Beds/SaveBed`

**Parameters**:

| Parameter   | Type   | Description       |
|-------------|--------|-------------------|
| BedId       | int    | BedId             |
| BedName     | string | Bed Name (Required) |
| HospitalId  | int    | HospitalId (Optional) |
| WardId      | int    | Ward Id           |
| DepartmentId| int    | Department Id     |

---

### Update Bed

**Endpoint**: `PUT /api/Beds/UpdateBed`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Beds/UpdateBed`

**Parameters**:

| Parameter   | Type   | Description       |
|-------------|--------|-------------------|
| BedId       | int    | BedId             |
| BedName     | string | Bed Name (Required) |
| HospitalId  | int    | HospitalId (Optional) |
| WardId      | int    | Ward Id           |
| DepartmentId| int    | Department Id     |

---

### Get All Beds

**Endpoint**: `GET /api/Beds/GetAllBeds`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Beds/GetAllBeds`

**Parameters**:

| Parameter   | Type   | Description       |
|-------------|--------|-------------------|
| BedId       | int    | BedId             |
| BedName     | string | Bed Name (Required) |
| HospitalId  | int    | HospitalId (Optional) |
| WardId      | int    | Ward Id           |
| DepartmentId| int    | Department Id     |

---

### Get Bed By Id

**Endpoint**: `GET /api/Beds/GetBedsById`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Beds/GetBedsById`

**Parameters**:

| Parameter | Type | Description   |
|-----------|------|---------------|
| Id        | int  | BedId         |

---

### Active/ Deactivate Beds

**Endpoint**: `PUT /api/Beds/ActiveDeactivateBeds`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Beds/ActiveDeactivateBeds`

**Parameters**:

| Parameter | Type | Description           |
|-----------|------|-----------------------|
| BedId     | int  | BedId                 |
| IsActive  | bool | Boolean (True/False)  |
| ModifiedBy| int  | UserId                |

---

### Get Beds By Wards

**Endpoint**: `GET /api/Beds/GetBedsByWard`

**URL**: `https://tritonlenmedapi.converge-solutions.com/api/Beds/GetBedsByWard`

**Parameters**:

| Parameter    | Type | Description        |
|--------------|------|--------------------|
| HospitalId   | int  | Hospital Id        |
| DepartmentId | int  | Department Id      |
| WardId       | int  | Ward Id            |
