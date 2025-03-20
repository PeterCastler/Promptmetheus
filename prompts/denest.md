# **How to Denest Code**

There are two ways you can denest:
*1. Extraction*
This is where you pull out a function into its own function.

*2. Inversion*
This is simply flipping conditions and switching to an early return.

Example:

```before_extraction
int calculate(int bottom, int top)
{
    if (top > bottom)
    {
        int sum = 0;

        for (int number = bottom; number <= top; number++)
        {
            if (number %2 == 0)
            {
                sum += number;
            }
        }

        return sum;
    }
    else
    {
        return 0;
    }
}
```

```after_extraction
int filterNumber(int number)
{
    if (number %2 == 0)
    {
        return number;
    }

    return 0;
}

int calculate(int bottom, int top)
{
    if (top > bottom)
    {
        int sum = 0;

        for (int number = bottom; number <= top; number++)
        {
            sum += filterNumber(number);
        }

        return sum;
    }
    else
    {
        return 0;
    }
}
```

Now we can apply inversion.
When you put the happy path of code within deeper and deeper blocks, it creates a lot of nesting.
Instead, we'll invert that condition and put the unhappy first.
First, we'll flip our if/else by inverting the condition. This eliminates the need for the else block and allows us to flatten our else into the main level. Now, if our unhappy condition is hit, we simply get out of the way and the main part of the code can do its job.

```after_inversion
int filterNumber(int number)
{
    if (number %2 == 0)
    {
        return number;
    }

    return 0;
}

int calculate(int bottom, int top)
{
    if (top <= bottom)
    {
        return 0;
    }

    int sum = 0;
    
    for (int number = bottom; number <= top; number++)
    {
        sum += filterNumber(number);
    }

        return sum;
}
```

When you have a lot of conditions to check (see below):

```too_many_conditions
void registerUser(String user)
{
    String[] parts = user.split(":");
    
    if (parts.length == 2)
    {
        int userID = Integer.parseInt(parts[0]);

        if (userID >= 0)
        {
            String userName = parts[1];

            if (users.containsKey(userID))
            {
                users.get(userId).setName(userName);
            }
            else
            {
                users.put(userId, new User(userName));
            }
        }
        else
        {
            throw new IllegalArgumentException("Invalid user id: " + userId);
        }
    }
    else
    {
        throw new IllegalArgumentException("Invalid user string: " + user);
    }
}
```

We can apply inversion over and over again until we end up with a "validation gatekeeping section" of the code which declares the requirements of the function. And then we have the crux of the real functionality at the bottom.

```after_inversion
void registerUser(String user)
{
    String[] parts = user.split(":");

    if (parts.length != 2)
    {
        throw IllegalArgumentException("Invalid user string: " + user);
    }

    int userId = Integer.parseInt(parts[0]);

    if (userId < 0)
    {
        throw new IllegalArgumentException("Invalid user id: " + userId);
    }

    String userName = parts[1];

    if (users.containsKey(userId))
    {
        users.get(userId).setName(userName);
    }
    else
    {
        users.put(userId, new User(userName));
    }

}

```

The happy path moves down the function and all the error paths are indented. When reading the code above, we can mentally discard the condition and focus on the core code. When we read them while they are nested, we end up having to hold too many ideas in our head.



