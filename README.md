# VPC Diagram

```mermaid
flowchart TB;
subgraph &nbsp;
rootPublicSubnet[PublicSubnet<br/>EC2::Subnet]-->rootMyVPC[MyVPC<br/>EC2::VPC]
rootPrivateSubnet[PrivateSubnet<br/>EC2::Subnet]-->rootMyVPC[MyVPC<br/>EC2::VPC]
rootAttachIGW[AttachIGW<br/>EC2::VPCGatewayAttachment]-->rootMyVPC[MyVPC<br/>EC2::VPC]
rootAttachIGW[AttachIGW<br/>EC2::VPCGatewayAttachment]-->rootInternetGateway[InternetGateway<br/>EC2::InternetGateway]
rootNATGateway[NATGateway<br/>EC2::NatGateway]-->rootPublicSubnet[PublicSubnet<br/>EC2::Subnet]
rootNATGateway[NATGateway<br/>EC2::NatGateway]-->rootEIPForNAT[EIPForNAT<br/>EC2::EIP]
rootPublicRouteTable[PublicRouteTable<br/>EC2::RouteTable]-->rootMyVPC[MyVPC<br/>EC2::VPC]
rootPrivateRouteTable[PrivateRouteTable<br/>EC2::RouteTable]-->rootMyVPC[MyVPC<br/>EC2::VPC]
rootPublicRoute[PublicRoute<br/>EC2::Route]-->rootPublicRouteTable[PublicRouteTable<br/>EC2::RouteTable]
rootPublicRoute[PublicRoute<br/>EC2::Route]-->rootInternetGateway[InternetGateway<br/>EC2::InternetGateway]
rootPrivateRoute[PrivateRoute<br/>EC2::Route]-->rootPrivateRouteTable[PrivateRouteTable<br/>EC2::RouteTable]
rootPrivateRoute[PrivateRoute<br/>EC2::Route]-->rootNATGateway[NATGateway<br/>EC2::NatGateway]
rootPublicEC2[PublicEC2<br/>EC2::Instance]-->rootPublicSubnet[PublicSubnet<br/>EC2::Subnet]
rootPrivateEC2[PrivateEC2<br/>EC2::Instance]-->rootPrivateSubnet[PrivateSubnet<br/>EC2::Subnet]
end
