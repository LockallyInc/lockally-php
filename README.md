<!-- lockally-brand-header -->
<p align="center">
  <a href="https://lockally.com">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/LockallyInc/community/main/brand/lockup-dark.png">
      <img alt="Lockally" src="https://raw.githubusercontent.com/LockallyInc/community/main/brand/lockup-light.png" width="260">
    </picture>
  </a>
</p>
<!-- /lockally-brand-header -->

# Lockally

The lockally control plane lets integrators and direct customers manage
everything except actual mail data flow (which uses standard JMAP / IMAP /
SMTP-submission against the data plane endpoints).

**Authentication.** All `/v1/_*` endpoints require a Bearer API key in the
`Authorization` header. Keys are formatted `lk_live_<8-char-prefix>_<32-char-secret>`,
or `lk_test_<...>` for a test key. Create keys in the dashboard, or with
`POST /v1/api-keys` using a key that holds `tenant:admin`.

The key's plan is checked on every request, so a key stops working if the
account moves to a plan without API access, and works again if it moves back.

**Errors.** Failures return [RFC 9457](https://www.rfc-editor.org/rfc/rfc9457)
`application/problem+json` documents.

**Scopes.** Each endpoint requires a specific scope on the presented key.
Insufficient scope returns `403` with the required scope name in `detail`.



## Installation & Usage

### Requirements

PHP 8.1 and later.

### Composer

To install the bindings via [Composer](https://getcomposer.org/), add the following to `composer.json`:

```json
{
  "repositories": [
    {
      "type": "vcs",
      "url": "https://github.com/GIT_USER_ID/GIT_REPO_ID.git"
    }
  ],
  "require": {
    "GIT_USER_ID/GIT_REPO_ID": "*@dev"
  }
}
```

Then run `composer install`

### Manual Installation

Download the files and include `autoload.php`:

```php
<?php
require_once('/path/to/Lockally/vendor/autoload.php');
```

## Getting Started

Please follow the [installation procedure](#installation--usage) and then run the following:

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



// Configure Bearer (lk_live_<prefix>_<secret>) authorization: bearerAuth
$config = Lockally\SDK\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new Lockally\SDK\Api\AddOnsApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$name = 'name_example'; // string | Add-on key

try {
    $result = $apiInstance->activateAddOn($name);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling AddOnsApi->activateAddOn: ', $e->getMessage(), PHP_EOL;
}

```

## API Endpoints

All URIs are relative to *https://api.lockally.com*

Class | Method | HTTP request | Description
------------ | ------------- | ------------- | -------------
*AddOnsApi* | [**activateAddOn**](docs/Api/AddOnsApi.md#activateaddon) | **POST** /v1/add-ons/{name}/activate | Activate an add-on
*AddOnsApi* | [**cancelAddOn**](docs/Api/AddOnsApi.md#canceladdon) | **POST** /v1/add-ons/{name}/cancel | Cancel an add-on
*AddOnsApi* | [**getAddOnStatus**](docs/Api/AddOnsApi.md#getaddonstatus) | **GET** /v1/add-ons/{name} | Get add-on status
*AddOnsApi* | [**listAddOns**](docs/Api/AddOnsApi.md#listaddons) | **GET** /v1/add-ons | List add-ons
*AdminApi* | [**adminLogin**](docs/Api/AdminApi.md#adminlogin) | **POST** /v1/admin/login | Tenant-admin email+password login
*AdminApi* | [**adminLogout**](docs/Api/AdminApi.md#adminlogout) | **POST** /v1/admin/logout | Invalidate the current admin session
*AdminApi* | [**getCurrentAdmin**](docs/Api/AdminApi.md#getcurrentadmin) | **GET** /v1/admin/me | Get the current admin + tenant
*AdminsApi* | [**deleteAdmin**](docs/Api/AdminsApi.md#deleteadmin) | **DELETE** /v1/admins/{id} | Delete an admin
*AdminsApi* | [**inviteAdmin**](docs/Api/AdminsApi.md#inviteadmin) | **POST** /v1/admins | Invite a new admin
*AdminsApi* | [**listAdmins**](docs/Api/AdminsApi.md#listadmins) | **GET** /v1/admins | List tenant admins
*AdminsApi* | [**updateAdmin**](docs/Api/AdminsApi.md#updateadmin) | **PATCH** /v1/admins/{id} | Update an admin
*AgentsApi* | [**downloadThreadAttachment**](docs/Api/AgentsApi.md#downloadthreadattachment) | **GET** /v1/threads/{threadID}/messages/{messageID}/attachments/{idx} | Download an attachment
*AgentsApi* | [**getThread**](docs/Api/AgentsApi.md#getthread) | **GET** /v1/threads/{threadID} | Get a whole conversation
*AgentsApi* | [**getThreadMessage**](docs/Api/AgentsApi.md#getthreadmessage) | **GET** /v1/threads/{threadID}/messages/{messageID} | Get one message with body
*AgentsApi* | [**grantApiKeyMailbox**](docs/Api/AgentsApi.md#grantapikeymailbox) | **POST** /v1/api-keys/{keyID}/mailboxes | Grant a mailbox to a key
*AgentsApi* | [**listApiKeyMailboxes**](docs/Api/AgentsApi.md#listapikeymailboxes) | **GET** /v1/api-keys/{keyID}/mailboxes | List a key&#39;s mailbox grants
*AgentsApi* | [**listInboxes**](docs/Api/AgentsApi.md#listinboxes) | **GET** /v1/inboxes | List granted inboxes
*AgentsApi* | [**listThreads**](docs/Api/AgentsApi.md#listthreads) | **GET** /v1/inboxes/{mailbox}/threads | List conversation threads
*AgentsApi* | [**lookupContact**](docs/Api/AgentsApi.md#lookupcontact) | **GET** /v1/contacts/lookup | Who is this sender?
*AgentsApi* | [**markThreadMessageRead**](docs/Api/AgentsApi.md#markthreadmessageread) | **POST** /v1/threads/{threadID}/messages/{messageID}/read | Mark read/unread
*AgentsApi* | [**replyToThread**](docs/Api/AgentsApi.md#replytothread) | **POST** /v1/threads/{threadID}/reply | Reply in-thread (agent stream)
*AgentsApi* | [**revokeApiKeyMailbox**](docs/Api/AgentsApi.md#revokeapikeymailbox) | **DELETE** /v1/api-keys/{keyID}/mailboxes/{mailboxID} | Revoke a mailbox grant
*AgentsApi* | [**startConversation**](docs/Api/AgentsApi.md#startconversation) | **POST** /v1/inboxes/{mailbox}/messages | Start a new conversation (agent stream)
*AgentsApi* | [**whoami**](docs/Api/AgentsApi.md#whoami) | **GET** /v1/auth/whoami | Introspect the calling credentials
*AiApi* | [**classifyThread**](docs/Api/AiApi.md#classifythread) | **POST** /v1/threads/{threadID}/classify | LLM-classify a thread
*AiApi* | [**createAiUnitsCheckout**](docs/Api/AiApi.md#createaiunitscheckout) | **POST** /v1/billing/ai-units/checkout | Buy prepaid AI units
*AiApi* | [**getAiConfig**](docs/Api/AiApi.md#getaiconfig) | **GET** /v1/ai-config | Read the tenant&#39;s AI configuration
*AiApi* | [**updateAiConfig**](docs/Api/AiApi.md#updateaiconfig) | **PUT** /v1/ai-config | Configure the AI tier
*AliasesApi* | [**createAlias**](docs/Api/AliasesApi.md#createalias) | **POST** /v1/aliases | Create an alias
*AliasesApi* | [**deleteAlias**](docs/Api/AliasesApi.md#deletealias) | **DELETE** /v1/aliases/{address} | Delete an alias
*AliasesApi* | [**listAliases**](docs/Api/AliasesApi.md#listaliases) | **GET** /v1/aliases | List aliases
*ApiKeysApi* | [**createApiKey**](docs/Api/ApiKeysApi.md#createapikey) | **POST** /v1/api-keys | Create an API key
*ApiKeysApi* | [**listApiKeys**](docs/Api/ApiKeysApi.md#listapikeys) | **GET** /v1/api-keys | List API keys
*ApiKeysApi* | [**revokeApiKey**](docs/Api/ApiKeysApi.md#revokeapikey) | **DELETE** /v1/api-keys/{id} | Revoke an API key
*BillingApi* | [**createBillingCheckout**](docs/Api/BillingApi.md#createbillingcheckout) | **POST** /v1/billing/checkout | Create a plan checkout session
*BillingApi* | [**createUnitsCheckout**](docs/Api/BillingApi.md#createunitscheckout) | **POST** /v1/billing/units/checkout | Create a send-units checkout session
*BillingApi* | [**getBilling**](docs/Api/BillingApi.md#getbilling) | **GET** /v1/billing | Get billing status
*CalendarsApi* | [**addCalendarMember**](docs/Api/CalendarsApi.md#addcalendarmember) | **POST** /v1/calendars/{id}/members | Add a member to a calendar
*CalendarsApi* | [**createCalendar**](docs/Api/CalendarsApi.md#createcalendar) | **POST** /v1/calendars | Create a calendar
*CalendarsApi* | [**createCalendarEvent**](docs/Api/CalendarsApi.md#createcalendarevent) | **POST** /v1/calendars/{id}/events | Create an event in a calendar
*CalendarsApi* | [**createCalendarIntegration**](docs/Api/CalendarsApi.md#createcalendarintegration) | **POST** /v1/calendar-integrations | Create a calendar integration
*CalendarsApi* | [**deleteCalendar**](docs/Api/CalendarsApi.md#deletecalendar) | **DELETE** /v1/calendars/{id} | Delete a calendar
*CalendarsApi* | [**deleteCalendarEvent**](docs/Api/CalendarsApi.md#deletecalendarevent) | **DELETE** /v1/calendars/{id}/events/{eventId} | Delete a calendar event
*CalendarsApi* | [**deleteCalendarIntegration**](docs/Api/CalendarsApi.md#deletecalendarintegration) | **DELETE** /v1/calendar-integrations/{id} | Delete a calendar integration
*CalendarsApi* | [**getCalendar**](docs/Api/CalendarsApi.md#getcalendar) | **GET** /v1/calendars/{id} | Get a calendar
*CalendarsApi* | [**getCalendarOverview**](docs/Api/CalendarsApi.md#getcalendaroverview) | **GET** /v1/calendar-overview | Administrative overview of the organization&#39;s calendar system
*CalendarsApi* | [**getCalendarPolicies**](docs/Api/CalendarsApi.md#getcalendarpolicies) | **GET** /v1/calendar-policies | Get calendar policies
*CalendarsApi* | [**getCalendarSecurity**](docs/Api/CalendarsApi.md#getcalendarsecurity) | **GET** /v1/calendar-security | Get calendar security overview
*CalendarsApi* | [**listCalendarEvents**](docs/Api/CalendarsApi.md#listcalendarevents) | **GET** /v1/calendars/{id}/events | List events in a calendar
*CalendarsApi* | [**listCalendarIntegrations**](docs/Api/CalendarsApi.md#listcalendarintegrations) | **GET** /v1/calendar-integrations | List calendar integrations
*CalendarsApi* | [**listCalendarMembers**](docs/Api/CalendarsApi.md#listcalendarmembers) | **GET** /v1/calendars/{id}/members | List calendar members
*CalendarsApi* | [**listCalendars**](docs/Api/CalendarsApi.md#listcalendars) | **GET** /v1/calendars | List calendars
*CalendarsApi* | [**removeCalendarMember**](docs/Api/CalendarsApi.md#removecalendarmember) | **DELETE** /v1/calendars/{id}/members/{memberId} | Remove a member from a calendar
*CalendarsApi* | [**syncCalendarIntegration**](docs/Api/CalendarsApi.md#synccalendarintegration) | **POST** /v1/calendar-integrations/{id}/sync | Trigger sync for a calendar integration
*CalendarsApi* | [**updateCalendar**](docs/Api/CalendarsApi.md#updatecalendar) | **PATCH** /v1/calendars/{id} | Update a calendar
*CalendarsApi* | [**updateCalendarEvent**](docs/Api/CalendarsApi.md#updatecalendarevent) | **PATCH** /v1/calendars/{id}/events/{eventId} | Update a calendar event
*CalendarsApi* | [**updateCalendarIntegration**](docs/Api/CalendarsApi.md#updatecalendarintegration) | **PATCH** /v1/calendar-integrations/{id} | Update a calendar integration
*CalendarsApi* | [**updateCalendarMember**](docs/Api/CalendarsApi.md#updatecalendarmember) | **PATCH** /v1/calendars/{id}/members/{memberId} | Update a calendar member&#39;s role
*CalendarsApi* | [**updateCalendarPolicies**](docs/Api/CalendarsApi.md#updatecalendarpolicies) | **PATCH** /v1/calendar-policies | Update calendar policies
*ContactListsApi* | [**addContactListMember**](docs/Api/ContactListsApi.md#addcontactlistmember) | **POST** /v1/contact-lists/{id}/members | Add a member to a contact list
*ContactListsApi* | [**createContactList**](docs/Api/ContactListsApi.md#createcontactlist) | **POST** /v1/contact-lists | Create a contact list
*ContactListsApi* | [**deleteContactList**](docs/Api/ContactListsApi.md#deletecontactlist) | **DELETE** /v1/contact-lists/{id} | Delete a contact list
*ContactListsApi* | [**getContactList**](docs/Api/ContactListsApi.md#getcontactlist) | **GET** /v1/contact-lists/{id} | Get a contact list with members
*ContactListsApi* | [**listContactLists**](docs/Api/ContactListsApi.md#listcontactlists) | **GET** /v1/contact-lists | List contact lists
*ContactListsApi* | [**removeContactListMember**](docs/Api/ContactListsApi.md#removecontactlistmember) | **DELETE** /v1/contact-lists/{id}/members/{contactId} | Remove a member from a contact list
*ContactListsApi* | [**updateContactList**](docs/Api/ContactListsApi.md#updatecontactlist) | **PATCH** /v1/contact-lists/{id} | Update a contact list
*ContactsApi* | [**createContact**](docs/Api/ContactsApi.md#createcontact) | **POST** /v1/contacts | Create a contact
*ContactsApi* | [**deleteContact**](docs/Api/ContactsApi.md#deletecontact) | **DELETE** /v1/contacts/{id} | Delete a contact
*ContactsApi* | [**getContact**](docs/Api/ContactsApi.md#getcontact) | **GET** /v1/contacts/{id} | Get a contact
*ContactsApi* | [**getContactLists**](docs/Api/ContactsApi.md#getcontactlists) | **GET** /v1/contacts/{id}/lists | Get lists a contact belongs to
*ContactsApi* | [**listContacts**](docs/Api/ContactsApi.md#listcontacts) | **GET** /v1/contacts | List contacts
*ContactsApi* | [**updateContact**](docs/Api/ContactsApi.md#updatecontact) | **PATCH** /v1/contacts/{id} | Update a contact
*DashboardApi* | [**getAuditSummary**](docs/Api/DashboardApi.md#getauditsummary) | **GET** /v1/audit-summary | Audit summary for the dashboard
*DashboardApi* | [**getDomainsStatus**](docs/Api/DashboardApi.md#getdomainsstatus) | **GET** /v1/domains/status | Domain health status for the dashboard
*DashboardApi* | [**getIntegrationsSummary**](docs/Api/DashboardApi.md#getintegrationssummary) | **GET** /v1/integrations-summary | Integrations summary for the dashboard
*DashboardApi* | [**getSecurity**](docs/Api/DashboardApi.md#getsecurity) | **GET** /v1/security | Security overview for the dashboard
*DashboardApi* | [**getStorage**](docs/Api/DashboardApi.md#getstorage) | **GET** /v1/storage | Storage usage for the dashboard
*DashboardApi* | [**getTenantHealth**](docs/Api/DashboardApi.md#gettenanthealth) | **GET** /v1/health | Full tenant health report
*DashboardApi* | [**getUserInsights**](docs/Api/DashboardApi.md#getuserinsights) | **GET** /v1/user-insights | User insights for the dashboard
*DirectoryApi* | [**getDirectoryActivity**](docs/Api/DirectoryApi.md#getdirectoryactivity) | **GET** /v1/directory-activity | Get recent directory activity
*DirectoryApi* | [**getDirectoryPermissions**](docs/Api/DirectoryApi.md#getdirectorypermissions) | **GET** /v1/directory-permissions | Get directory permission settings
*DirectoryApi* | [**getDirectoryStats**](docs/Api/DirectoryApi.md#getdirectorystats) | **GET** /v1/directory-stats | Get directory statistics
*DirectoryApi* | [**getGALSettings**](docs/Api/DirectoryApi.md#getgalsettings) | **GET** /v1/gal-settings | Get Global Address List settings
*DirectoryApi* | [**rebuildGALIndex**](docs/Api/DirectoryApi.md#rebuildgalindex) | **POST** /v1/gal-settings/rebuild-index | Rebuild the GAL search index
*DirectoryApi* | [**syncGAL**](docs/Api/DirectoryApi.md#syncgal) | **POST** /v1/gal-settings/sync | Sync GAL with external directory sources
*DirectoryApi* | [**updateDirectoryPermissions**](docs/Api/DirectoryApi.md#updatedirectorypermissions) | **PATCH** /v1/directory-permissions | Update directory permission settings
*DirectoryApi* | [**updateGALSettings**](docs/Api/DirectoryApi.md#updategalsettings) | **PATCH** /v1/gal-settings | Update GAL settings
*DistributionListsApi* | [**createDistributionList**](docs/Api/DistributionListsApi.md#createdistributionlist) | **POST** /v1/distribution-lists | Create a distribution list
*DistributionListsApi* | [**deleteDistributionList**](docs/Api/DistributionListsApi.md#deletedistributionlist) | **DELETE** /v1/distribution-lists/{address} | Delete a distribution list
*DistributionListsApi* | [**getDistributionList**](docs/Api/DistributionListsApi.md#getdistributionlist) | **GET** /v1/distribution-lists/{address} | Get a distribution list
*DistributionListsApi* | [**listDistributionLists**](docs/Api/DistributionListsApi.md#listdistributionlists) | **GET** /v1/distribution-lists | List distribution lists
*DistributionListsApi* | [**replaceDistributionListMembers**](docs/Api/DistributionListsApi.md#replacedistributionlistmembers) | **PUT** /v1/distribution-lists/{address}/members | Replace distribution list members
*DomainsApi* | [**createDomain**](docs/Api/DomainsApi.md#createdomain) | **POST** /v1/domains | Register a domain
*DomainsApi* | [**deleteDomain**](docs/Api/DomainsApi.md#deletedomain) | **DELETE** /v1/domains/{domain} | Delete a domain
*DomainsApi* | [**disableReturnPath**](docs/Api/DomainsApi.md#disablereturnpath) | **DELETE** /v1/domains/{domain}/return-path | Turn off the custom Return-Path
*DomainsApi* | [**enableReturnPath**](docs/Api/DomainsApi.md#enablereturnpath) | **POST** /v1/domains/{domain}/return-path | Turn on the custom Return-Path
*DomainsApi* | [**getDomain**](docs/Api/DomainsApi.md#getdomain) | **GET** /v1/domains/{domain} | Get a domain
*DomainsApi* | [**getReturnPath**](docs/Api/DomainsApi.md#getreturnpath) | **GET** /v1/domains/{domain}/return-path | Get the custom Return-Path
*DomainsApi* | [**listDomains**](docs/Api/DomainsApi.md#listdomains) | **GET** /v1/domains | List domains
*DomainsApi* | [**verifyDomain**](docs/Api/DomainsApi.md#verifydomain) | **POST** /v1/domains/{domain}/verify | Force-poll DNS verification
*DomainsApi* | [**verifyReturnPath**](docs/Api/DomainsApi.md#verifyreturnpath) | **POST** /v1/domains/{domain}/return-path/verify | Check the custom Return-Path records
*DraftsApi* | [**approveDraft**](docs/Api/DraftsApi.md#approvedraft) | **POST** /v1/drafts/{draftID}/approve | Approve a pending draft (human)
*DraftsApi* | [**cancelDraft**](docs/Api/DraftsApi.md#canceldraft) | **POST** /v1/drafts/{draftID}/cancel | Withdraw a pending draft
*DraftsApi* | [**createConversationDraft**](docs/Api/DraftsApi.md#createconversationdraft) | **POST** /v1/inboxes/{mailbox}/drafts | Propose a new conversation as a draft
*DraftsApi* | [**createReplyDraft**](docs/Api/DraftsApi.md#createreplydraft) | **POST** /v1/threads/{threadID}/drafts | Propose a reply as a draft
*DraftsApi* | [**getDraft**](docs/Api/DraftsApi.md#getdraft) | **GET** /v1/drafts/{draftID} | Get a draft
*DraftsApi* | [**listDrafts**](docs/Api/DraftsApi.md#listdrafts) | **GET** /v1/drafts | List drafts
*DraftsApi* | [**rejectDraft**](docs/Api/DraftsApi.md#rejectdraft) | **POST** /v1/drafts/{draftID}/reject | Reject a pending draft (human)
*EncryptionApi* | [**batchLookupPublicKeys**](docs/Api/EncryptionApi.md#batchlookuppublickeys) | **GET** /v1/encryption/keys/lookup | Batch-lookup public keys by email
*EncryptionApi* | [**createEncryptionKey**](docs/Api/EncryptionApi.md#createencryptionkey) | **POST** /v1/encryption/keys | Upload an encryption key pair
*EncryptionApi* | [**createEncryptionRecovery**](docs/Api/EncryptionApi.md#createencryptionrecovery) | **POST** /v1/encryption/recovery | Store an encryption recovery blob
*EncryptionApi* | [**getEncryptionKey**](docs/Api/EncryptionApi.md#getencryptionkey) | **GET** /v1/encryption/keys/{email} | Get encryption key for a mailbox
*EncryptionApi* | [**rotateEncryptionKey**](docs/Api/EncryptionApi.md#rotateencryptionkey) | **POST** /v1/encryption/keys/rotate | Rotate an encryption key
*HealthApi* | [**healthCheck**](docs/Api/HealthApi.md#healthcheck) | **GET** /healthz | Liveness check
*IpPoolsApi* | [**createDedicatedIPRequest**](docs/Api/IpPoolsApi.md#creatededicatediprequest) | **POST** /v1/dedicated-ip-requests | Request a dedicated IP
*IpPoolsApi* | [**getIPAssignment**](docs/Api/IpPoolsApi.md#getipassignment) | **GET** /v1/ip-assignment | Get current IP assignment
*IpPoolsApi* | [**listDedicatedIPRequests**](docs/Api/IpPoolsApi.md#listdedicatediprequests) | **GET** /v1/dedicated-ip-requests | List dedicated IP requests
*MailboxesApi* | [**addSharedMember**](docs/Api/MailboxesApi.md#addsharedmember) | **POST** /v1/mailboxes/{email}/members | Add a shared mailbox member
*MailboxesApi* | [**createMailbox**](docs/Api/MailboxesApi.md#createmailbox) | **POST** /v1/mailboxes | Create a mailbox
*MailboxesApi* | [**deleteMailbox**](docs/Api/MailboxesApi.md#deletemailbox) | **DELETE** /v1/mailboxes/{email} | Soft-delete a mailbox
*MailboxesApi* | [**deleteVacationResponder**](docs/Api/MailboxesApi.md#deletevacationresponder) | **DELETE** /v1/mailboxes/{email}/vacation | Remove the vacation responder
*MailboxesApi* | [**downloadMailboxExport**](docs/Api/MailboxesApi.md#downloadmailboxexport) | **GET** /v1/mailboxes/{email}/export/download | Download a previously-issued mailbox export
*MailboxesApi* | [**exportMailbox**](docs/Api/MailboxesApi.md#exportmailbox) | **POST** /v1/mailboxes/{email}/export | Request a mailbox export
*MailboxesApi* | [**getMailbox**](docs/Api/MailboxesApi.md#getmailbox) | **GET** /v1/mailboxes/{email} | Get a mailbox
*MailboxesApi* | [**getVacationResponder**](docs/Api/MailboxesApi.md#getvacationresponder) | **GET** /v1/mailboxes/{email}/vacation | Get the vacation responder
*MailboxesApi* | [**listMailboxes**](docs/Api/MailboxesApi.md#listmailboxes) | **GET** /v1/mailboxes | List mailboxes
*MailboxesApi* | [**listSharedMembers**](docs/Api/MailboxesApi.md#listsharedmembers) | **GET** /v1/mailboxes/{email}/members | List shared mailbox members
*MailboxesApi* | [**listVacationResponders**](docs/Api/MailboxesApi.md#listvacationresponders) | **GET** /v1/vacation | List all vacation responders
*MailboxesApi* | [**removeSharedMember**](docs/Api/MailboxesApi.md#removesharedmember) | **DELETE** /v1/mailboxes/{email}/members/{memberEmail} | Remove a shared mailbox member
*MailboxesApi* | [**setVacationResponder**](docs/Api/MailboxesApi.md#setvacationresponder) | **PUT** /v1/mailboxes/{email}/vacation | Set the vacation responder
*MailboxesApi* | [**updateMailbox**](docs/Api/MailboxesApi.md#updatemailbox) | **PATCH** /v1/mailboxes/{email} | Update a mailbox
*MigrationsApi* | [**cancelMigration**](docs/Api/MigrationsApi.md#cancelmigration) | **POST** /v1/migrations/{id}/cancel | Cancel a running migration
*MigrationsApi* | [**checkMigrationDNS**](docs/Api/MigrationsApi.md#checkmigrationdns) | **GET** /v1/migrations/{id}/dns-check | Check DNS readiness for cutover
*MigrationsApi* | [**createMigration**](docs/Api/MigrationsApi.md#createmigration) | **POST** /v1/migrations | Create a migration
*MigrationsApi* | [**createMigrationCredential**](docs/Api/MigrationsApi.md#createmigrationcredential) | **POST** /v1/migrations/credentials | Store a migration credential
*MigrationsApi* | [**deleteMigration**](docs/Api/MigrationsApi.md#deletemigration) | **DELETE** /v1/migrations/{id} | Delete a migration
*MigrationsApi* | [**deleteMigrationCredential**](docs/Api/MigrationsApi.md#deletemigrationcredential) | **DELETE** /v1/migrations/credentials/{id} | Delete a migration credential
*MigrationsApi* | [**deltaSyncMigration**](docs/Api/MigrationsApi.md#deltasyncmigration) | **POST** /v1/migrations/{id}/delta-sync | Run a delta sync
*MigrationsApi* | [**discoverMigration**](docs/Api/MigrationsApi.md#discovermigration) | **POST** /v1/migrations/{id}/discover | Discover source mailboxes
*MigrationsApi* | [**finalSyncMigration**](docs/Api/MigrationsApi.md#finalsyncmigration) | **POST** /v1/migrations/{id}/final-sync | Run the final sync before cutover
*MigrationsApi* | [**getMigration**](docs/Api/MigrationsApi.md#getmigration) | **GET** /v1/migrations/{id} | Get a migration
*MigrationsApi* | [**getMigrationProgress**](docs/Api/MigrationsApi.md#getmigrationprogress) | **GET** /v1/migrations/{id}/progress | Get migration progress
*MigrationsApi* | [**listMigrationCredentials**](docs/Api/MigrationsApi.md#listmigrationcredentials) | **GET** /v1/migrations/credentials | List migration credentials
*MigrationsApi* | [**listMigrationEvents**](docs/Api/MigrationsApi.md#listmigrationevents) | **GET** /v1/migrations/{id}/events | List migration events
*MigrationsApi* | [**listMigrationMailboxes**](docs/Api/MigrationsApi.md#listmigrationmailboxes) | **GET** /v1/migrations/{id}/mailboxes | List migration mailboxes
*MigrationsApi* | [**listMigrations**](docs/Api/MigrationsApi.md#listmigrations) | **GET** /v1/migrations | List migrations
*MigrationsApi* | [**mapMigration**](docs/Api/MigrationsApi.md#mapmigration) | **POST** /v1/migrations/{id}/map | Map source to destination mailboxes
*MigrationsApi* | [**retryMigration**](docs/Api/MigrationsApi.md#retrymigration) | **POST** /v1/migrations/{id}/retry | Retry a failed or cancelled migration
*MigrationsApi* | [**startMigration**](docs/Api/MigrationsApi.md#startmigration) | **POST** /v1/migrations/{id}/start | Start the migration
*MigrationsApi* | [**updateMigration**](docs/Api/MigrationsApi.md#updatemigration) | **PATCH** /v1/migrations/{id} | Update a migration
*MigrationsApi* | [**updateMigrationMailbox**](docs/Api/MigrationsApi.md#updatemigrationmailbox) | **PATCH** /v1/migrations/{id}/mailboxes/{mbxId} | Update a migration mailbox
*MigrationsApi* | [**validateMigration**](docs/Api/MigrationsApi.md#validatemigration) | **POST** /v1/migrations/{id}/validate | Validate migrated data
*ResourcesApi* | [**createResource**](docs/Api/ResourcesApi.md#createresource) | **POST** /v1/resources | Create a resource
*ResourcesApi* | [**deleteResource**](docs/Api/ResourcesApi.md#deleteresource) | **DELETE** /v1/resources/{id} | Delete a resource
*ResourcesApi* | [**getResource**](docs/Api/ResourcesApi.md#getresource) | **GET** /v1/resources/{id} | Get a resource
*ResourcesApi* | [**listResources**](docs/Api/ResourcesApi.md#listresources) | **GET** /v1/resources | List resources
*ResourcesApi* | [**updateResource**](docs/Api/ResourcesApi.md#updateresource) | **PATCH** /v1/resources/{id} | Update a resource
*SendApi* | [**cancelMessage**](docs/Api/SendApi.md#cancelmessage) | **DELETE** /v1/messages/{id} | Cancel a scheduled send
*SendApi* | [**getMessage**](docs/Api/SendApi.md#getmessage) | **GET** /v1/messages/{id} | Get message status
*SendApi* | [**getMessageStats**](docs/Api/SendApi.md#getmessagestats) | **GET** /v1/messages/stats | Aggregate delivery stats
*SendApi* | [**listMessages**](docs/Api/SendApi.md#listmessages) | **GET** /v1/messages | List outbound messages
*SendApi* | [**sendEmail**](docs/Api/SendApi.md#sendemail) | **POST** /v1/send | Send an email
*SendApi* | [**sendEmailBatch**](docs/Api/SendApi.md#sendemailbatch) | **POST** /v1/send/batch | Send a batch of emails
*SignupApi* | [**signup**](docs/Api/SignupApi.md#signup) | **POST** /v1/signup | Sign up a new tenant
*SuppressionsApi* | [**createSuppression**](docs/Api/SuppressionsApi.md#createsuppression) | **POST** /v1/suppressions | Add a suppression
*SuppressionsApi* | [**deleteSuppression**](docs/Api/SuppressionsApi.md#deletesuppression) | **DELETE** /v1/suppressions/{email} | Remove a suppression
*SuppressionsApi* | [**getSuppression**](docs/Api/SuppressionsApi.md#getsuppression) | **GET** /v1/suppressions/{email} | Check whether an address is suppressed
*SuppressionsApi* | [**listSuppressions**](docs/Api/SuppressionsApi.md#listsuppressions) | **GET** /v1/suppressions | List suppressed recipients
*TemplatesApi* | [**createTemplate**](docs/Api/TemplatesApi.md#createtemplate) | **POST** /v1/templates | Create a template
*TemplatesApi* | [**deleteTemplate**](docs/Api/TemplatesApi.md#deletetemplate) | **DELETE** /v1/templates/{id} | Delete a template
*TemplatesApi* | [**getTemplate**](docs/Api/TemplatesApi.md#gettemplate) | **GET** /v1/templates/{id} | Get a template
*TemplatesApi* | [**listTemplates**](docs/Api/TemplatesApi.md#listtemplates) | **GET** /v1/templates | List templates
*TemplatesApi* | [**updateTemplate**](docs/Api/TemplatesApi.md#updatetemplate) | **PUT** /v1/templates/{id} | Update a template
*TenantApi* | [**getTenant**](docs/Api/TenantApi.md#gettenant) | **GET** /v1/tenant | Get the calling tenant
*TenantApi* | [**getUsage**](docs/Api/TenantApi.md#getusage) | **GET** /v1/usage | Usage snapshot
*TestApi* | [**simulateInboundEmail**](docs/Api/TestApi.md#simulateinboundemail) | **POST** /v1/test/inbound | Simulate an inbound email (test keys only)
*UsersApi* | [**createUser**](docs/Api/UsersApi.md#createuser) | **POST** /v1/users | Create a user
*UsersApi* | [**deleteUser**](docs/Api/UsersApi.md#deleteuser) | **DELETE** /v1/users/{id} | Delete a user
*UsersApi* | [**getUser**](docs/Api/UsersApi.md#getuser) | **GET** /v1/users/{id} | Get a user
*UsersApi* | [**listUsers**](docs/Api/UsersApi.md#listusers) | **GET** /v1/users | List users
*UsersApi* | [**updateUser**](docs/Api/UsersApi.md#updateuser) | **PATCH** /v1/users/{id} | Update a user
*WebhooksApi* | [**createWebhook**](docs/Api/WebhooksApi.md#createwebhook) | **POST** /v1/webhooks | Create a webhook
*WebhooksApi* | [**deleteWebhook**](docs/Api/WebhooksApi.md#deletewebhook) | **DELETE** /v1/webhooks/{id} | Delete a webhook
*WebhooksApi* | [**listWebhooks**](docs/Api/WebhooksApi.md#listwebhooks) | **GET** /v1/webhooks | List webhooks
*WebhooksApi* | [**updateWebhook**](docs/Api/WebhooksApi.md#updatewebhook) | **PATCH** /v1/webhooks/{id} | Update a webhook

## Models

- [APIKey](docs/Model/APIKey.md)
- [ActivateAddOn200Response](docs/Model/ActivateAddOn200Response.md)
- [AddCalendarMemberRequest](docs/Model/AddCalendarMemberRequest.md)
- [AddContactListMemberRequest](docs/Model/AddContactListMemberRequest.md)
- [AddOn](docs/Model/AddOn.md)
- [AddSharedMemberRequest](docs/Model/AddSharedMemberRequest.md)
- [Admin](docs/Model/Admin.md)
- [AdminFull](docs/Model/AdminFull.md)
- [AdminLogin200Response](docs/Model/AdminLogin200Response.md)
- [AdminLoginRequest](docs/Model/AdminLoginRequest.md)
- [AgentSendResult](docs/Model/AgentSendResult.md)
- [AiConfig](docs/Model/AiConfig.md)
- [AiConfigUpdate](docs/Model/AiConfigUpdate.md)
- [Alias](docs/Model/Alias.md)
- [Annotations](docs/Model/Annotations.md)
- [Attachment](docs/Model/Attachment.md)
- [AuditEvent](docs/Model/AuditEvent.md)
- [BatchLookupPublicKeys200Response](docs/Model/BatchLookupPublicKeys200Response.md)
- [BatchLookupPublicKeys200ResponseDataInner](docs/Model/BatchLookupPublicKeys200ResponseDataInner.md)
- [BatchResult](docs/Model/BatchResult.md)
- [BillingStatus](docs/Model/BillingStatus.md)
- [Calendar](docs/Model/Calendar.md)
- [CalendarEvent](docs/Model/CalendarEvent.md)
- [CalendarIntegration](docs/Model/CalendarIntegration.md)
- [CalendarMember](docs/Model/CalendarMember.md)
- [CalendarPolicies](docs/Model/CalendarPolicies.md)
- [Classification](docs/Model/Classification.md)
- [Contact](docs/Model/Contact.md)
- [ContactList](docs/Model/ContactList.md)
- [ContactLookup](docs/Model/ContactLookup.md)
- [ContactLookupContact](docs/Model/ContactLookupContact.md)
- [ContactLookupHistory](docs/Model/ContactLookupHistory.md)
- [CreateAiUnitsCheckout200Response](docs/Model/CreateAiUnitsCheckout200Response.md)
- [CreateAliasRequest](docs/Model/CreateAliasRequest.md)
- [CreateApiKey201Response](docs/Model/CreateApiKey201Response.md)
- [CreateApiKeyRequest](docs/Model/CreateApiKeyRequest.md)
- [CreateBillingCheckout200Response](docs/Model/CreateBillingCheckout200Response.md)
- [CreateBillingCheckoutRequest](docs/Model/CreateBillingCheckoutRequest.md)
- [CreateCalendarEventRequest](docs/Model/CreateCalendarEventRequest.md)
- [CreateCalendarIntegrationRequest](docs/Model/CreateCalendarIntegrationRequest.md)
- [CreateCalendarRequest](docs/Model/CreateCalendarRequest.md)
- [CreateContactListRequest](docs/Model/CreateContactListRequest.md)
- [CreateContactRequest](docs/Model/CreateContactRequest.md)
- [CreateDedicatedIPRequestRequest](docs/Model/CreateDedicatedIPRequestRequest.md)
- [CreateDistributionListRequest](docs/Model/CreateDistributionListRequest.md)
- [CreateDomainRequest](docs/Model/CreateDomainRequest.md)
- [CreateEncryptionKey201Response](docs/Model/CreateEncryptionKey201Response.md)
- [CreateEncryptionKeyRequest](docs/Model/CreateEncryptionKeyRequest.md)
- [CreateEncryptionRecoveryRequest](docs/Model/CreateEncryptionRecoveryRequest.md)
- [CreateMailboxRequest](docs/Model/CreateMailboxRequest.md)
- [CreateMigrationCredentialRequest](docs/Model/CreateMigrationCredentialRequest.md)
- [CreateMigrationCredentialRequestCredentials](docs/Model/CreateMigrationCredentialRequestCredentials.md)
- [CreateMigrationRequest](docs/Model/CreateMigrationRequest.md)
- [CreateResourceRequest](docs/Model/CreateResourceRequest.md)
- [CreateSuppressionRequest](docs/Model/CreateSuppressionRequest.md)
- [CreateUnitsCheckout200Response](docs/Model/CreateUnitsCheckout200Response.md)
- [CreateUnitsCheckoutRequest](docs/Model/CreateUnitsCheckoutRequest.md)
- [CreateUserRequest](docs/Model/CreateUserRequest.md)
- [CreateWebhookRequest](docs/Model/CreateWebhookRequest.md)
- [DNSRecord](docs/Model/DNSRecord.md)
- [DedicatedIPRequest](docs/Model/DedicatedIPRequest.md)
- [DirectoryPermissions](docs/Model/DirectoryPermissions.md)
- [DiscoverMigration202Response](docs/Model/DiscoverMigration202Response.md)
- [DistributionListDetail](docs/Model/DistributionListDetail.md)
- [DistributionListSummary](docs/Model/DistributionListSummary.md)
- [Domain](docs/Model/Domain.md)
- [Draft](docs/Model/Draft.md)
- [DraftList](docs/Model/DraftList.md)
- [DraftResult](docs/Model/DraftResult.md)
- [ExportMailbox201Response](docs/Model/ExportMailbox201Response.md)
- [GALSettings](docs/Model/GALSettings.md)
- [GetAddOnStatus200Response](docs/Model/GetAddOnStatus200Response.md)
- [GetAuditSummary200Response](docs/Model/GetAuditSummary200Response.md)
- [GetCalendarOverview200Response](docs/Model/GetCalendarOverview200Response.md)
- [GetCalendarOverview200ResponseActivityInner](docs/Model/GetCalendarOverview200ResponseActivityInner.md)
- [GetCalendarSecurity200Response](docs/Model/GetCalendarSecurity200Response.md)
- [GetCalendarSecurity200ResponseAlertsInner](docs/Model/GetCalendarSecurity200ResponseAlertsInner.md)
- [GetCalendarSecurity200ResponseDelegatedAccessInner](docs/Model/GetCalendarSecurity200ResponseDelegatedAccessInner.md)
- [GetCalendarSecurity200ResponseExternalSharing](docs/Model/GetCalendarSecurity200ResponseExternalSharing.md)
- [GetCalendarSecurity200ResponsePublicCalendarListInner](docs/Model/GetCalendarSecurity200ResponsePublicCalendarListInner.md)
- [GetContactList200Response](docs/Model/GetContactList200Response.md)
- [GetContactList200ResponseMembersInner](docs/Model/GetContactList200ResponseMembersInner.md)
- [GetContactLists200Response](docs/Model/GetContactLists200Response.md)
- [GetContactLists200ResponseDataInner](docs/Model/GetContactLists200ResponseDataInner.md)
- [GetCurrentAdmin200Response](docs/Model/GetCurrentAdmin200Response.md)
- [GetDirectoryActivity200Response](docs/Model/GetDirectoryActivity200Response.md)
- [GetDirectoryActivity200ResponseDataInner](docs/Model/GetDirectoryActivity200ResponseDataInner.md)
- [GetDirectoryStats200Response](docs/Model/GetDirectoryStats200Response.md)
- [GetDomainsStatus200Response](docs/Model/GetDomainsStatus200Response.md)
- [GetDomainsStatus200ResponseDomainsInner](docs/Model/GetDomainsStatus200ResponseDomainsInner.md)
- [GetDomainsStatus200ResponseDomainsInnerChecksInner](docs/Model/GetDomainsStatus200ResponseDomainsInnerChecksInner.md)
- [GetEncryptionKey200Response](docs/Model/GetEncryptionKey200Response.md)
- [GetIPAssignment200Response](docs/Model/GetIPAssignment200Response.md)
- [GetIntegrationsSummary200Response](docs/Model/GetIntegrationsSummary200Response.md)
- [GetIntegrationsSummary200ResponseApiKeysInner](docs/Model/GetIntegrationsSummary200ResponseApiKeysInner.md)
- [GetIntegrationsSummary200ResponseWebhooksInner](docs/Model/GetIntegrationsSummary200ResponseWebhooksInner.md)
- [GetSecurity200Response](docs/Model/GetSecurity200Response.md)
- [GetSecurity200ResponseAlertsInner](docs/Model/GetSecurity200ResponseAlertsInner.md)
- [GetSecurity200ResponseStatsInner](docs/Model/GetSecurity200ResponseStatsInner.md)
- [GetStorage200Response](docs/Model/GetStorage200Response.md)
- [GetStorage200ResponseTopMailboxesInner](docs/Model/GetStorage200ResponseTopMailboxesInner.md)
- [GetStorage200ResponseTopMessagesInner](docs/Model/GetStorage200ResponseTopMessagesInner.md)
- [GetUsage200Response](docs/Model/GetUsage200Response.md)
- [GetUserInsights200Response](docs/Model/GetUserInsights200Response.md)
- [HealthCheck200Response](docs/Model/HealthCheck200Response.md)
- [Inbox](docs/Model/Inbox.md)
- [InboxList](docs/Model/InboxList.md)
- [InjectionRisk](docs/Model/InjectionRisk.md)
- [InviteAdminRequest](docs/Model/InviteAdminRequest.md)
- [ListAddOns200Response](docs/Model/ListAddOns200Response.md)
- [ListAdmins200Response](docs/Model/ListAdmins200Response.md)
- [ListAliases200Response](docs/Model/ListAliases200Response.md)
- [ListApiKeys200Response](docs/Model/ListApiKeys200Response.md)
- [ListCalendarEvents200Response](docs/Model/ListCalendarEvents200Response.md)
- [ListCalendarIntegrations200Response](docs/Model/ListCalendarIntegrations200Response.md)
- [ListCalendarMembers200Response](docs/Model/ListCalendarMembers200Response.md)
- [ListCalendars200Response](docs/Model/ListCalendars200Response.md)
- [ListContactLists200Response](docs/Model/ListContactLists200Response.md)
- [ListContacts200Response](docs/Model/ListContacts200Response.md)
- [ListDedicatedIPRequests200Response](docs/Model/ListDedicatedIPRequests200Response.md)
- [ListDistributionLists200Response](docs/Model/ListDistributionLists200Response.md)
- [ListDomains200Response](docs/Model/ListDomains200Response.md)
- [ListMailboxes200Response](docs/Model/ListMailboxes200Response.md)
- [ListMessages200Response](docs/Model/ListMessages200Response.md)
- [ListMigrationCredentials200Response](docs/Model/ListMigrationCredentials200Response.md)
- [ListMigrationEvents200Response](docs/Model/ListMigrationEvents200Response.md)
- [ListMigrationMailboxes200Response](docs/Model/ListMigrationMailboxes200Response.md)
- [ListMigrations200Response](docs/Model/ListMigrations200Response.md)
- [ListResources200Response](docs/Model/ListResources200Response.md)
- [ListSharedMembers200Response](docs/Model/ListSharedMembers200Response.md)
- [ListSuppressions200Response](docs/Model/ListSuppressions200Response.md)
- [ListTemplates200Response](docs/Model/ListTemplates200Response.md)
- [ListUsers200Response](docs/Model/ListUsers200Response.md)
- [ListVacationResponders200Response](docs/Model/ListVacationResponders200Response.md)
- [ListWebhooks200Response](docs/Model/ListWebhooks200Response.md)
- [Mailbox](docs/Model/Mailbox.md)
- [MailboxGrant](docs/Model/MailboxGrant.md)
- [MailboxGrantList](docs/Model/MailboxGrantList.md)
- [MapMigrationRequest](docs/Model/MapMigrationRequest.md)
- [MapMigrationRequestMappingsInner](docs/Model/MapMigrationRequestMappingsInner.md)
- [MarkReadResult](docs/Model/MarkReadResult.md)
- [Message](docs/Model/Message.md)
- [MessageDetail](docs/Model/MessageDetail.md)
- [MessageStats](docs/Model/MessageStats.md)
- [MessageStatsCounts](docs/Model/MessageStatsCounts.md)
- [MessageStatsRates](docs/Model/MessageStatsRates.md)
- [MessageStatsWindow](docs/Model/MessageStatsWindow.md)
- [Migration](docs/Model/Migration.md)
- [MigrationCredential](docs/Model/MigrationCredential.md)
- [MigrationEvent](docs/Model/MigrationEvent.md)
- [MigrationMailbox](docs/Model/MigrationMailbox.md)
- [MigrationProgress](docs/Model/MigrationProgress.md)
- [MigrationProgressMailboxesInner](docs/Model/MigrationProgressMailboxesInner.md)
- [MigrationSettings](docs/Model/MigrationSettings.md)
- [PlanCatalogEntry](docs/Model/PlanCatalogEntry.md)
- [PolicyFlags](docs/Model/PolicyFlags.md)
- [Problem](docs/Model/Problem.md)
- [ReplaceDistributionListMembers200Response](docs/Model/ReplaceDistributionListMembers200Response.md)
- [ReplaceDistributionListMembersRequest](docs/Model/ReplaceDistributionListMembersRequest.md)
- [Resource](docs/Model/Resource.md)
- [ReturnPath](docs/Model/ReturnPath.md)
- [ReturnPathCheck](docs/Model/ReturnPathCheck.md)
- [RotateEncryptionKeyRequest](docs/Model/RotateEncryptionKeyRequest.md)
- [SendEmail200Response](docs/Model/SendEmail200Response.md)
- [SendEmail202Response](docs/Model/SendEmail202Response.md)
- [SendEmailBatch200Response](docs/Model/SendEmailBatch200Response.md)
- [SendEmailBatchRequest](docs/Model/SendEmailBatchRequest.md)
- [SendEmailRequest](docs/Model/SendEmailRequest.md)
- [SendEmailRequestAttachmentsInner](docs/Model/SendEmailRequestAttachmentsInner.md)
- [SendMessage](docs/Model/SendMessage.md)
- [SetVacationResponderRequest](docs/Model/SetVacationResponderRequest.md)
- [SharedMember](docs/Model/SharedMember.md)
- [SignupRequest](docs/Model/SignupRequest.md)
- [SimulatedInbound](docs/Model/SimulatedInbound.md)
- [StartConversationRequest](docs/Model/StartConversationRequest.md)
- [StartMigration202Response](docs/Model/StartMigration202Response.md)
- [Suppression](docs/Model/Suppression.md)
- [Template](docs/Model/Template.md)
- [TemplateInput](docs/Model/TemplateInput.md)
- [Tenant](docs/Model/Tenant.md)
- [Thread](docs/Model/Thread.md)
- [ThreadClassification](docs/Model/ThreadClassification.md)
- [ThreadList](docs/Model/ThreadList.md)
- [ThreadMessage](docs/Model/ThreadMessage.md)
- [ThreadMessageBody](docs/Model/ThreadMessageBody.md)
- [ThreadMessageBodyAllOfBody](docs/Model/ThreadMessageBodyAllOfBody.md)
- [ThreadSummary](docs/Model/ThreadSummary.md)
- [UnitBundle](docs/Model/UnitBundle.md)
- [UpdateAdminRequest](docs/Model/UpdateAdminRequest.md)
- [UpdateCalendarEventRequest](docs/Model/UpdateCalendarEventRequest.md)
- [UpdateCalendarIntegrationRequest](docs/Model/UpdateCalendarIntegrationRequest.md)
- [UpdateCalendarMemberRequest](docs/Model/UpdateCalendarMemberRequest.md)
- [UpdateCalendarPoliciesRequest](docs/Model/UpdateCalendarPoliciesRequest.md)
- [UpdateCalendarRequest](docs/Model/UpdateCalendarRequest.md)
- [UpdateContactListRequest](docs/Model/UpdateContactListRequest.md)
- [UpdateContactRequest](docs/Model/UpdateContactRequest.md)
- [UpdateDirectoryPermissionsRequest](docs/Model/UpdateDirectoryPermissionsRequest.md)
- [UpdateGALSettingsRequest](docs/Model/UpdateGALSettingsRequest.md)
- [UpdateMailboxRequest](docs/Model/UpdateMailboxRequest.md)
- [UpdateMigrationMailboxRequest](docs/Model/UpdateMigrationMailboxRequest.md)
- [UpdateMigrationRequest](docs/Model/UpdateMigrationRequest.md)
- [UpdateResourceRequest](docs/Model/UpdateResourceRequest.md)
- [UpdateUserRequest](docs/Model/UpdateUserRequest.md)
- [UpdateWebhookRequest](docs/Model/UpdateWebhookRequest.md)
- [User](docs/Model/User.md)
- [UserEvent](docs/Model/UserEvent.md)
- [VacationParams](docs/Model/VacationParams.md)
- [VacationResponder](docs/Model/VacationResponder.md)
- [Webhook](docs/Model/Webhook.md)
- [Whoami](docs/Model/Whoami.md)

## Authorization

Authentication schemes defined for the API:
### bearerAuth

- **Type**: Bearer authentication (lk_live_<prefix>_<secret>)

### oauth2

- **Type**: `OAuth`
- **Flow**: `accessCode`
- **Authorization URL**: `https://api.lockally.com/oauth/authorize`
- **Scopes**: 
    - **inboxes:read**: Read agent-accessible mailboxes and threads
    - **inboxes:write**: Send and act on agent-accessible mailboxes

## Tests

To run the tests, use:

```bash
composer install
vendor/bin/phpunit
```

## Author

support@lockally.com

## About this package

This PHP package is automatically generated by the [OpenAPI Generator](https://openapi-generator.tech) project:

- API version: `0.1.0`
    - Package version: `0.3.1`
    - Generator version: `7.23.0`
- Build package: `org.openapitools.codegen.languages.PhpClientCodegen`
