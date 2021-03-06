# Transform your AWS VPN Generic Config to a Mikrotik set-up script

## Problem description
Unfortunately AWS doesn't support cheaper routers like one that we have(MikroTik) in my current startup company Smartup (http://smartup.io/).

We were struggling for a few days now to set up a VPN connection into AWS, because of a MikroTik limitation (http://rant.gulbrandsen.priv.no/mikrotik/ipsec-policy-bugs) and the lack of general documentation as well.

We have created a script that will transform your Generic (Vendor Agnostic) AWS VPN Configuration guide, that you can download from the AWS console into a MikroTik specific configuration script that you can copy-paste into your MikroTik SSH console.

Obviously, we are not accountable for any trouble that this causes to you or your organization, so use it on your own risk.

## Usage example
```
# You have to give the script one argument,
# the path of the file you downloaded from AWS
# Example:
[mate@devmate]$ ./static-router-config ~/Downloads/vpn-12345abc.txt

Type in local network CIDR (Enter to use guessed 192.168.1.0/24):
Type in your VPC CIDR [10.0.0.0/16]):

Your configuration will be created by using the following values
Your public adddress: 1.2.3.4
Your local network CIDR: 192.168.1.0/24
Your VPC's CIDR: 10.0.0.0/16

AWS Tunnel #1 - Public Address: 5.6.7.8
AWS Tunnel #1 - Inside Customer Gateway Address: 169.254.x.x
AWS Tunnel #1 - Inside Virtual Gateway Address: 169.254.x.x
AWS Tunnel #1 - Secret: THISISVEEEERYVEEERYSECRET

AWS Tunnel #2 - Public Address: 10.11.12.13
AWS Tunnel #2 - Inside Customer Gateway Address: 169.254.y.y
AWS Tunnel #2 - Inside Virtual Gateway Address: 169.254.y.y
AWS Tunnel #2 - Secret: THISISVEEEERYVEEERYSECRET

Is this correct(y/n)? y
Generate the config file in [./mikrotik-aws-config]:
Your config file has been generated in mikrotik-aws-config
```

Now just copy paste the contents of the generated config file into MikroTik's SSH console and you should be up and running.

> Note:
>
> Do not forget to add static routes from AWS back to your home network as well.
>
> Also, make sure you have your route tables correctly set up,
> and define routes back to your home network.

# Kudos
Kudos go out to these guys who wrote blog posts on this topic and shared my pain.
* http://biplane.com.au/blog/?p=406
* http://rant.gulbrandsen.priv.no/amazon/mikrotik-aws-ipsec

# Contributions
Feel free to fork and improve or contribute.

May the source be with you.
