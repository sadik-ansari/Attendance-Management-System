### 1. Actors

In software engineering, an **actor is an entity that interacts with the system** to achieve a goal. 

Actors in this system include:

- Administrator
- Teacher
- Faculty
- HR
- Student
- Employee

### 2. Organization Types and Roles

The platform supports three organization types: School, College, and Company. Each organization type has roles with different responsibilities and permissions. There are three types of Organization:

1. School
2. College
3. Company

Every types has their own roles which help us t understand their work.

1. School: 
    
    School Organization has three roles of their actors:
    
    1. Admin: So the responsibility of admin is to manage the system very well, because of too much responsibility like
        - Admin should be able to view an organizational dashboard containing user counts and attendance summaries such as total users, present users, and absent users.
        - Should able to add/deactivate/update the students and teachers.
        - View every students and teachers personal information (not password)
    2. Teacher: So the responsibility of teachers are:
        - In every school, each class usually has a class teacher who is assigned to manage the class and teach the students, so that teacher should able to add students. Adding students responsibility is assign on to class teacher not every teacher.
        - Teachers should be able to mark attendance only for students/classes they are authorized to manage. Students can report an incorrect attendance record to an administrator for review and correction.
        - Can view the student info.
        - Can’t able to see the other teacher personal info
    3. Student: Responsibility of student is:
        - Should able to see their own Attendance and personal info.
2. College: 
    
    College Organization has three roles of their actors:
    
    1. Admin: So the responsibility of admin is to manage the system very well, because of too much responsibility like
        - Admin should be able to view an organizational dashboard containing user counts and attendance summaries such as total users, present users, and absent users.
        - Should able to add/deactivate/update the students and faculties.
        - View every students and faculties personal information (not password).
    2. Faculty: So the responsibility of Faculties are:
        - Should able to mark attendance of students
        - Can view the student info.
        - Faculty members cannot view other faculty members' personal information.
        - Some faculty will be HOD of their department, so are responsible for adding students. HOD is not a seprate role, it is additional responsibility.
        - Students can report an incorrect attendance record to an administrator for review and correction.
        - An HOD can manage students within their assigned department.
    3. Student: Responsibility of studetn is:
        - Should able to see their own Attendance and personal info.
3. Company: 
    
    Company Organization has three roles of their actors:
    
    1. Admin: So the responsibility of admin is to manage the system very well, because of too much responsibility like
        - Admin should be able to view an organizational dashboard containing user counts and attendance summaries such as total users, present users, and absent users.
        - Should able to add/deactivate/update the employees/HR users.
        - View every employees personal information (not password).
    2. HR: So the responsibility of HR are:
        - Should able to give permission of leaves, and able reject the leaves
        - Can view the employees info.
        - Should able to view attendance history.
        - Should able to generate attendance reports.
        - HR can correct employee attendance records after reviewing the request.
    3. Employee: Responsibility of employees is:
        - Should able to see their own Attendance and personal info.
        - Employee should able to mark their attendance.
4. **Platform-Level Role**
    
    **Platform Operator**
    
    The Platform Operator manages organization registration and onboarding at the platform level.
    
    **Responsibilities:**
    
    - Review organization registration requests.
    - Approve or reject registration requests.
    - Access only the information necessary to manage organization onboarding and other explicitly authorized platform-level operations.
    - Avoid accessing an organization's private attendance records, student information, or employee information unless a separate, explicitly authorized operational need exists.
    
    **Important:** The Platform Operator is a platform-level role, separate from an organization's Administrator. An organization Administrator manages users, attendance, and other operations within their own organization. The Platform Operator manages platform-level onboarding and does not automatically receive access to an organization's private data.
    

### 3. Actors Goals

### Platform-Level Actor

**Platform Operator**

A Platform Operator manages organization registration requests for the entire platform.

**Responsibilities:**

- View submitted organization registration requests.
- Review the information provided by the applicant.
- Approve or reject registration requests.
- Ensure that an organization is not activated before approval.
- Ensure that the initial organization administrator cannot access the organization before the required approval is completed.

**Important:** The Platform Operator is a platform-level role, not an organization-level role. It is separate from the Admin role of a School, College, or Company.

