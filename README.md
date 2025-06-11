# postman_chained_api_trello

This repository provides an example of a chained API workflow using Trello's REST API, demonstrated with a Postman collection. The collection showcases how to automate the creation, retrieval, manipulation, and deletion of Trello boards and lists through a sequence of dependent API calls.

## Overview

The included Postman collection (`Trello API Testing.postman_collection.json`) demonstrates a basic end-to-end workflow with the Trello API, where the output of one request is used as input for subsequent requests. This is commonly referred to as "chained" API testing.

### Workflow Steps

1. **Create Board**
    - Creates a new Trello board with a randomized name.
    - Stores the resulting Board ID as a global variable for use in later requests.

2. **Get Board**
    - Retrieves the details of the board created in the previous step using the stored Board ID.

3. **Create a List**
    - Creates a new list on the created board, with a randomized name.
    - Uses the Board ID variable to assign the list to the correct board.

4. **Delete Trello Board**
    - Deletes the board created in step 1, using the stored Board ID.

## How It Works

- **Environment Variables**: The collection uses several variables:
  - `trello_base_uri`: The base URI for Trello's API (e.g., `https://api.trello.com`).
  - `trelloauthkey`: Your Trello API key.
  - `trelloauthtoken`: Your Trello API token.
- **Chaining**: The Board ID returned on board creation is stored globally in Postman and referenced in subsequent requests.
- **Randomization**: The collection uses Postman's built-in random variables to generate random names for boards and lists.

## Requirements

- [Postman](https://www.postman.com/downloads/)
- Trello account with [API key and token](https://trello.com/app-key)
- An environment in Postman with the following variables set:
    - `trello_base_uri` (e.g., `https://api.trello.com`)
    - `trelloauthkey`
    - `trelloauthtoken`

## Usage

1. **Import the Collection**
    - Download or clone this repository.
    - Open Postman.
    - Click "Import" and select `Trello API Testing.postman_collection.json`.

2. **Set Up Environment**
    - Create a new environment in Postman.
    - Add the variables:
      - `trello_base_uri`
      - `trelloauthkey`
      - `trelloauthtoken`
    - Set their values according to your Trello account and API credentials.

3. **Run the Collection**
    - Select the environment you created.
    - Run each request in order, or use the "Runner" to execute the entire collection as a sequence.

4. **Observe Chaining**
    - The `Create Board` request sets a global variable `BoardID` that is then used by subsequent requests (`Get Board`, `Create a List`, `Delete Trello Board`).

## Collection Structure

- `Create Board`  
  Creates a new board and saves its ID as `BoardID`.
- `Get Board`  
  Reads the details of the created board using `BoardID`.
- `Create a List`  
  Adds a new list to the board using `BoardID`.
- `Delete Trello Board`  
  Cleans up by deleting the board using `BoardID`.

## Notes

- This collection is intended for demonstration and testing purposes.
- Ensure you do not exceed Trello's API rate limits.
- Deleting a board is irreversible. Use with caution.

## License

This repository is provided as-is for educational purposes.

