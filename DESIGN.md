
# Commands
## Seed Commands

## Sync Commands

### Sync (Main Flow)

| Phase  | Activities   |
| :----- |:------------ |
| Begin Seed | _**A Sender**_ A Start Sync Request from either A or B (assume “A” is the requestor for this example) |
| Calculate Pair | **A (Sender):** Calculate Pair Name from Seed Request |
| <a name="05618054-ADF4-4170-A2AB-C45B36F6AFE7"> Get Config | _**A Sender**_ 1. Determine the the configuration bootstrap. 2. Send message [Seed Configuration Request](#DA4C78FF-4211-464E-8C78-6B099F87E55C). 3. Receive message [Seed Configuration Response](#260C18A0-2B6C-47D0-A7E2-529E8423B664). 
| <a name="FD0C10C7-0AE0-4F27-B6AC-AA18A5E9F4D4"> Block if Existing Session | _**A Sender**_ 1. Validation that no active sessions are underway for the pair locally. 2. Send [Validate No Active Session Request](#Validate-No-Active-Session-Request). _**B Receiver**_ 3. Validation that no active sessions are underway on for the pair locally. 4. Send [Validate No Active Session Response](#Validate-No-Active-Session-Response) _**A Sender**_ 5. Validation that no active sessions are underway for the pair remotely
| Create Session | _**A Sender**_ 1. Session id is created. 2. Persist session id locally. 3. Send Session Start Request _**B Receiver**_ 4. Persist session id locally. 5. Send Session Start Response (start “Check if Seeded”). _**A Sender**_ 6. Receive Session Start Response 
| <a name="4910908C-63E1-46F5-BFFF-E69B62EBC714"> Heart Beats | See algorithm [Heart Beat Checker](#CCF35108-AACD-46A0-9364-BAFD022D38DE) |
| Check if Seeded | _**A Sender**_ 1. Check if seeded (on both peers) 2. If NOT seeded on both peers, go to Phase Wait for Peer to Complete

# Algorithms
## Management and Error Recovery Algorithms
### <a name="CCF35108-AACD-46A0-9364-BAFD022D38DE"> Heart Beat Checker 
Used in: [Sync (Main Flow) • Heart Beats](#4910908C-63E1-46F5-BFFF-E69B62EBC714)

# Messages

## Seed Messages

### <a name="DA4C78FF-4211-464E-8C78-6B099F87E55C"> Seed Configuration Request
Used in: [Sync (Main Flow) • Get Config](#05618054-ADF4-4170-A2AB-C45B36F6AFE7)

| Name | Type | Repeating | Mandatory |
| ---- | ---- | --------- | --------- |
| Pair Name | String | False | True |
| Client Provided Id | String | False | False |
| Msg Type | Integer | False | True |

### <a name="73ED374F-B6DE-4FD4-B77F-750FBF3BF511"> Seed Configuration Request
Used in: [Sync (Main Flow) • Get Config](#05618054-ADF4-4170-A2AB-C45B36F6AFE7)

### <a name="260C18A0-2B6C-47D0-A7E2-529E8423B664"> Seed Configuration Response
Used in: [Sync (Main Flow) • Get Config](#05618054-ADF4-4170-A2AB-C45B36F6AFE7)

--- finish me ---

### <a name="Validate-No-Active-Session-Request"> Validate No Active Session Request
Used in: [Sync (Main Flow) • Block if Existing Session](#FD0C10C7-0AE0-4F27-B6AC-AA18A5E9F4D4)

--- finish me ---

| Name | Type | Repeating | Mandatory |
| ---- | ---- | --------- | --------- |
| Pair Name | String | False | True |
| Client Provided Id | String | False | False |
| Msg Type | Integer | False | True |

### <a name="Validate-No-Active-Session-Response"> Validate No Active Session Response
Used in: [Sync (Main Flow) • Block if Existing Session](#FD0C10C7-0AE0-4F27-B6AC-AA18A5E9F4D4)

--- finish me ---

| Name | Type | Repeating | Mandatory |
| ---- | ---- | --------- | --------- |
| Pair Name | String | False | True |
| Client Provided Id | String | False | False |
| Msg Type | Integer | False | True |

-
-
-
-
-
-
-
-
-
-
-
-
