

## Solution to `abcdef = (abc + def) ** 2` where `abcdef` is a six digit number.


    import time


### Solution 1
#### Time 0.42408013343811035, iterations 900000

    count_iterations = 0
    time_start = time.time()

    for abcdef in range(100_000, 999_999 + 1):

        abc = int(abcdef / 1000)
        def_ = abcdef % 1000

        if abcdef == (abc + def_) ** 2:
            print(f"Found: {abcdef}")

        count_iterations += 1

    elapsed = time.time() - time_start
    print(f"Time {elapsed}, iterations {count_iterations}")


### Solution 2 - Fastest
#### Time 0.19486093521118164, iterations 313614
#### Does not finds 998001 unless we zero-pad numbers

    from math import sqrt

    count_iterations = 0
    time_start = time.time()

    for abc_plus_def in range(int(sqrt(100_000)), int(sqrt(999_999) + 1)):

        for abc in range(100, 999):

            def_ = abc_plus_def - abc

            if def_ < 100:
                break

            abcdef = int(f"{abc}{def_}")
            if abcdef == (abc + def_) ** 2:
                print(f"Found: {abcdef}")

            count_iterations += 1

    elapsed = time.time() - time_start
    print(f"Time {elapsed}, iterations {count_iterations}")


### Solution 3
#### Time 0.4392850399017334, iterations 810000
#### Does not finds 998001 unless we zero-pad numbers

#### x = abc
#### y = def
#### abcdef = x * 1_000 + y
#### x * 1_000 + y = (x + y) ** 2

    count_iterations = 0
    time_start = time.time()

    for abc in range(100, 999 + 1):

        for def_ in range(100, 999 + 1):

            abcdef = int(f"{abc}{def_}")
            if abcdef == (abc + def_) ** 2:
                print(f"Found: {abcdef}")

            count_iterations += 1

    elapsed = time.time() - time_start
    print(f"Time {elapsed}, iterations {count_iterations}")
