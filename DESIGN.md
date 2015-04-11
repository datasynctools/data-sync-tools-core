
# Commands
## Seed
1. Either node initializes a [Sync Request](#syncRequest)
2. Originator creates session id
3. three

_italic_ 

## Sync Commands

### Sync (Main Flow)

| Phase  | Activities   |
| :----- |:------------ |
| Begin Seed | _**A Sender**_ -> A Start Sync Request from either A or B (assume “A” is the requestor for this example) |
| Calculate Pair | **A (Sender):** Calculate Pair Name from Seed Request |
| Get Config <a name="05618054-ADF4-4170-A2AB-C45B36F6AFE7"> | _**A Sender**_ 1. Determine the the configuration bootstrap. 2. Send message [Seed Configuration Request](#DA4C78FF-4211-464E-8C78-6B099F87E55C). 3. Receive message Seed Configuration Response. 
| Block if Existing Session | _**A Sender**_ 1. Validation that no active sessions are underway for the pair locally. 2. Send Validate No Active Session Request. _**B Receiver**_ 3. Validation that no active sessions are underway on for the pair locally. 4. Send Validate No Active Session Response _**A Sender**_ 5. Validation that no active sessions are underway for the pair remotely
| Create Session | _**A Sender**_ 1. Session id is created. 2. Persist session id locally. 3. Send Session Start Request _**B Receiver**_ 4. Persist session id locally. 5. Send Session Start Response (start “Check if Seeded”). _**A Sender**_ 6. Receive Session Start Response 
| Heart Beats | See algorithm [Heart Beat Checker](#CCF35108-AACD-46A0-9364-BAFD022D38DE) |
| Check if Seeded | _**A Sender**_ 1. Check if seeded (on both peers) 2. If NOT seeded on both peers, go to Phase Wait for Peer to Complete

# Algorithms
## Management and Error Recovery Algorithms
### Heart Beat Checker <a name="CCF35108-AACD-46A0-9364-BAFD022D38DE"> 
--- finish me ---


# Messages

## Seed Messages

### Seed Configuration Request <a name="DA4C78FF-4211-464E-8C78-6B099F87E55C">
Used in: [Sync (Main Flow) • Get Config](#05618054-ADF4-4170-A2AB-C45B36F6AFE7)

| Name | Type | Repeating | Mandatory |
| ---- | ---- | --------- | --------- |
| Pair Name | String | False | True |
| Client Provided Id | String | False | False |
| Msg Type | Integer | False | True |



# Interfaces

## <a name="syncRequest"></a>Sync Request
```java
public class SyncSession {

  public seed() {
  }
}
```

| Left-Aligned  | Center Aligned  | Right Aligned |
| :------------ |:---------------:| -----:|
| col 3 is      | some wordy text | $1600 |
| col 2 is      | centered        |   $12 |
| test |
| zebra stripes | are neat        |    $1 |


Node A  | Node B
------------- | -------------
(either side initializes)  | (either side initializes)
test me

Content Cell  | Content Cell
