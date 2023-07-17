# DoWell-Permutation
Welcome to the Permutation API! The Permutation API is a comprehensive tool that enables users to generate permutations of a set of items efficiently. It provides a reliable and high-performance solution for permutation calculations, making it ideal for a wide range of applications such as combinatorial optimization, data analysis, and algorithm design.

## Features

The Permutation API offers the following key features:

- ```Total Number of Permutations Possible``` : this feature calculates the precise count of all the potential permutations based on the provided values of ```'n'``` and ```'r'```. 
- ```Exact Permutations``` : this feature allows users to find the precise permutations for any given range of ```'n'``` and ```'r'```. This feature utilizes a specially designed algorithm that ensures accurate and efficient permutation generation.

```Note``` : ```'n'``` is total number of items present and ```'r'``` is the total number of items to be selected from ```'r'```.

## Getting Started

To get started with the Permutation API, follow these steps:

1. Review the [API Documentation](https://documenter.getpostman.com/view/27523601/2s946e9D1K) to understand the available endpoints, request parameters, and response formats.

2. Make API requests to calculate the total number of permutations possible and to find the exact permutations by providing the ```'n'``` , ```'r'``` , and the exact values for each item.

3. Permutation API has 2 endpoints that are ```find``` and ```save```. The urls for both the endpoints are:
    - find : `https://100050.pythonanywhere.com/permutation/V2/find/<your-api-key>/`
    - save : `https://100050.pythonanywhere.com/permutation/V2/save/<your-api-key>/`

4. Both the endpoints are neccessary for generating the desired permutations. The ```find``` endpoint is used to find permutation for the available variables, the ```save``` endpoint is used to select permutations for the next step. 

5. Analyze the returned results, including the number of permutations and the final permutation.

- **Note** : Both the endpoints should always be used for generating the permutations .

## Example

Here is an example to demonstrate use the Permutation API, for the example we will be using ```n``` as 5 and ```r``` as 3:

1. ```Inserting the first variable``` - use the ```find``` endpoint for inserting the first variable to the permutations function with the following request data.

    ```Request```
    ```json
    {
        "inserted_id": "",
        "nextVariable":"A",
        "n":5,
        "r":3
    }
    ```
    ```Response```
    ```json
    {
    "n": 5,
    "r": 3,
    "numberOfPermutations": 60,
    "permutationsVariables": [
        "A"
    ],
    "success": true,
    "inserted_id": "64afb77be6f563a2b08ab7d4"
    }
    ```

2. ```Saving the first variable``` - use the ```save``` endpoint for saving the first variable to the permutations function with the following request data.

    ```Request```
    ```json
    {
        "inserted_id":"64afb77be6f563a2b08ab7d4",
        "selectedPermutation":    [
            "A"
        ]
    }
    ```
    ```Response```
    ```json
    {
    "message": "Selected permutation ['A'] is saved successfully.",
    "success": true
    }
    ```

3. ```Inserting the second variable``` - this step is similar to the first step where we inserted the first variable, the only difference would be in the request data. This time we have the ```inserted_id``` so we will send it's value with the request data.

    ```Request```
    ```json
    {
        "inserted_id": "64afb77be6f563a2b08ab7d4",
        "nextVariable":"B",
        "n":5,
        "r":3
    }
    ```
    ```Response```
    ```json
    {
        "n": 5,
        "r": 3,
        "numberOfPermutations": 60,
        "permutationsVariables": [
            [
                "B",
                "A"
            ],
            [
                "A",
                "B"
            ]
        ],
        "inserted_id": "64afb77be6f563a2b08ab7d4",
        "success": true
    }
    ```

4. ```Selecting and saving the permutation``` - now we need to select one permuation from the ```permutationsVariables``` and save it for the next steps using the ```save``` endpoint.

    ```Request```
    ```json
    {
        "inserted_id":"64afb77be6f563a2b08ab7d4",
        "selectedPermutation":    [
                "B",
                "A"
        ]
    }
    ```
    ```Response```
    ```json
    {
        "message": "Selected permutation ['B', 'A'] is saved successfully.",
        "success": true
    }
    ```

5. We can repeat the step ```3``` and ```4``` for inserting the third variable and saving the selected permutation. After that we can finalize our permutation for getting the final results using the ```find``` endpoint with the following request data.

    ```Request```
    ```json
    {
        "inserted_id": "64afb77be6f563a2b08ab7d4",
        "nextVariable":"",
        "n":5,
        "r":3
    }
    ```
    ```Response```
    ```json
    {
        "message": "3 items are already selected, here is your final permutation ['B', 'C', 'A']",
        "n": 5,
        "r": 3,
        "numberOfPermutations": 60,
        "finalPermutation": [
            "B",
            "C",
            "A"
        ],
        "inserted_id": "64afb77be6f563a2b08ab7d4",
        "success": true
    }
    ```

## Documentation and Support

For detailed API documentation, including endpoint descriptions, request and response examples, and authentication details, please refer to the [API Documentation](https://documenter.getpostman.com/view/27523601/2s946e9D1K).

If you encounter any issues, have questions, or need assistance with the Permutation API, please contact our support team.