The Platform Operator should have only the permissions required to manage organization onboarding. This role does not automatically grant access to an organization's attendance records, student information, or employee information.

**Admin**

> Manage organization users and monitor overall attendance.
> 

**Teacher**

> Record and monitor attendance for assigned students.
> 

**Faculty**

> Record and monitor attendance for assigned students and, when assigned as HOD, manage students within their department.
> 

**Student**

> View personal attendance records and attendance percentage.
> 

**HR**

> Manage employee attendance and leave requests.
> 

**Employee**

> View personal attendance and leave information.
> 

### 4. Functional Requirements

A functional requirement describes a **specific capability or behavior the system must provide**.

4.1 Authentication & Authorization

4.2 Organization Management

4.3 User Management

4.4 Class & Department Management

4.5 Attendance Management

4.6 Leave Management

4.7 Reporting

4.8 Dashboards

4.9 Profile Management

#### 4.1 Authentication & Authorization

- **FR-AUTH-001 — Organization Registration Request**
    
    **Actor:** Organization Representative
    
    **Description:**
    
    The system shall allow an organization representative to submit a request to register a School, College, or Company on the platform.
    
    **Expected behavior:**
    
    - The system shall collect the required organization details, including organization name, organization type, official email address, and initial administrator information.
    - The system shall validate all submitted information on the server.
    - The system shall prevent duplicate organization registrations according to the defined uniqueness rules.
    - The system shall save the submitted information as an organization registration request with a `Pending` status.
    - The system shall not activate the organization or grant administrative access merely because a registration request has been submitted.
    - The system shall inform the applicant that the request has been submitted successfully and is awaiting review.
    - The system shall allow the applicant to receive the final approval or rejection decision.
    
    **Note:** An organization registration request and an active organization are separate things. An organization becomes active only after the required approval process is completed.
    
- **FR-AUTH-002 — Organization Registration Approval**
    
    **Actor:** Platform Operator
    
    **Description:**
    
    The system shall allow an authorized Platform Operator to review and approve or reject organization registration requests.
    
    **Expected behavior:**
    
    - The system shall allow only authorized Platform Operators to review registration requests.
    - The Platform Operator shall be able to view the information required to make an approval decision.
    - The Platform Operator shall be able to approve or reject a pending request.
    - The system shall update the request status according to the decision.
    - When a registration request is approved, the system shall activate the organization and allow the initial administrator to complete the required initial account activation process.
    - The initial administrator shall not gain access to the organization until the registration approval and required account activation steps have been completed.
    - When a registration request is rejected, the system shall not activate the organization or grant the initial administrator access.
    - The system shall not allow an organization administrator to approve their own organization's registration request or bypass the required platform-level approval process.
    - The system shall inform the applicant about the decision.
    - The system shall prevent unauthorized users from changing the approval status.
    
    **Note:** Only authorized Platform Operators can approve or reject registration requests. The initial organization administrator cannot approve their own request.
    
- **FR-AUTH-003 — User Account Creation**
    
    **Actor:** Administrator or another explicitly authorized organizational role
    
    **Description:**
    
    The system shall allow authorized personnel to create accounts for students, teachers, faculty members, HR personnel, and employees according to the organization's type and permissions.
    
    **Expected behavior:**
    
    - The system shall validate the submitted user information.
    - The system shall enforce the email uniqueness policy.
    - The system shall associate each user with the correct organization.
    - The system shall assign only roles supported by the organization type and the actor's permissions.
    - The system shall provide an appropriate account activation or initial credential process.
    - The system shall not allow unauthorized public registration into protected organizational roles.
        
        **Email Uniqueness Policy**
        
        **Decision:** The platform shall enforce globally unique email addresses for user accounts.
        
        **Rules:**
        
        - Each email address shall belong to only one user account across the entire platform.
        - The same email address shall not be registered for different users, even if they belong to different organizations.
        - The system shall check email uniqueness on the server during account creation.
        - The system shall enforce email uniqueness at the database level to prevent duplicate accounts, including when multiple registration requests occur simultaneously.
        - The system shall apply a consistent email normalization policy before checking uniqueness.
        - Deactivating a user account shall not automatically make its email address available for a new account.
        - The system shall not reveal another user's private information when rejecting a duplicate email address.
        
        **Reason for this decision:**
        
        Global email uniqueness simplifies account identification during login, password recovery, and account management. It also reduces authentication complexity for Version 1.
        
        **Example:**
        
        If `rahul@example.com` already belongs to a user at School A, the system shall reject registration using that email address for another user at Company B.
        
