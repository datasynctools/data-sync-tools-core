
# Commands
## Seed Commands

## Sync Commands

### Sync (Main Flow)

| Phase  | Activities   |
| :----- |:------------ |
| Begin Sync | _**A Sender**_ A Start Sync Request from either A or B (assume “A” is the requestor for this example) |
| Calculate Pair | **A (Sender):** Calculate Pair Name from Seed Request |
| <a name="Get-Config"> Get Config | _**A Sender**_ 1. Determine the the configuration bootstrap. 2. Send message [Seed Configuration Request](#Seed-Configuration-Request). 3. Receive message [Seed Configuration Response](#Seed-Configuration-Response). 
| <a name="Block-if-Existing-Session"> Block if Existing Session | _**A Sender**_ 1. Validation that no active sessions are underway for the pair locally. 2. Send [Validate No Active Session Request](#Validate-No-Active-Session-Request). _**B Receiver**_ 3. Validation that no active sessions are underway on for the pair locally. 4. Send [Validate No Active Session Response](#Validate-No-Active-Session-Response) _**A Sender**_ 5. Validation that no active sessions are underway for the pair remotely
| Create Session | _**A Sender**_ 1. Session id is created. 2. Persist session id locally. 3. Send Session Start Request _**B Receiver**_ 4. Persist session id locally. 5. Send Session Start Response (start “Check if Seeded”). _**A Sender**_ 6. Receive Session Start Response 
| <a name="Heart-Beats"> Heart Beats | See algorithm [Heart Beat Checker](#Heart-Beat-Checker) |
| Check if Seeded | _**A Sender**_ 1. Check if seeded (on both peers) 2. If NOT seeded on both peers, go to Phase [Wait for Peer to Complete](#Sync-Main-Flow-Wait-for-Peer-to-Complete)
| Syncing (Main) | _Old Session Recovery Check:_ Run algorithm Old Session Recovery Check, if it’s false continue. If it’s true, run Sync (Recovery Flow) and then go to Phase Wait for Peer to Complete. <br><br> _First Time Check:_ Run algorithm First Time Syncing Check, if it’s false continue. If it’s true, run Sync (First Time Flow) and and to go Phase Wait for Peer to Complete. <br><br> _Normal Flow Check:_ Run algorithm Normal Syncing Check, if it’s true, run Sync (Normal Flow) and then go to Phase Wait for Peer to Complete. If it’s false this is an unknown state. --- add unknown state error state --- |
| <a name="Sync-Main-Flow-Wait-for-Peer-to-Complete">Wait for Peer to Complete | |
| End Sync | |

### Sync (Normal Flow)

| Phase  | Activities   |
| :----- |:------------ |
| Syncing (Normal Flow) | _**A Sender**_ <br>For Each Sync State Table { <br><br> wait until we’re sure that the other side is ready to process the same table as me <br><br> For Each Sync State Table Record by Table { <br><br> 1. Read Local Sync State (Normal) (todo: this needs to be scalable to millions of records, using database cursors or other such technique.) <br> 2. Translate data message format for storage format to transmission format, if different (see table sync_node / field “Sync Data Persist Form” and table sync_node / field “Sync Data Trans Form”) <br> 3. Apply messages data format, message security policy (see table sync_node / field “Sync Msg Trans Form” and table sync_node / field “Sync Msg Sec Pol”) <br> 4. Continue reading local sync state until a message batch size is reached, a loop (see e table sync_node / field “In Msg Batch Size” / field “Max Out Msg Batch Size”) <br>5. Mark the local table sync_peer_state with field Sent Sync to 1 <br>6. Send the message batch to peer (see sync data change batch request) <br><br> _**B Receiver**_ <br> 1. Receive message batch on peer, apply message security policy to access the message, and apply message data format to native format conversion <br> 2. Process sync on Peer <br><br> _Add Sync Request Process Check:_ <br><br> _Update Sync Request Process Check:_ <br><br> _Delete Sync Request Process Check:_ <br><br> _**B Sender**_ <br>Package up and send Response (see Seed Data Batch Response) <br><br> _**A Receiver**_ <br> 1. Receive Response <br> 2. Apply response batch to local table sync_peer_state <br><br> _Add Sync Response Process Check:_ <br><br>_Update Sync Response Process Check:_ <br><br> _Delete Sync Response Process Check:_









# Algorithms
## Management and Error Recovery Algorithms
### <a name="Heart-Beat-Checker"> Heart Beat Checker 
Used in: [Sync (Main Flow) • Heart Beats](#Heart-Beats)

# Messages

## Seed Messages

### <a name="Seed-Configuration-Request"> Seed Configuration Request
Used in: [Sync (Main Flow) • Get Config](#Get-Config)

--- finish me ---

### <a name="Seed-Configuration-Response"> Seed Configuration Response
Used in: [Sync (Main Flow) • Get Config](#Get-Config)

--- finish me ---

### <a name="Validate-No-Active-Session-Request"> Validate No Active Session Request
Used in: [Sync (Main Flow) • Block if Existing Session](#Block-if-Existing-Session)

--- finish me ---

| Name | Type | Repeating | Mandatory |
| ---- | ---- | --------- | --------- |
| Pair Name | String | False | True |
| Client Provided Id | String | False | False |
| Msg Type | Integer | False | True |

### <a name="Validate-No-Active-Session-Response"> Validate No Active Session Response
Used in: [Sync (Main Flow) • Block if Existing Session](#Block-if-Existing-Session)

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
