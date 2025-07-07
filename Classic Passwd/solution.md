This is probably the most easy challenge ever solved by me yet.

```bash
ltrace ./Challenge.Challenge
```

```C
printf("Insert your username: ")                                             = 22
__isoc99_scanf(0x55f97838901b, 0x7ffcb6b498b0, 0, 0Insert your username: idontknow
)                         = 1
strcpy(0x7ffcb6b49820, "idontknow")                                          = 0x7ffcb6b49820
strcmp("idontknow", "<REDACTED>")                                         = 40
puts("\nAuthentication Error"
Authentication Error
)                                               = 22
exit(0 <no return ...>
+++ exited (status 0) +++
```

The <REDACTED> is our way to the flag, use it and get the flag.