- **FR-AUTH-004 — User Login and Access Initialization**
    
    **Actor:** Registered User
    
    **Description:**
    
    The system shall authenticate registered users and establish their identity and organizational context so that access can be granted according to their roles and permissions.
    
    **Expected behavior:**
    
    - The system shall validate the submitted login credentials.
    - The system shall verify that the user's account is active and eligible to log in.
    - The system shall reject invalid credentials or ineligible accounts without revealing sensitive authentication information.
    - After successful authentication, the system shall identify the authenticated user.
    - The system shall determine the organization associated with the authenticated user's membership.
    - The system shall identify the user's assigned role and relevant additional responsibilities, such as assigned classes or departments, where applicable.
    - The system shall ensure that subsequent requests are authorized according to the user's role, organization membership, and relevant assignments.
    - The system shall prevent users from accessing resources or performing operations for which they do not have permission.
    - The system shall not grant access to protected resources solely because a user has successfully authenticated.
    
    **Note:** Authentication establishes the user's identity, while authorization determines what the user is allowed to access. The system must enforce authorization on the server for every protected operation.
    
- **FR-AUTH-005 — User Logout**
    
    **Actor:** Authenticated User
    
    **Description:**
    
    The system shall allow authenticated users to terminate their current session.
    
    **Expected behavior:**
    
    - The system shall invalidate the session or revoke the relevant authentication credential, as applicable to the chosen authentication mechanism.
    - The system shall clear authentication cookies when applicable.
    - The user shall no longer be able to access protected resources using the terminated session.
- **FR-AUTH-006 — Password Management and Recovery**
    
    **Actor:** Registered User or Explicitly Authorized Recovery Process
    
    **Description:**
    
    The system shall securely manage user passwords, including password creation, password changes, and forgotten-password recovery.
    
    **Expected behavior:**
    
    - The system shall enforce the defined password policy whenever a password is created or changed.
    - The system shall store passwords using an appropriate secure password-hashing algorithm.
    - The system shall never store passwords in plain text.
    - The system shall verify login passwords against the stored password hashes.
    - The system shall allow users to change their passwords through an authorized process.
    - The system shall provide a password-reset process that verifies the user's authority to recover the account.
    - The system shall use time-limited password-reset links or codes that can be used only as intended.
    - The system shall reject invalid, expired, or already-used password-reset links or codes.
    - The system shall ensure that password-reset credentials cannot be reused after a successful password reset.
    - The system shall never expose passwords or password-reset secrets in API responses, application logs, or error messages.
    - The system shall invalidate existing authenticated sessions after a successful password reset, so that the user must authenticate again.
    - The system shall handle invalid password-change and password-reset requests safely without exposing sensitive account information.
    
    **Note:** The specific password policy, password-hashing algorithm, recovery method, and technical implementation of session invalidation shall be finalized during Security and System Design.
    
- **FR-AUTH-007 — Role-Based and Assignment-Based Authorization**
    
    **Actor:** Authenticated User
    
    **Description:**
    
    The system shall allow users to perform only the actions permitted by their roles and assigned responsibilities. It shall also ensure that users can access only the resources belonging to their authorized organization.
    
    **Expected behavior:**
    
    - The system shall check the user's role before allowing a protected operation.
    - The system shall ensure that users can access only data belonging to their authorized organization.
    - The system shall restrict access to classes, students, and departments according to the user's assignments and permissions.
    - A Teacher shall be able to mark attendance only for the classes or students they are authorized to manage.
    - A Faculty member shall be able to mark attendance only for the classes or students they are authorized to manage.
    - An HOD shall be able to manage students only within their assigned department and according to their permitted responsibilities.
    - HOD shall remain an additional responsibility of a Faculty member, not a separate role.
    - The system shall not grant access to all classes, students, or departments merely because a user has a particular role.
    - The system shall check the user's permissions and relevant assignments on the server before allowing a protected operation.
    - The system shall deny unauthorized requests, even when users try to access protected API endpoints directly or change resource IDs in their requests.
    - The frontend shall display features according to the user's permissions, but the server shall remain responsible for enforcing access restrictions.
    
    **Note:** The specific permissions and assignment rules for each role shall be defined in the authorization permission matrix during system design.
    
