## Review component:

- Enable rating books

## Single book page:

- Update rating stars to match the actual reviews

## Review component:

- Hide the "Customer reviews" title, if there are no reviews

### Existing stars:

- 5 separate star images
- Convert them to svg
- Retrieve the fill value (pass as a prop)
- If a star was clicked, it is filled

### Stars to click:

- Click x number of stars. This is saved in a variable
- When the user submits the review:
- A PUT request is sent to db with the new rating value.
- The existing rating is updated with the new value
