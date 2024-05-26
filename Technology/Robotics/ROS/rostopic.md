#ros 
rostopic is a command-line tool for printing information about [[Overview|Overview]] topics.
For `rostopic` options type: `rostopic -h`:

list topics: `rostopic list`. Add `-v` for verbose.
#### publish
Usage: `rostopic pub /topic type [args...]`
 see `rostopic pub -h` for options
example: `rostopic pub -1 /pleco/app_vacuum_power std_msgs/Int32 "data: -90"`,
- `-1` publish only once

##### send json file to rostopic:
```sh
rostopic pub -1 /pleco/version_control std_msgs/String  "$(cat msg.txt)"
```
*msg.txt* should be like this:
```
"data: '{
  \"command\": \"start\",
  \"version\": \"release-0.4.72\",
  \"source\": \"server\"
}'"
```

present a message structure: `rostopic type /turtle1/cmd_vel | rosmsg show`. Use [[rosmsg]] to present the message structure and internal types.