- **FR-AUTH-008 — Organization Membership Identification**
    
    **Actor:** Authenticated User
    
    **Description:**
    
    The system shall identify the organization associated with an authenticated user and enforce organizational data isolation.
    
    **Expected behavior:**
    
    - The system shall resolve the user's organization membership using trusted server-side identity and authorization data.
    - The system shall restrict organization-specific operations to the user's authorized organization.
    - The system shall prevent users from accessing another organization's protected records by manipulating request parameters or resource identifiers.
    - The system shall verify organization membership before allowing access to organization-specific users, attendance records, reports, and settings.
- **FR-AUTH-009 — Account Activation and Deactivation**
    
    **Actor:** Authorized Administrator
    
    **Description:**
    
    The system shall allow authorized administrators to activate or deactivate existing organizational user accounts. Reactivation shall restore access to an existing deactivated account only when the user and organization satisfy the required access conditions.
    
    **Expected behavior:**
    
    - The system shall verify that the administrator has permission to manage the target account.
    - The system shall update the account status according to the requested action.
    - The system shall prevent deactivated users from establishing new authenticated sessions.
    - The system shall prevent deactivated users from accessing protected resources through existing sessions or authentication credentials.
    - The system shall invalidate existing sessions or authentication credentials after deactivation, or otherwise ensure that access is denied promptly.
    - The system shall ensure that subsequent requests from a deactivated user are rejected by the server, even if the user still possesses a previously issued authentication credential.
    - The system shall preserve the deactivated user's account information and historical attendance records.
    - The system shall distinguish reactivation of an existing deactivated account from the initial activation of an administrator account during organization onboarding.
    - An authorized administrator may reactivate an existing organizational account only when permitted by the applicable organizational and platform policies.
    - Reactivation shall not bypass organization registration approval, organization status restrictions, or any required initial account activation steps.
    - After reactivation, the system shall grant access only according to the user's current role, organization membership, permissions, and account status.
    - The system shall prevent unauthorized users from activating or deactivating accounts.
    
    **Note:** The mechanism for invalidating existing sessions or credentials shall be finalized during Security and System Design. Account deactivation shall not automatically delete the user's account or historical attendance records.
    
- **FR-AUTH-010 — Failed Login Protection**
    
    **Actor:** User attempting to authenticate
    
    **Description:**
    
    The system shall implement safeguards against repeated unsuccessful login attempts.
    
    **Expected behavior:**
    
    - The system shall limit or slow repeated failed authentication attempts according to a defined security policy.
    - The system shall avoid revealing whether a particular email address is registered.
    - The system shall provide an appropriate response when an attempt limit is reached.
    - The protection mechanism shall not unnecessarily prevent legitimate users from recovering access to their accounts.
- **FR-AUTH-011 — Authentication Credential Expiry**
    
    **Actor:** Authenticated User
    
    **Description:**
    
    The system shall enforce the validity period of authentication credentials.
    
    **Expected behavior:**
    
    - Expired credentials shall not grant access to protected resources.
    - The system shall require re-authentication or an authorized credential-renewal process when necessary.
    - Credential renewal shall not bypass account status checks or authorization rules.

#### 4.2 Organization Management

This section defines the functional requirements for managing organization profiles and their lifecycle within the Attendance Management System.

The platform shall support Schools, Colleges, and Companies through a shared organization-management system. Organization-specific functionality shall be defined in the relevant requirements sections.

Organization registration, approval, authentication, account activation, and general authorization rules are defined in Section 4.1. This section focuses on organization profiles, organization lifecycle management, and protection of organization-owned data.

