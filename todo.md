## Search component:

- Fetch data => json web server + nuxt state management hooks
- Filter by title - array.filter() + array.includes(some string)
- Print a list with every match - array.map()
- Data is visualized with a list of Single Book cards (SingleBookCard component)
- On top of the list is the number of corresponding results

### User behavior:

- User writes stuff in the search bar
- Presses ENTER
- Sees results

## Book data:

- Download all the images for books
- Find the publishing years or make up different ones

## Single book page:

- Put review stars under the book card. They correspond to the stars given in the review form (or the hard-coded ones from the json file)

## Review component:

- Title
- Subtitle
- Stars to click (maybe checkboxes)
- Review form => text field + submit button
- Submitted review POSTS to the json db => a new array with an object
