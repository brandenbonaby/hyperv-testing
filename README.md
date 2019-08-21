# hyperv-testing Tool

    My testing tool for the hyperv drivers in the linux kernel,
    you'll need to make sure to compile your kernel using
    menuconfig to turn HYPERV_TESTING on in kernel (5.3).
    Currently this will inject delays into host to guest communications.


<h2> usage:  </h2>

vmbus_testing [-s] [0|1] [-q] [-p] <debugfs-path>  
vmbus_testing -s [0|1] [-q] -p <debugfs-path> delay -d [buffer-delay-value] [message-delay-value]  
vmbus_testing [-q] delay [buffer-delay-value] [message-delay-value] -E  
vmbus_testing [-q] delay [buffer-delay-value] [message-delay-value] -D  
vmbus_testing [-q] disable-all  
vmbus_testing [-q] view [-v|-V]  
vmbus_testing --version  
  
<h2> positional arguments: </h2>  
  
    delay               Delay buffer/message reads in microseconds.  
    disable-all         Disable ALL testing on all vmbus devices.  
    view                View testing on vmbus devices.  
  
<h2> optional arguments: </h2>  
  
    -h, --help            show this help message and exit
  
    --version             show program's version number and exit  
  
    -q, --quiet           silence none important test messages
  
    -s , --state          Turn testing ON or OFF for a single device. The value
                          (1) will turn testing ON. The value of (0) will turn
                          testing OFF with the default set to (0).
  
    -p , --path           Refers to the debugfs path to a vmbus device. If the
                          path is not a valid path to a vmbus device, the
                          program will exit. The path must be the absolute path.
                          devices are found in /sys/kernel/debug/hyperv/<device>

<h2> optional arguments: when positional argument 'delay' used </h2> 
  
    -h, --help            show this help message and exit

    -E, --en-all-delay    Enable Buffer/Message Delay testing on ALL devices.
                          Use -d option with this to set the values for both the
                          buffer delay and the message delay. No value can be
                          (0) or less than (-1). If testing is disabled on a
                          device prior to running this command, testing will be
                          enabled on the device as a result of this command.
                        
    -D, --dis-all-delay  Disable Buffer/Message delay testing on ALL devices. A
                         value equal to (-1) will keep the current delay value,
                         and a value equal to (0) will remove delay testing for
                         the specified delay column. only values (-1) and (0)
                         will be accepted but at least one value must be a (0)
                         or a (-1).

    -d  , --delay-time    Buffer/message delay time. A value of (0) will disable
                          delay testing on the specified delay column, while a
                          value of (-1) will ignore the specfied delay column.
                          The default values are [0] & [0]. The first column
                          represents the buffer delay value and the second
                          represents the message delay value. Value constraints:
                          -1 <= value <= 1000.

<h2> optional arguments: when positional argument 'view' used </h2> 

    -V, --view-all-states    View the test status for all vmbus devices.
  
    -v, --view-single-device View test values for a single vmbus device.
