Open on [websequencediagrams.com](https://www.websequencediagrams.com/)

```text
title Retrieve Asset information (ASE.002)

participant Any
participant Agent
participant Dec. VM
participant Ocean DB

Any->Agent: Get an Asset (ASE.002)
note right of Any: Could be sent by any Actor

Agent->Agent: Validate assetId
Agent-->Any:HTTP 400 (bad request)

Agent->Dec. VM:Get asset info
note left of Dec. VM: Searching if Asset exists \n && contentState != 9

Dec. VM-->Agent:Asset doesn't exists
Agent-->Any:HTTP 404 (not found)

Dec. VM->Agent: Asset information

Agent-->Agent: Is Ocean DB enabled?

Ocean DB<-->Agent: Asset information
Agent-->Agent: Build Asset model

Agent->Any: HTTP 200 (Asset)



```