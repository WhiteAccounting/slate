# Errors

Error Code | Meaning
---------- | -------
400 | Required parameters are missing in the request.
410 | The resource has been destroyed. You are trying to get/update a resource that has been destroyed.
422 | The resource you are trying to save is not valid. This happens when the data you pass do not make any logical sense.
423 | Locked resource. Mostly happens when trying to destroy a resource that is required by another resource. See details for each type of resource for more details.
500 | Something went seriously wrong on our side. Sorry about that. We are most likely already informed that you hit a wall, but please reach out to our [support](mailto:support@white.eu.com).
