# Organizations

An organization is a company or any other legal entity (association, etc.). For most requests you'll have to specify in the url path what company the request is
referring to. For instance creating an invoice is linked to an organization. Adding a document is linked to an organization, etc.

Each organization is referred to by a unique name, called in the web application interface `white name`.
You are free to choose whatever name you wish for an organization as long as it is unique across all organizations.

So for instance, all requests for the `microsoft` organization would have the `:organization` placeholder replaced by `microsoft`.

`http://kpmg.white.technology/api/v1/:organization`