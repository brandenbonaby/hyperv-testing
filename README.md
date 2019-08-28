# hyperv-testing Tool

    My testing tool for the hyperv drivers in the linux kernel,
    you'll need to make sure to compile your kernel using
    menuconfig to enable HYPERV_TESTING. NOTE* this is only available in
    kernel versions (5.3.0<rc6>) and up.

<h4> Current testing methods: </h4>

   1. delay
     
<h2> usage:  </h2>

    vmbus_testing delay [-e|-E] -t [value] [value] [-p] <debugfs-path>
    vmbus_testing [disable_single | d] -p <debugfs-path>
    vmbus_testing [disable_all    | D]  
    vmbus_testing [view_all       | V]
    vmbus_testing [view_single    | v] -p <debugfs-path>
    vmbus_testing --version  
  
<h2> positional arguments: </h2>  
  
    ddelay                 Delay the ring buffer interrupt or the ring buffer
                           message reads in microseconds.
    disable_all    (D)     Disable ALL testing on ALL vmbus devices.
    disable_single (d)     Disable ALL testing on a SINGLE vmbus device.
    view_all       (V)     View the test state for ALL vmbus devices.
    view_single    (v)     View the test values for a SINGLE vmbus device. 
  
<h2> optional arguments: </h2>  
  
    -h, --help             show this help message and exit
  
    --version              show program's version number and exit  
  
    -q, --quiet            silence none important test messages

<h2> optional arguments: Shared by test methods and arguments postfixed with _single </h2> 
  
     -h, --help            show this help message and exit
     -E, --enable_all      Enable the specified test type on ALL vmbus devices.
     -e, --enable_single   Enable the specified test type on a SINGLE vmbus
                           device.
     -p, --path            Debugfs path to a vmbus device. The path must be the
                           absolute path to the device.
                           
<h2> optional arguments: 'delay' specific arguments </h2> 
     
      -t  , --delay_time   Set [buffer] & [message] delay time. Value
                           constraints: -1 == value or 0 < value <= 1000. Use -1
                           to keep the previous value for that delay type, or a
                           value > 0 <= 1000 to change the delay time.
