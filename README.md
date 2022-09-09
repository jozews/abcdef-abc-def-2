# abcdef-abc-def-2
Solution to `abcdef = (abc + def) ** 2` where `abcdef` is a six digit number.

```
# Solution 1

for abcdef in range(100_000, 999_999 + 1):
    
    abc = int(abcdef / 1000)
    def_ = abcdef % 1000

    if abcdef == (abc + def_) ** 2:
        print(f"Found: {abcdef}")
            

# Solution 2 (slightly faster?)

from math import sqrt

for abc_plus_def in range(int(sqrt(100_000)), int(sqrt(999_999) + 1)):

    for abc in range(100, 999):

        def_ = abc_plus_def - abc

        if not def_ > 0:
            continue
        
        def_str = str(def_)

        while len(def_str) < 3:
            def_str = "0" + def_str

        abcdef = int(f"{abc}{def_str}")
        if abcdef == (abc + def_) ** 2:
            print(f"Found: {abcdef}")
```
