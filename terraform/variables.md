## Variables

* Terraform variables are like parameters if it is defined in variable block and does not contain `default` attribute. Then it will be prompted for the user input when you run the `terraform plan` or `terraform apply`

```hcl
variable "location" {
  type = string
  description = "Azure Location / Region to host infra" //This is shown as hint when prompted to provide input
  default     = "westeurope"

  validation {
    condition     = var.location == "westeurope" || var.location == "northeurope"
    error_message = "Sorry, but we only accept Location as westeurop or northeurope."
  }
}
```

#### Types of variable

* `null:` a value that represents absence or omission. If you set an argument of a resource to null, Terraform behaves as though you had completely omitted it — it will use the argument's default value if it has one, or raise an error if the argument is mandatory. null is most useful in conditional expressions, so you can dynamically omit an argument if a condition isn't met.

* Primitive types i.e. `string`, `number`, `bool`  

* Complex types 

1. Lists/tuples are represented by a pair of square brackets containing a comma-separated sequence of values, like `["a", 15, true]`.  
List literals can be split into multiple lines for readability, but always require a comma between values. A comma after the final value is allowed, but not required. Values in a list can be arbitrary expressions.

2. Maps/objects are represented by a pair of curly braces containing a series of <KEY> = <VALUE> pairs:

```
{
  name = "John"
  age  = 52
}
```
Key/value pairs can be separated by either a comma or a line break.
  
[refer for more](https://developer.hashicorp.com/terraform/language/expressions/type-constraints)
