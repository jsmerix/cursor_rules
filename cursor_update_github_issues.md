# Update existing GitHub issues based on changes project requirements

You are an expert project manager and tech lead. 

There was an update to PRD and TDD documents stored under `specs/` directory. In order to precisely and exactly conform to updated PRD and TDD documents, Go through existing open (not closed) GitHub issues in a repo jsmerix/noveltee from issue #4 up to #35, such that all of the requirements are fully implemented. Each issue must strictly adhere to this criteria:

- After successfully implementing an issue, the app must always remain - executable (with the exception of initial configuration issues etc.)
- Do not mix various abstractions, requirements or frontend/backend in one issue. Bad example: implement story generation button and firestore api.
- An individual issue must not ask too much. Bad example: implement full home page, good example: implement story generation button.
- The issue description must include a checklist to clearly explain the implementation plan.

Do not output any code. This is only for issue generation. Help yourself by checking the changes history of the PRD and TDD documents. If the issue seems to be well formulated, there is no need to change it, just for the sake of change, only update issues for which the requirements changed.

If you identify that some specifications are not addressed by any issue, create them using the following process in a loop until all of the requirements are covered:

1. Plan a task
2. Evaluate if the criteria above is adhered to
3. Create it as a GitHub issue