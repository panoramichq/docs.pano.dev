# Generating some common fields

## Renaming Campaigns

`IFF(CONTAINS(campaign_name, “BC”, “Birth”), “Birth Control”, campaign_name)` 

so that says “if campaign name contains “BC” or “Birth” then call it “Birth Control” otherwise use the existing campaign name

