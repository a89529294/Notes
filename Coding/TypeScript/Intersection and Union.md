Both `intersection` and `union` follows the distributive law

The following are *equivalent*
- type T1 = IsAdmin & (User | Cat);
- type T2 = (IsAdmin & User) | (IsAdmin & Cat);
- 
We can switch the `&` and `|`, they are still *equivalent*
- type T1 = IsAdmin | (User & Cat);
- type T2 = (IsAdmin | User) & (IsAdmin | Cat);