- **FR-ORG-001 — Organization Profile Creation**
    
    **Actor:** System
    
    **Description:**
    
    The system shall create an organization profile after an authorized Platform Operator approves the organization's registration request, following the approval and account activation process defined in Section 4.1.
    
    **Expected behavior:**
    
    - The system shall create the organization profile using the approved registration information.
    - The profile shall include the organization's name, organization type, and required registration and contact details.
    - The system shall associate the organization with its initial administrator according to the onboarding process defined in Section 4.1.
    - The system shall validate required profile fields and reject invalid data before creating the organization profile.
    - The system shall assign the organization an initial status of `Active` after successful approval and profile creation.
- **FR-ORG-002 — Organization Profile Viewing**
    
    **Actor:** Organization Administrator
    
    **Description:**
    
    The system shall allow authorized organization administrators to view their organization's profile.
    
    **Expected behavior:**
    
    - The system shall display the organization's name, organization type, contact details, and current status.
    - The system shall restrict profile access according to the identity, organization membership, and authorization rules defined in Section 4.1.
    - The system shall not expose private profile information belonging to another organization to unauthorized users.
- **FR-ORG-003 — Organization Profile Updating**
    
    **Actor:** Organization Administrator
    
    **Description:**
    
    The system shall allow authorized organization administrators to update permitted organization profile details.
    
    **Expected behavior:**
    
    - The system shall allow administrators to update permitted fields, including the organization name and contact information.
    - The system shall validate submitted information before saving changes.
    - The system shall reject missing, malformed, or otherwise invalid field values according to the defined profile validation rules.
    - The system shall enforce appropriate field length limits and formats for fields such as organization name, email address, and contact information.
    - The system shall prevent administrators from modifying restricted fields, including organization type and lifecycle status, through ordinary profile updates.
    - The system shall reject invalid updates without saving any part of the invalid changes.
    - The system shall preserve the existing valid profile information when an update is rejected.
- **FR-ORG-004 — Organization Type Enforcement**
    
    **Actor:** System
    
    **Description:**
    
    The system shall associate each organization with exactly one supported organization type: `School`, `College`, or `Company`.
    
    **Expected behavior:**
    
    - The system shall validate the organization type during organization creation.
    - The organization type shall determine which organization-specific roles and features are applicable.
    - The system shall prevent organization administrators from changing the organization type through ordinary profile updates.
    - Any future organization-type migration shall require a separately defined and authorized process.
    - The system shall enforce organization-type restrictions on the server for all applicable organization-specific operations.
- **FR-ORG-005 — Organization Status Management**
    
    **Actor:** Platform Operator
    
    **Description:**
    
    The system shall maintain and manage the lifecycle status of each existing organization.
    
    **Supported organization statuses:**
    
    - `Active`: The organization is operating normally and may use permitted platform features.
    - `Suspended`: The organization is temporarily restricted from using ordinary organization-level functionality.
    - `Deactivated`: The organization is disabled from ordinary platform operations, potentially following organizational closure. Reopening it requires an explicitly authorized reactivation decision.
    
    **Permitted status transitions:**
    
    | Current status | Requested status | Allowed? |
    | --- | --- | --- |
    | `Active` | `Suspended` | Yes |
    | `Active` | `Deactivated` | Yes |
    | `Suspended` | `Active` | Yes |
    | `Suspended` | `Deactivated` | Yes |
    | `Deactivated` | `Active` | Yes, through explicit reactivation |
    | `Deactivated` | `Suspended` | No |
    | Same status | Same status | No status change required |
    
    **Expected behavior:**
    
    - The system shall assign the `Active` status when an organization is successfully created following approval.
    - Only an authorized Platform Operator shall be permitted to perform organization lifecycle status changes.
    - The system shall validate each requested transition against the permitted transition rules before applying it.
    - The system shall reject invalid transitions and unauthorized status-change requests without modifying the existing status.
    - Reactivation from `Deactivated` shall require an explicit Platform Operator decision.
    - The system shall preserve the organization's existing data and historical records when its status changes.
    - The system shall maintain the correct status after each successful lifecycle operation.
    
    **Note:** `Pending` is the status of an organization registration request, as defined in Section 4.1. It is not a status of an existing organization record in this section.
    
