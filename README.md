# Deno cross account R53 resolver sharing
## Deploy
```
terraform init
```
```
terraform apply
```
## Testing
```
rm -rf ./key.pem
terraform output -raw private_key >key.pem
chmod 400 ./key.pem
```

## DNS testing
```
ssh -i ./key.pem ubuntu@<jumpbox>
```
```
dig www.radarhack.com
...
dig demo.radarhacker.com  #DNS forward to DigitalOceans hosted zone
...
dig testing.radarhacker.com  #DNS forward to DigitalOceans hosted zone
...
dig my-instance.demo-radarhack.internal #r53 internal zone
```

## Check invite
Invite should be send to other account.

## TODO
The other account can access
```
dig www.radarhack.com
...
dig demo.radarhacker.com  #DNS forward
...
dig testing.radarhacker.com  #DNS forward
...
dig my-instance.demo-radarhack.internal # not configured r53 internal zone ... adding a rule to inbound endpoints will solve
```