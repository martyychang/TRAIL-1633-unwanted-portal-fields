# SFDX  App

This repo demonstrates a bug with Salesforce DX observed in Winter '19
and API 44.0, regarding the presence of unwanted `Account.IsCustomerPortal`
and `Contact.CanAllowPortalSelfReg` fields in new scratch orgs.

These two fields do _NOT_ deploy to any of our sandbox orgs, because those
two fields do not exist in any of our sandbox orgs (or in **production**).

## Dev, Build and Test

1. Clone this repo
2. Create a new scratch org using **config/project-scratch-def.json**
3. Push source to the new scratch org using `sfdx force:source:push`
4. Open the org with `sfdx force:org:open`
5. Enable field history tracking on the **Account Name** field (`Account.Name`)
   and **Contact Email** (`Contact.Email`) field
6. Pull source from the scratch org using `sfdx force:source:pull`

Expected Outcome | Actual Outcome
----- | -----
`Account.IsCustomerPortal` does not show up | Metadata for this field _does_ appear
`Customer.CanAllowPortalSelfReg` does not show up | Metadata for this field _does_ appear


## Resources

* "[Push Source to the Scratch Org][1]." _Salesforce DX Developer Guide_.

[1]: https://developer.salesforce.com/docs/atlas.en-us.sfdx_dev.meta/sfdx_dev/sfdx_dev_push_md_to_scratch_org.htm