- **FR-ORG-006 — Organization Data Isolation**
    
    **Actor:** System
    
    **Description:**
    
    The system shall protect organization-owned records and prevent unauthorized cross-organization access or modification, following the identity, membership, and authorization rules defined in Section 4.1.
    
    **Expected behavior:**
    
    - The system shall restrict access to organization-owned users, attendance records, reports, and settings according to the user's authorized organization membership and permissions.
    - The system shall not trust an organization identifier supplied by the client as sufficient proof of authorization.
    - The system shall prevent users from accessing or modifying another organization's records by manipulating organization identifiers, resource identifiers, URL parameters, or request bodies.
    - The system shall enforce organization data isolation on protected API operations.
    - The system shall reject unauthorized cross-organization requests, including requests made directly to API endpoints.
- **FR-ORG-007 — Suspended and Deactivated Organization Handling**
    
    **Actor:** System
    
    **Description:**
    
    The system shall enforce access restrictions according to an organization's current lifecycle status while preserving its historical data.
    
    **Expected behavior:**
    
    - The system shall permit ordinary organization-level functionality only when the organization is `Active` and the authenticated user has the required permissions.
    - The system shall prevent suspended organizations from performing ordinary organization-level operations while the suspension remains in effect.
    - The system shall prevent deactivated organizations from performing ordinary organization-level operations.
    - The system shall enforce organization status restrictions on the server, including for users with previously issued authentication credentials.
    - The system shall preserve user accounts, attendance records, and other historical organizational data when an organization is suspended or deactivated.
    - The system shall not interpret data preservation as automatic permission to access historical records while the organization is restricted.
    - After reactivation, the system shall restore access only when the organization is `Active` and the user satisfies the applicable account status, membership, and authorization requirements.
    - The system shall not automatically delete historical records or reactivate an organization merely because a period of time has elapsed.
    
    **Note:** Suspension and deactivation both restrict ordinary organization-level functionality in Version 1. Suspension represents a temporary restriction, while deactivation represents a formal disabling of the organization. Historical data shall remain stored unless a separately defined data-retention policy requires otherwise.

#### 4.3 User Management

This section defines the functional requirements for managing user records within an organization. It covers user creation, profile viewing, profile updating, role assignment, organization association, and user deactivation.

User authentication, account activation, password management, and general authorization rules are defined in Section 4.1. Organization lifecycle and organization-level data isolation are defined in Section 4.2.

- **FR-USER-001 — User Account Creation**
    
    **Actor:** Organization Administrator or explicitly authorized organizational user
    
    **Description:**
    
    The system shall allow authorized users to create user accounts within their organization according to the organization's type, the creator's permissions, and the creator's assigned responsibilities.
    
    **Expected behavior:**
    
    - The system shall collect and validate the required information before creating a user account.
    - The system shall associate the new user with the correct organization.
    - The system shall permit only roles supported by the organization's type.
    - The system shall enforce the global email uniqueness policy defined in Section 4.1.
    - The system shall allow an Organization Administrator to create accounts for users supported by their organization type and permissions.
    - In a School, an assigned class teacher may create student accounts only within their assigned class and permitted responsibilities.
    - In a College, an authorized Faculty member assigned as HOD may create student accounts only within their assigned department and permitted responsibilities.
    - In a Company, authorized HR personnel may create employee accounts within their permitted responsibilities.
    - The system shall not allow teachers, faculty members, or HR personnel to create accounts outside their authorized scope.
    - The system shall reject user creation requests from unauthorized actors or requests containing invalid information or unsupported roles.
    - The system shall follow the account activation and initial credential requirements defined in Section 4.1.
    - The system shall enforce the email uniqueness policy defined in Section 4.1 when creating a user account.
