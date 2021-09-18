# Transit gateway

-> Transit gateway is a network transit hub that you can use to interconnect your VPC and on-prem.

-> This solution can also handle transitive routing.

-> VPC using this solution will need a VPN Gateway.

-> It is highly available and scalable

-> Attachments to other network types

-> It uses route tables with routing information.

-> Can be used to create global network.

-> Share between accounts using AWS RAM

-> You can peer TGW (Tansist Gateway) with different region in same account or cross account. No limitation.

-> Less complexity with respect to Network arch.


## Key concepts of transit gateway

- **Attachment**: You can attach a direct connected gateway or VPC to transit gateway.

- **Transit gateway MTU**: A tansit gateway supports an MTU of 8500 bytes traffic between VPCs, Direct connects and peering attachments.

