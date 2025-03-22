# API Automation Testing

## Overview
This repository contains a Postman collection for automating API tests. The collection includes various API requests for searching products, managing the shopping cart, and performing automated validation using Postman scripts.

## Prerequisites
- [Postman](https://www.postman.com/downloads/)
- A valid internet connection

## Installation
1. Clone this repository:
   ```sh
   git clone https://github.com/yourusername/API_Automation.git
   ```
2. Open Postman and import the `API_Automation.postman_collection.json` file.

## Collection Details
This collection contains the following requests:

1. **Search Product**  
   - Method: `GET`  
   - URL: `{{baseURL}}/search?keyword={{searchText}}&ajax=true`  
   - Purpose: Searches for a product using the keyword.
   - Automated Tests:
     - Verifies the response status code is 200.
     - Checks if the response body contains the expected product name.
     - Stores product details in collection variables.

2. **View Cart (Before Adding Product)**  
   - Method: `GET`  
   - URL: `{{baseURL}}/cart?ajax=true`  
   - Purpose: Retrieves the current cart status before adding a product.
   - Automated Tests:
     - Stores previous cart quantity for comparison.
     - Verifies the response status code is 200.

3. **Add Product to Cart**  
   - Method: `POST`  
   - URL: `{{baseURL}}/api/cart/mine/items`  
   - Body:
     ```json
     {
       "sku": "{{selected_sku}}",
       "qty": "{{selected_qty}}"
     }
     ```  
   - Purpose: Adds a selected product to the cart.
   - Automated Tests:
     - Verifies the response status code is 200.
     - Confirms that the correct product SKU is added.
     - Checks if the quantity matches the expected value.

4. **View Cart (After Adding Product)**  
   - Method: `GET`  
   - URL: `{{baseURL}}/cart?ajax=true`  
   - Purpose: Retrieves cart details after adding a product.
   - Automated Tests:
     - Confirms that the cart quantity updates correctly.

5. **Remove Product from Cart**  
   - Method: `DELETE`  
   - URL: `{{baseURL}}/api/cart/{cart_id}/items/{item_id}`  
   - Purpose: Removes a specific item from the cart.

## Environment Variables
The collection uses the following variables:
- `baseURL`: `https://demo.evershop.io/`
- `searchText`: Search keyword for the product.
- `productname`: Stores the product name from search results.
- `items`: Stores the list of items retrieved from the search.
- `selected_sku`: Stores the SKU of the selected product.
- `selected_qty`: Stores the quantity of the selected product.
- `prev_qty`: Stores the previous cart quantity before adding a new item.

## Running Tests
1. Open Postman and navigate to the **API Automation Testing** collection.
2. Select a request and click **Send** to execute.
3. Observe the response data to verify expected results.
4. Run the full collection using **Collection Runner** in Postman to execute all test cases automatically.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

