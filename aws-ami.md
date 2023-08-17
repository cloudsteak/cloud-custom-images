# AWS egyedi kép készítése (AMI)

Cloud-Shell alapú megoldást hoztam, mert azt böngészőben is a helyi gépen is el lehet végezni

1. Gép azonosítójának lekérdezése a `Name` címke alapján

```bash
aws ec2 describe-instances --query "Reservations[].Instances[].InstanceId" --filters "Name=tag:Name,Values=<Name címke értéke>"
```

2. Másold ki vágólapra az `i-********` értékét

3. Futtasd le a kép készítési parancsot úgy, hogy az `--instance-id` kpacsolónál az előbbi `i-********` értékét add meg.
```bash
aws ec2 create-image --instance-id <i-********> --name "CloudSteak_Ubuntu22.04-Apache2_20230817" --description "Apache web szerver | Ubuntu 22 | CloudSteak" --tag-specifications 'ResourceType=image,Tags=[{Key=Name,Value=CloudSteak_Ubuntu22.04-Apache2_20230817}]'
```