POSTMORTEM REPORT
Incident Duration:  
Start: 10/04/2024, 5:00 AM 
End: 14/04/2024, 8:00 PM  
IMPACT:

- Affected Service: 
  The entire application, running on PHP 7, experienced downtime during this period.

- User Experience: 
  Users faced an inability to access their accounts, and those already logged in were unable to perform any actions, such as sending messages.

- User Affected: 
  Nearly 100% of users were impacted by this outage.

- Root Cause:  
  The root cause was an update deployed to the production environment while certain methods were still dependent on the previous development stack (PHP 7, Apache 5).

TIMELINE:

- Detection Time:  
  The issue was first detected on 10/04/2024 at 2:00 PM .

- Detection Method: 
  The issue was identified through alerts in the application deployment log regarding dependency issues.
ACTIONS TAKEN:

- Response: 
  A rollback of the application to the previous development state was initiated to resolve the issue.

- Misleading Paths: 
  Initially, attempts were made to update affected methods and variables to the new version, which only exacerbated the problem.

- Team Involved:
  The incident was escalated to the developers' team for resolution.

- Resolution:
  The incident was resolved by reverting the application to its previous state. Although this resulted in new user accounts being lost, it was deemed the most effective solution.

- Root Cause Analysis and Resolution:  
  The issue stemmed from an individual attempting to upgrade their local development stack, mistakenly affecting the production environment. The resolution involved a comprehensive rollback to restore functionality.

- Implementation: 
  Additionally, automated backups were scheduled daily at 23:59 PM to prevent similar incidents in the future.
CORRECTIVE AND PREVENTATIVE MEASURES:

- Corrective Actions 
  Developers' local environments were configured with Docker containers to isolate development activities and prevent global system disruptions.

- Preventative Measures:  
  - Enhance monitoring systems to detect similar dependency issues early.
  - Conduct thorough testing before deploying updates to production.
  - Establish clear communication channels between development and operations teams to prevent similar miscommunications.
  - Implement stricter change control processes to prevent unauthorized changes to production environments.

