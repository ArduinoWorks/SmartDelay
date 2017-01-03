# SmartDelay
The SmartDelay class for non blocking delays in arduino sketches.

I use this class for non-blocking delays or cooperative multitasking emulation.

    // Declaration
    SmartDelay var(delay_in_microseconds);

    loop () {
      // Typical code block.
      if (var.Now()) {
        // The action after delay.
        // This code is executed each "delay_in_microseconds".
        // After this call the variable has been resetted for next delay. See Wait() method.
      }
      ...
    }

    var.Get(); // Get the current delay.
    
    old=var.Set(new_delay_micros);  // Set new delay interval and returns the old one.
    
    old=var.Wait(); Reset delay from right now.

The method Now() returns FALSE when the waiting time is not reached. It returns true if the internal timer is over and resets the timer again.

The method Get() just returns the current waiting interval.

The method Set() used for changing waiting time of fly. It returns the old timer.

The method Wait() returns the waiting time and reset the internal timer. It is useful to hold the timer. It prevents the method Now() to work. 
