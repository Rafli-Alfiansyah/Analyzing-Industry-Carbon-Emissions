# Analysis of Product Carbon Footprints by Industry

![pollution](https://github.com/user-attachments/assets/8afe0523-bdcd-4a52-8c4d-35fe41c98cb5)

Greenhouse gas emissions from the manufacturing and transportation of consumer products account for over 75% of global emissions. To better understand this impact, this analysis examines product carbon footprints (PCFs), which measure the total greenhouse gas emissions attributable to a product in terms of CO\<sub\>2\</sub\> equivalent.
The goal is to analyze a database of PCFs to identify which industry groups have the largest carbon footprints, based on the most recent year of available data.

## The Dataset

The analysis uses a single table, `product_emissions`, from a PostgreSQL database. This table contains product-level carbon footprint data, including the company, country, and industry group.

### `product_emissions` table schema

| field | data type |
|---|---|
| `id` | `VARCHAR` |
| `year` | `INT` |
| `product_name` | `VARCHAR` |
| `company` | `VARCHAR` |
| `country` | `VARCHAR` |
| `industry_group` | `VARCHAR` |
| `weight_kg` | `NUMERIC` |
| `carbon_footprint_pcf` | `NUMERIC` |
| `upstream_percent_total_pcf` | `VARCHAR` |
| `operations_percent_total_pcf` | `VARCHAR` |
| `downstream_percent_total_pcf` | `VARCHAR` |

## Analysis and Findings

To determine the total carbon footprint for each industry, a single SQL query was executed. The query was designed to:

1.  Filter the data to include only records from the most recent year in the dataset.
2.  Group the data by `industry_group`.
3.  For each industry, count the number of unique companies and calculate the total carbon footprint by summing the `carbon_footprint_pcf` values.
4.  Order the results to show the industries with the highest footprints first.

The analysis successfully ranked the industries by their total carbon footprint. The **Materials** industry has the largest footprint at **107,129.0 CO\<sub\>2\</sub\>e**, followed closely by **Capital Goods** at **94,942.7 CO\<sub\>2\</sub\>e**. The **Technology Hardware & Equipment** industry also has a significant footprint, while other sectors like Software and Services have a comparatively minor impact.

## Conclusion

The findings clearly indicate that heavy industries such as **Materials** and **Capital Goods** are the largest contributors to product-related carbon emissions in this dataset. This information is valuable for focusing sustainability efforts and regulations on the sectors with the greatest environmental impact.

## Tools Used

  * **SQL (PostgreSQL)**
  * **Jupyter Notebook**
