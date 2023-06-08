# Chaining for_each Between Resources
Because a resource using `for_each` appears as a **map of objects** when used in expressions elsewhere, you can directly use one resource as the `for_each` of another in situations where there is a one-to-one relationship between two sets of objects.

For example, in AWS an aws_vpc object is commonly associated with a number of other objects that provide additional services to that VPC, such as an "internet gateway". If you are declaring multiple VPC instances using for_each then you can chain that for_each into another resource to declare an internet gateway for each VPC.

This chaining pattern explicitly and concisely declares the relationship between the internet gateway instances and the VPC instances, which tells Terraform to expect the instance keys for both to always change together, and typically also makes the configuration easier to understand for human maintainers.

TODO put into terraform techniques/patterns repo