- **FR-USER-002 — User Profile Viewing**
    
    **Actor:** Authorized organizational user
    
    **Description:**
    
    The system shall allow authorized users to view user information according to their role, permissions, and organizational responsibilities.
    
    **Expected behavior:**
    
    - The system shall display only the user information permitted for the requesting user's role.
    - Users shall be able to view their own permitted profile information.
    - Organization Administrators shall be able to view permitted profile information for users within their organization.
    - Teachers and faculty members shall be able to view student information within their authorized scope.
    - HR personnel shall be able to view employee information within their authorized scope.
    - The system shall prevent unauthorized access to private user information, including password hashes and authentication secrets.
    - The system shall prevent users from viewing information outside their authorized organizational scope.
    - Authorized administrators shall be able to access deactivated user records for legitimate administrative and historical purposes.
- **FR-USER-003 — User Profile Updating**
    
    **Actor:** Authorized organizational user
    
    **Description:**
    
    The system shall allow authorized users to update permitted user profile information.
    
    **Expected behavior:**
    
    - The system shall allow updates only to fields the requesting user is authorized to modify.
    - The system shall validate submitted information before saving changes.
    - The system shall reject invalid or unauthorized update requests.
    - The system shall preserve existing valid information when an update is rejected.
    - The system shall prevent ordinary profile updates from changing restricted account status, organization association, or role information without the required authorization.
    - The system shall enforce the account management and authorization rules defined in Section 4.1.
- **FR-USER-004 — Role Assignment and Modification**
    
    **Actor:** Organization Administrator
    
    **Description:**
    
    The system shall allow authorized Organization Administrators to assign or change organizational user roles according to the supported organization type and applicable authorization rules.
    
    **Expected behavior:**
    
    - The system shall restrict school users to applicable school roles, college users to applicable college roles, and company users to applicable company roles.
    - Only the Organization Administrator shall be permitted to change an existing organizational user's role in Version 1.
    - The system shall reject unsupported or unauthorized role assignments.
    - The system shall not allow an Organization Administrator to assign the platform-level Platform Operator role through ordinary organization user management.
    - The system shall treat class teacher and HOD as additional responsibilities or assignments rather than separate user roles.
    - The system shall ensure that assigning additional responsibilities does not grant permissions beyond the defined scope of those responsibilities.
    - Any future delegation of role-management permissions shall require separately defined authorization rules.
- **FR-USER-005 — User Organization Association**
    
    **Actor:** System
    
    **Description:**
    
    The system shall associate each organizational user with the organization to which the user belongs and enforce the organization isolation requirements defined in Section 4.2.
    
    **Expected behavior:**
    
    - The system shall establish the user's organization association during account creation.
    - The system shall prevent unauthorized users from changing their organization association.
    - The system shall ensure that user management operations respect organization-level data isolation.
    - The system shall not permit a user to access another organization's records merely by changing a user identifier or organization identifier in a request.
    - Any future transfer of a user between organizations shall require a separately defined and authorized process.
- **FR-USER-006 — User Deactivation and Historical Record Preservation**
    
    **Actor:** Organization Administrator
    
    **Description:**
    
    The system shall allow authorized Organization Administrators to deactivate organizational user accounts while preserving historical records required for administrative and reporting purposes.
    
    **Expected behavior:**
    
    - The system shall permit user deactivation only by authorized Organization Administrators, following the account lifecycle rules defined in Section 4.1.
    - The system shall enforce the account deactivation and access restrictions defined in Section 4.1.
    - Deactivation shall not automatically delete the user's account or historical attendance records.
    - Historical attendance records shall remain associated with the relevant user and organization.
    - The system shall exclude deactivated users from ordinary active-user lists by default.
    - The system shall provide authorized administrators with a way to view deactivated user records separately from active users.
    - The system shall preserve the information necessary to identify users associated with historical attendance records.
    - Reactivation of a deactivated account shall follow the account lifecycle rules defined in Section 4.1.
    - Reactivation shall not bypass organization lifecycle restrictions, organization membership requirements, or authorization rules.
    - Deactivation shall not automatically transfer the user's responsibilities or permissions to another user.
    - The system shall make assignments held by a deactivated user available for review by authorized administrators, so that necessary responsibilities can be reassigned through the applicable assignment-management process.
    - Assignment-management requirements shall define how assignments belonging to deactivated users are reviewed, removed, or reassigned and shall ensure that deactivated users cannot continue performing restricted responsibilities.
