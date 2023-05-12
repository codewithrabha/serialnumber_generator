# serialnumber_generator
This is a PHP function that sets a serial number for a post-type in WordPress. The function is triggered when a new post is inserted into the WordPress database, using the 'wp_insert_post' action.

The function first checks if the post type is 'post', which means it only works for regular blog posts. Then, it creates an array of arguments to query the database for the most recent post with a 'serial_number' custom field. The 'post__not_in' argument ensures that the current post being inserted is not included in the query.

If no posts are found in the query, the function sets the last serial number to 99. Otherwise, it retrieves the last post's serial number from the custom field and sets the last serial number to that value. If the serial number is empty, the function also sets it to 99.

Finally, the function sets the new post's serial number to the last serial number plus one, and updates the 'serial_number' custom field for the new post with this new value using the 'update_post_meta' function.

Overall, this function ensures that each new blog post is given a unique serial number, incrementing by one from the last post's serial number, starting from 100.
