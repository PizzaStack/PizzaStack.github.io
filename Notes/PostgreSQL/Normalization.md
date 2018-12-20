# Normalization
A process in which you eliminate redundancy and maintain data integrity.

### Starting point (no normalization)
| SalesStaff |
| --- |
| EmployeeID |
| SalesPerson |
| SalesOffice |
| Age |
| DOB |
| Customer1 |
| Customer2 |
| Customer3 |

### 1st NF (Atomic values, No repeating Columns)
| SalesStaff |
| --- |
| EmployeeID |
| SalesPersonName |
| Age |
| DOB |
| SalesOfficeStreet |
| SalesOfficeCity |
| SalesOfficeState |
| SalesOfficeZip |

| Customer |
| --- |
| CustomerId |
| EmployeeId |
| CustomerName |


### 2nd NF (Remove Partial Dependencies)
| SalesStaff |
| --- |
| EmployeeID |
| SalesPersonName |
| Age |
| DOB |
| SalesOfficeID |

| SalesOffice |
| --- |
| SalesOfficeId |
| SalesOfficeStreet |
| SalesOfficeCity |
| SalesOfficeState |
| SalesOfficeZip |

| Customer |
| --- |
| CustomerId |
| EmployeeId |
| CustomerName |

### 3rd NF (Remove Transitive Dependencies)
| SalesStaff |
| --- |
| EmployeeID |
| SalesPersonName |
| DOB |
| SalesOfficeID |

| SalesOffice |
| --- |
| SalesOfficeId |
| SalesOfficeStreet |
| SalesOfficeZip |

| Customer |
| --- |
| CustomerId |
| EmployeeId |
| CustomerName |