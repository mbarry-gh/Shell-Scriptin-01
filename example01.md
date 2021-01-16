##### 01-Read input from user on shell
```html
#!/bin/bash
printf "what do you get 6*7 ?"
read answer
  if test "$answer" = "42"; then
    echo "You are correct"
  else
    echo "You are wrong"
  fi
```
##### 02-Read input with case 
```html
#!/bin/bash
printf "Would you like to play a game? (please enter yes or no): "
read input
case $input in
  [Yy]*) echo "I would like to play a game too, but I am only a sample script.";;
  [Nn]*) echo "I am very disappointed.";;
  *) echo "I said to please enter yes or no. Now formatting your disk...";;
esac
```

