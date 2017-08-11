# FailingWCFFirstRequest
Sample demonstrating how the first streamed WCF request will fail if a Global Application File exists. The sample is the 'SelfHost' WCF sample from Microsoft updated to use a web service.

## Steps to reproduce

- Set startup projects to both projects.
- Run the solution.
- A deserialization exception will occur in the client in the client.Add method.
- Move the handle to execute the client.Add method again and it will work correctly.
- Stop execution.
- Delete the Global Application File 'Global.asax'.
- Run the solution again.
- This time client.Add will not fail on first request.

Adding the Global file again and it will resume failing on each first request after the service has started. If the service is kept running it will not fail.

Removing 'Streaming' from the Web.config file will also fix the issue.
