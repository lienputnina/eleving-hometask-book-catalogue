## Author's note

I've tried my best to implement all the desired features.
Unfortunately, did not manage to do everything.
Things like full responsiveness and the rating option, sadly, did not make the cut.

## Overview

A Book Catalogue app. Here you can browse books searching by title.
The landing page has a search bar that provides a list of corresponding titles. When choose a book from the list, you are directed to a more detailed book view, where you can leave a review in a text form.

## Usage

### Disclaimer

- The rating stars are not functional as the rating option has not been implemented
- To see the updated review list on the UI, reload the page
- The reviews are sent to the database, appending the book objects with a new array

There is no production mode for now.

To run the app in the development mode, run:

```shell
yarn dev
```

To run the database, run:

```shell
yarn backend
```
