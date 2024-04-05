# YML OR YAML
YAML, often represented by the file extension ".yml" or ".yaml", stands for "YAML Ain't Markup Language." It's a human-readable data serialization format that is commonly used for configuration files, data exchange, and structuring data in various applications. YAML is designed to be easy to read and write, making it popular for settings and data where human readability is important. It uses indentation to denote structure, and supports a variety of data types like lists, dictionaries, and scalar values.

## KEY & VALUE
In YAML, a key-value pair is like a label attached to some information. The "key" is like the label, while the "value" is the actual information you want to associate with that label. It's a simple way to organize and represent data. For example:
```yaml
name: John
age: 30
```

## COMENTS

In YAML, comments are indicated using the # symbol. Anything after the # symbol on a line is considered a comment and is ignored by parsers. For example:

```yaml
# This is a comment
key: value  # This is also a comment
```

## Boolean Values and Numbers
In YAML, boolean values and numbers are represented as follows:

```yaml
## Boolean
is_active: true
is_valid: false
## Numbers
count: 10
price: 5.99
scientific_notation: 6.022e23
```

## LIST

In YAML, a list is like a collection of items, where each item can be of any data type. Lists are represented using hyphens -, and each item is listed below the hyphen with an optional space. 

**Example:**
```yaml
favorite_fruits:
  - apple
  - banana
  - orange

## NUMBER
numbers: [1, 2, 3, 4, 5]
## OR
ages:
  - 25
  - 30
  - 40

## STRING BOOLEAN
colors:
  - red
  - green
  - blue
  - true
  - false

## Mixed Data Types:

mixed_types:
  - "apple"
  - 42
  - true
  - null

## Nested Lists:
nested_lists:
  - [1, 2, 3]
  - ["a", "b", "c"]

## Lists of Maps:
list_of_maps:
  - name: John
    age: 25
  - name: Alice
    age: 30
## ABOVE EQUIVALENT IN JSON
{
  "list_of_maps": [
    {
      "name": "John",
      "age": 25
    },
    {
      "name": "Alice",
      "age": 30
    }
  ]
}

```

## DICTIONARY (MAP)
In YAML, a dictionary (also known as a mapping) is a collection of key-value pairs where each key is associated with a value. Dictionaries are represented using colon : to separate keys and values, and each key-value pair is listed on a new line with an optional space. Here's a simple explanation and example:

```yaml
details:
  name: Alice
  age: 25
  is_student: true

## Nested Dictionaries:
user:
  profile:
    name: Bob
    email: bob@example.com
    address:
      city: New York
      country: USA

## EQUIVALENT JSON OF ABOVE
{
    "user": {
        "profile": {
            "name": "Bob",
            "email": "bob@example.com",
            "address": {
                "city": "New York",
                "country": "USA"
            }
        }
    }
}

## Lists of Dictionaries:
employees:
  - name: John
    age: 30
    department: HR
  - name: Alice
    age: 25
    department: IT

## EQUIVALENT JSON OF ABOVE
{
    "employees": [
        {
            "name": "John",
            "age": 30,
            "department": "HR"
        },
        {
            "name": "Alice",
            "age": 25,
            "department": "IT"
        }
    ]
}
```