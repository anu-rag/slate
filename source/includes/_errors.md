# Errors

<!-- <aside class="notice">
This error section is stored in a separate file in <code>includes/_errors.md</code>. Slate allows you to optionally separate out your docs into many files...just save them to the <code>includes</code> folder and add them to the top of your <code>index.md</code>'s frontmatter. Files are included in the order listed.
</aside> -->

<!-- The Kittn API uses the following error codes: -->


Error Code | Meaning
---------- | -------
200 | Success. OK. -- Request has been processed successfully.
201 | Created -- Request has been fulfilled and resulted in a new resource being created.
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your API token is either invalid, expired, or inactive. For inactive users also.
403 | Forbidden -- Your API token is not allowed to perform this action.
404 | Not Found -- The specified resource could not be found.
500 | Internal Server Error -- We had a problem with our server. Try again later.