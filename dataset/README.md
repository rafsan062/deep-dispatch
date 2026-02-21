# NYC Yellow Taxi Trip Dataset

## About Dataset

### Context

New York City (NYC) Taxi & Limousine Commission (TLC) keeps data from all its cabs, and it is freely available to download from its official website. The TLC primarily keeps and manages data for 4 different types of vehicles:

*   **Yellow Taxi:** Yellow Medallion Taxicabs: These are the famous NYC yellow taxis that provide transportation exclusively through street hails. The number of taxicabs is limited by a finite number of medallions issued by the TLC. You access this mode of transportation by standing in the street and hailing an available taxi with your hand. The pickups are not pre-arranged.
*   **Green Taxi:** Street Hail Livery: The SHL program will allow livery vehicle owners to license and outfit their vehicles with green borough taxi branding, meters, credit card machines, and ultimately the right to accept street hails in addition to pre-arranged rides.
*   **For-Hire Vehicles (FHVs):** FHV transportation is accessed by a pre-arrangement with a dispatcher or limo company. These FHVs are not permitted to pick up passengers via street hails, as those rides are not considered pre-arranged.

### Important Points

*   In this dataset, we are considering **only the Yellow Taxis Data**, for the months of Jan 2015 & Jan-Mar 2016.
*   If you go over to the website of NYC TLC and download any of the CSV files today, you will find a different format. This is because the TLC regularly adds more data alongside updating the existing ones.
*   One of the key changes they have made to their data is that instead of providing the pickup & dropoff coordinates, they have divided NYC into regions and indexed those regions. In the recent CSV files, they provide these indices.
*   Due to this reason, this dataset uses an older version of the CSV files that still contains the exact coordinates. This makes it suitable for practicing clustering alongside time-series analysis. (If you want to leave out the clustering part, you can download the newer datasets from their website).

## Available Files

The dataset includes the following CSV files, covering data from Jan 2015 and Jan-Mar 2016:

- `yellow_tripdata_2015-01.csv` (~1.98 GB)
- `yellow_tripdata_2016-01.csv` (~1.71 GB)
- `yellow_tripdata_2016-02.csv` (~1.78 GB)
- `yellow_tripdata_2016-03.csv` (~1.91 GB)

## Dataset Dictionary & Feature Descriptions

**Total Records:** ~47 Million Rows (Combined)  

### **Trip Metadata**
| Field Name | Type | Description | Key / Notes |
| :--- | :--- | :--- | :--- |
| **VendorID** | Categorical | TPEP provider that provided the record. | `1` = Creative Mobile Technologies<br>`2` = VeriFone Inc. |
| **tpep_pickup_datetime** | DateTime | The date and time when the meter was engaged. | Start of the trip. |
| **tpep_dropoff_datetime** | DateTime | The date and time when the meter was disengaged. | End of the trip. |
| **store_and_fwd_flag** | Categorical | Whether the trip record was held in vehicle memory before sending to the vendor. | `Y` = store and forward<br>`N` = not a store and forward trip |
| **RateCodeID** | Categorical | The final rate code in effect at the end of the trip. | `1`= Standard rate, `2`=JFK, `3`=Newark<br>`4`=Nassau/Westchester, `5`=Negotiated, `6`=Group ride |

### **Location & Movement**
| Field Name | Type | Description | Notes |
| :--- | :--- | :--- | :--- |
| **passenger_count** | Integer | The number of passengers in the vehicle. | **Note:** This is a driver-entered value. |
| **trip_distance** | Float | The elapsed trip distance in miles reported by the taximeter. | |
| **pickup_longitude** | Float | Longitude where the meter was engaged. | |
| **pickup_latitude** | Float | Latitude where the meter was engaged. | |
| **dropoff_longitude** | Float | Longitude where the meter was disengaged. | |
| **dropoff_latitude** | Float | Latitude where the meter was disengaged. | |

### **Financials & Payment**
| Field Name | Type | Description | Key / Notes |
| :--- | :--- | :--- | :--- |
| **payment_type** | Categorical | How the passenger paid for the trip. | `1`= Credit card, `2`= Cash, `3`= No charge<br>`4`= Dispute, `5`= Unknown, `6`= Voided trip |
| **fare_amount** | Float | The time-and-distance fare calculated by the meter. | Does not include surcharges or tax. |
| **extra** | Float | Miscellaneous extras and surcharges. | Usually $0.50 or $1.00 for rush hour/overnight. |
| **mta_tax** | Float | $0.50 MTA tax automatically triggered based on the metered rate. | |
| **improvement_surcharge** | Float | $0.30 improvement surcharge assessed at flag drop. | |
| **tip_amount** | Float | Tip amount. | **Important:** Automatically populated for **Credit Cards only**. Cash tips are not included (usually 0). |
| **tolls_amount** | Float | Total amount of all tolls paid in trip. | |
| **total_amount** | Float | The total amount charged to passengers. | Does not include cash tips. |

## Usage Note

The datasets in this directory are quite large, totaling over 7 GB uncompressed. Consider the following when interacting with these files:
* Processing all of them simultaneously in memory might require an environment with sufficient RAM.
