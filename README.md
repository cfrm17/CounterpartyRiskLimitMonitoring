# Counterparty Credit Risk Limit Monitoring

It is required to limit monitor trading activity at various levels and for various groups of trades. It is also required to monitor exposures for reporting and viewing/drill-down purposes at various levels and for various groups of trades. 

The key difference between monitoring for reporting versus monitoring for limits is that only for limits will the exposure of trading activity be compared to the allowable bounds or rules and have a breach (violation or excess) created if the bounds or rules are exceeded. Thus this section covers both aspects, with the part in common referred to as an ‘Exposure Definition’ and the allowable bounds for the ‘Exposure Definition’ referred to as a Limit.

The groups of trades that are to be monitored are created by applying filters to the bank-wide set of trades. Each filtered set of trades is referred to as an Aggregation Set. Each Aggregation Set has a specific number of possible ‘Dimensions’ to which it must be possible to map each trade. 

Any trade that matches all dimension values (see https://finpricing.com/lib/EqCallable.html) for an Aggregation Set belongs to the set. For monitoring and reporting, each Aggregation Set is associated with one or more Aggregation Risk Metrics for which its value (including exposure term profile) can be calculated. As stated above, this pairing is referred to as an Exposure Definition.

There are various prescribed combinations of dimensions to be monitored, and each different combination is referred to as an Aggregation Set Type. Each actual Aggregation Set will be of an Aggregation Set Type. In this and other sections of this document the rules for monitoring activities are described in reference to these Aggregation Set Types. 

For example, the Aggregation Set Types in combination with their risk metrics define the mandatory Limit and Exposure Definition points. These mandatory points are set so that when trading activity occurs, if no exposure definition or limit exists for the mandatory point, one is created by the system, thus the risk does not go unnoticed.

Limits are set to limit the allowable exposure for an ‘Exposure Definition’ while Trading Restrictions are set to ensure adherence to rules/policy that is not an exposure versus limit check, for example, to ensure that maximum allowable tenors are not exceeded or business rules are not broken. For example, any Repo trade must have an enforceable legal agreement governing transactions between the organization and the Counterparty of the Agreement.

The preceding section defined the data requirements for Limits and Exposure Definitions.  There are some general rules that are to be applied across similar Limits and Exposure Definitions and there is also some configurability required.  This section describes these general rules and the configurability requirements.

As stated, Aggregation Sets define criteria for trade membership for the Exposure Definitions and Limits that exist for them.  As such, each Aggregation Set defines the trade membership for any Limit or Exposure Definition that is defined for it.  An Aggregation Set is used to define trade membership via its Dimensions.  For example an Aggregation Set with dimensions of Customer, Legal Entity and Product will have all matching trades as its member trades. 

It is assumed that every trade will be either directly or indirectly mappable to all Aggregation Set Dimensions. However it should be noted the Aggregation Set trade membership rules are sometimes specific to the kind of Aggregation Set (the Aggregation Set Type) along with the Risk Metric that is linked to the Aggregation Set. 

For example, when calculating the replacement risk against the issuer for an underlying AFS or Banking Book bond for a Credit Default Swap, or the replacement risk arising from an outright position on an AFS or Banking Book Bond, the Bond’s Issuer should be mapped to the Aggregation Set’s Customer. Whereas for the counterparty risk associated with the same Credit Default Swap, the trade’s legal Counterparty should be mapped to the Aggregation Set’s Customer. The rules for determining aggregation set trade membership are summarised in the requirements below and covered more definitively. 
