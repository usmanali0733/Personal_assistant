---
name: create-owesome-task
description: Automates logging into projects.owesome.work by opening browser and creating 3 daily tasks with task reports using the internal-management-tasks format, totaling 8 hours.
---

# Create Owesome Tasks & Reports

## Objective
To log in to the Owesome project board (https://projects.owesome.work/l/fznp92?view=board) using credentials from the `.env` file, and automatically create and manage daily tasks and time tracking.

## Rules & Requirements
1. **Daily Quota:** You must create exactly 3 tasks daily. 
2. **Time Tracking & Billing:** The total duration for these 3 tasks must equal exactly 8 hours per day. Divide the 8 hours reasonably among the 3 tasks. Tracking time does not automatically mark it as billable; the **Billable** flag is a separate input that must be explicitly selected.
3. **Task Format:** Each task must strictly follow the `internal-management-tasks/skill.md` structure:
   - Problem
   - Value
   - Scope
   - User Story
   - Acceptance Criteria
4. **Task Reports:** After work is marked as done, write a task report using the exact format specified in the `internal-management-tasks` skill (e.g., starting with `Task report :` and using a bulleted list of concrete changes).

## Execution Steps
1. **Read Credentials:** Extract `owesome_email` and `owesome_password` from the `.env` file.
2. **Browser Automation:** Navigate to `https://projects.owesome.work/l/fznp92?view=board`.
3. **Log In:** Authenticate using the credentials.
4. **Create and Configure Tasks:**
   - Click the “+ Add Task” button.
   - Type the task name and press Enter.
   - Open the newly created task.
   - Set the start and due dates.
   - Assign the task to yourself.
   - Enter a time estimate.
   - Enter time tracked also.
   - Add a description.
   - Set billable hours.
   - Send a comment.
5. **Track Time:** Ensure the logged time across tasks sums to 8 hours, and adjust as needed.
6. **Task Report:** Log the corresponding task completion reports for the shipped work.
1. **Read Credentials:** Extract `owesome_email` and `owesome_password` from the `.env` file.
2. **Browser Automation:** Navigate to `https://projects.owesome.work/l/fznp92?view=board`.
3. **Log In:** Authenticate using the credentials.
4. **Create Tasks:** Formulate and submit 3 distinct tasks following the structural guidelines.
5. **Track Time:** Log the time across the tasks (summing to 8 hours) and ensure you explicitly set the separate **Billable** input.
6. **Task Report:** Log the corresponding task completion reports for the shipped work.
