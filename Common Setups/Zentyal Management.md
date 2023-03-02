To remove computers from the domain please run the following on the Zentyal instance.

```sh
sudo pdbedit -x -m NAME_OF_COMPUTER_TO_REMOVE
sudo userdel NAME_OF_COMPUTER_TO_REMOVE\$
```