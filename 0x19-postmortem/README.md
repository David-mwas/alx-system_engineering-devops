Postmortem: Web Stack Outage

Issue Summary:

Duration: May 9, 2022, 9:00 AM to May 14, 2022, 3:00 PM EAT

Impact: Service disruption affecting the online marketplace platform

Users experienced intermittent access issues, slow page loads, and failed transactions. Approximately 30% of users were affected.

Timeline:

- May 15, 2023, 9:30 AM: Issue detected by monitoring alerts indicating increased error rates and latency.

- Investigation initiated by the on-call engineer, John, based on the alert.

- Assumption made that the issue was related to the database due to recent schema changes.

- Database team informed about the potential problem.

- Several database queries optimized and indexes rebuilt as an initial troubleshooting step.

- May 9, 2022, 1:00 PM: No improvement observed; incident escalated to the infrastructure team.

- Infrastructure team analyzed network configurations and firewall rules but found no anomalies.

- Misleading path: Load balancer settings were reviewed and adjusted, but no significant impact on the issue.

- Incident escalated to the development team for further investigation.

- May 10, 2022, 8:00 AM: Development team discovered a code change related to caching that might have caused the issue.

- The problematic code was rolled back to a previous stable version.

- May 10, 2022, 3:00 PM: Service fully restored; issue resolved.

Root Cause and Resolution:

Root Cause: The recent code change introduced a caching mechanism that led to unexpected cache invalidation and increased load on the database. This resulted in degraded performance and intermittent service disruptions.

Resolution: The code change responsible for the caching mechanism was rolled back to a previous version, eliminating the cache-related issues. Additionally, database optimizations and indexes were reevaluated to enhance performance.

Corrective and Preventative Measures:

1. Improve code review process: Strengthen the code review process to ensure that changes related to critical system components, such as caching mechanisms, are thoroughly examined and tested before deployment.

2. Performance testing: Implement comprehensive performance testing procedures to identify any potential bottlenecks or scalability issues prior to production deployment.

3. Monitoring enhancements: Enhance monitoring capabilities to provide more granular insights into cache utilization, database performance, and system health.

4. Incident response training: Conduct training sessions for all teams involved in incident response to improve coordination and minimize downtime during future outages.

Tasks:

- Conduct a thorough review of the code changes related to caching and ensure they adhere to best practices.

- Establish a comprehensive performance testing framework and include it as part of the CI/CD pipeline.

- Enhance monitoring systems to track cache utilization, database performance metrics, and overall system health.

- Develop incident response playbooks and conduct regular training exercises.

- Perform a post-incident review to identify any additional areas for improvement and implement necessary changes.

By implementing these measures, we aim to prevent similar incidents in the future, minimize user impact, and ensure the stability and reliability of our online marketplace platform.
