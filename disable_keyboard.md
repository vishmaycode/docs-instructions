# Disable keybaord

- https://askubuntu.com/questions/160945/is-there-a-way-to-disable-a-laptops-internal-keyboard

```shell
sudo apt install xinput
xinput list
```

 - to list devices
 - find "AT Translated Set 2 keyboard" and its id
 - also note slave keyboard number
 ↳ AT Translated Set 2 keyboard            	id=17	[slave  keyboard (3)]


#### Disable it using 
```shell
xinput float <id#>
xinput float 17
```

#### Re-enable it using
```shell
xinput reattach <id#> <master#>
xinput reattach 17 3
```


## for the above functionality i have created a script

```shell
nano ~/.keyboard.sh
chmod 755 ~/.keyboard.sh
```

```shell
#!/bin/bash

MASTER_ID_FILE="/tmp/keyboard_master_id"

# Function to get the id of the AT Translated Set 2 keyboard
get_keyboard_id() {
    xinput list | grep "AT Translated Set 2 keyboard" | grep -oP 'id=\K\d+'
}

# Function to get the master keyboard id
get_master_keyboard_id() {
    xinput list | grep "AT Translated Set 2 keyboard" | grep -oP '\[\K\w+\s+\w+\s+\(\d+\)' | grep -oP '\(\K\d+'
}

# Function to save the master keyboard id
save_master_keyboard_id() {
    local master_id=$(get_master_keyboard_id)
    if [ -n "$master_id" ]; then
        echo "$master_id" > "$MASTER_ID_FILE"
        echo "Master keyboard ID saved"
    else
        echo "Failed to get master keyboard ID"
        exit 1
    fi
}

# Function to get the saved master keyboard id
get_saved_master_keyboard_id() {
    if [ -f "$MASTER_ID_FILE" ]; then
        cat "$MASTER_ID_FILE"
    else
        echo "Saved master keyboard ID not found"
        exit 1
    fi
}

# Function to disable the keyboard
disable_keyboard() {
    local keyboard_id=$(get_keyboard_id)
    if [ -n "$keyboard_id" ]; then
        save_master_keyboard_id
        xinput float "$keyboard_id"
        echo "Keyboard disabled"
    else
        echo "Keyboard not found"
    fi
}

# Function to enable the keyboard
enable_keyboard() {
    local keyboard_id=$(get_keyboard_id)
    local master_id=$(get_saved_master_keyboard_id)
    if [ -n "$keyboard_id" ] && [ -n "$master_id" ]; then
        xinput reattach "$keyboard_id" "$master_id"
        echo "Keyboard enabled"
        rm -f "$MASTER_ID_FILE"
    else
        echo "Keyboard or saved master keyboard ID not found"
    fi
}

# Main script
case "$1" in
    disable)
        disable_keyboard
        ;;
    enable)
        enable_keyboard
        ;;
    *)
        echo "Usage: $0 {disable|enable}"
        exit 1
        ;;
esac

exit 0
```
