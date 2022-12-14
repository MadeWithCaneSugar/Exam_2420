# Exam_2420
Mitchel Webb
A01279081

## part 1
```
sudo apt update
sudo apt upgrade
```

## part 2
![part2 vim](images/part2.PNG)

made single character changes (replacing 1 with 0, V with C) using `replace` mode by hitting r and typing the new character when the cursor was moved into place (used ctrl+arrows to move cursor quickly)

longer word replacements(replcing numbs with :digit:) made by hitting v to enter `visual` mode and then selecting the word with an arrow key, deleting it, then entering `insert` mode and typing the new word.

## part 3
![part3 man](images/part3-1.PNG)
Searched `current` in the man page to find how to specify the current boot
(no need to specify anything past `-b` since the current boot is the default)

![part3 man](images/part3-2.PNG)
Searched `priority` to find in the man page how to specify priority
(in this case the option is `--priority==4`)

![part3 man](images/part3-3.PNG)
searched `json` to find in the man page how to specify a "nice pretty json"
(in this case the option is `--output-fields=json-pretty`)

![part3 command](images/part3_command.PNG)

##part 4
```
#!/bin/bash

# Search the passwd file in /etc
users=$(grep -E '[[:digit:]]{4}' /etc/passwd)

# Loop through the list of users
for user in $users
do
    # Getting the specific details
    NAME=$(echo $user | cut -d':' -f1)
    UID=$(echo $user | cut -d':' -f3)
    SHELL=$(echo $user | cut -d':' -f7)

    # Checking to make sure UID is between 1000 and 5000
    if [ "$uid" -ge 1000 ] && [ "$uid" -le 5000 ]
    then
        # Printing the data
        # echo "$NAME - $UID - $SHELL"

        # printing the data in the motd file
        cho"$NAME - $UID - $SHELL" >> /etc/motd
    fi
done
```
![part4 location](images/part4_script_location.PNG)

## part 5
```
[Unit]
Description=Runs the part 4 file which gets user information

[Service]
Type=oneshot
ExecStart=/opt/part4/part4


[Install]
WantedBy=multi-user.target
```
![part5 location](images/part5_service_location.PNG)
![part5 service starting and enabling](images/part5_start.PNG)


## part 6
```
[Unit]
Description=Timer that runs part5.service to run part4(script) 1 minute after booting + once every day the unit is active. Since this uses a monotonic timer, it counts by seconds. 60 seconds after boot, and then every day, which is 86400 seconds.

[Timer]
OnStartupSec=60
OnUnitActiveSec=86400

[Install]
WantedBy=timers.target
```
![part6 location](images/part6_timer_location.PNG)
Had to name weirdly because of my service fie name
![part6 timer starting and enabling](images/part6_start.PNG)
![part6 timer status check](images/part6_timer_status.PNG)





