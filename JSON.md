3/1/2022

lecture notes link: https://web.eecs.utk.edu/~jplank/plank/classes/cs302/Notes/JSON/
---
# General:

all you need to do is: #include "nlohmann/json.hpp"

JSON is pretty flexible -- a number, boolean or a quoted string is a valid piece of JSON. The two more complex pieces of JSON are the array and the key/value store (referred to as an "object"). 

The following strings are all valid JSON:
- 55                                       # Number
- -23.45                                   # Number
- true                                     # Boolean
- "Fred"                                   # String
- [ 1, 2, "Fred" ]                         # Array with three elements
- { "Name": "Jim", "Age": 100 }            # Key/Value "object" with two keys/values.


You may nest arrays and objects in arrays and objects, giving you a flexible hierarchy. For example, the code below contains a key/value store with two keys
"Jim" and "Brad". Each of them have objects as their values. I'm representing Brad's children with an empty JSON array.

```

{ "Jim" : { "Last": "Plank", 
            "Age": "Infinity",
            "Children": [ "Katie", "Emily", "Ellen", "Jeff" ] },
  "Brad" : { "Last": "Vander Zanden",
             "Age": 55,
            "Children": []}}
```

---
# Reading and "Dumping" JSON:

.dump() turns into string



```
/* Read JSON from standard input, and then use dump(2) to write it indented by two spaces. */

#include "nlohmann/json.hpp"
#include <iostream>
using namespace std;
using nlohmann::json;

int main()
{
  json js;

  cin >> js;
  
  cout << js.dump(2) << endl;
  return 0;
}
```

---
# Enumerating JSON keys

You can use an iterator to enumerate the keys in a JSON object. but you must use a cosnt iterator

```
/* This program uses an iterator to enumerate the keys inside a JSON object.
   For each key, it prints:
     - The key and val, if the val is a number or string.
     - The key and val size if the val is an object or array.
 */
   
#include "nlohmann/json.hpp"
#include <iostream>
using namespace std;
using nlohmann::json;

int main()
{
  json js;
  json::const_iterator jit;

  /* Read the json from standard input. */

  cin >> js;
  
  /* If it's not an object, print an error message and exit. */

  if (!js.is_object()) {
    cout << "Not a JSON object: " << js << endl;
    return 0;
  } 

  /* Otherwise, run through the keys with an iterator and print them. */

  for (jit = js.begin(); jit != js.end(); jit++) {
    printf("Key: %-10s ", jit.key().c_str());
    if (jit.value().is_string() || jit.value().is_number()) {
      cout << "Value: " << jit.value() << endl;
    } else if (jit.value().is_object() || jit.value().is_array()) {
      cout << "Size: " << jit.value().size() << endl;
    } else {
      cout << "Unknown value type.\n";
    }
  }
  return 0;
}
```

---
# Hardcode json in code

you can hard code the json data within the program like so

```
static json j = {
         { "first", "Tiger" },
         { "last", "Woods" },
         { "wins", 82 },
         { "majors", 15 },
         { "masters-wins", { 1997, 2001, 2002, 2005, 2019 } },  // These are arrays.
         { "pga-wins", { 1999, 2000, 2006, 2007 } },
         { "us-open-wins", { 2000, 2002, 2008 } },
         { "british-open-wins", { 2000, 2005, 2006} } 
         };

```

printed and sorted:

```
{
  "british-open-wins": [
    2000,
    2005,
    2006
  ],
  "first": "Tiger",
  "last": "Woods",
  "majors": 15,
  "masters-wins": [
    1997,
    2001,
    2002,
    2005,
    2019
  ],
  "pga-wins": [
    1999,
    2000,
    2006,
    2007
  ],
  "us-open-wins": [
    2000,
    2002,
    2008
  ],
  "wins": 82
}
```
---
# Other JSON methods

- parse() - will parse a string
- contains(key) -  returns if key is in the json
- find(key) - returns iterator to val
- erase(key) - erases key/val pair from json


### other type checking methods:
- j.is_null();
- j.is_boolean();
- j.is_number();
- j.is_object();
- j.is_array();
- j.is_string();