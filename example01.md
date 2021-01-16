##### 01-Read input from user on shell
```html
#!/bin/bash
printf "what do you get 6*7 ?"
read answer
  if test "$answer" = "42"; then
    echo "You are correct"
  else
    echo "You are wrong"
  fi ```

