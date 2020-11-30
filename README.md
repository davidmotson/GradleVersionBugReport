### Expected Behavior
I expect that a version specified as [1.2.3] is different from 1.2.3
### Current Behavior
When examining the DependencyResult object object for a resolved strict dependency, there doesn't appear to be any difference between strict and non-strict versions
### Context
I maintain a gradle plugin which monitors strict versions and ensures that they are respected. This bug currently breaks the plugin, since there is no discernible difference between strict and non-strict versions.

### Steps to Reproduce 
1. Import this project
2. Run a build or sync
3. Observe generated error messages:

Observed in 6.3 and lower: 
com.google.firebase:firebase-messaging-directboot:20.3.0 ->  com.google.firebase:firebase-messaging:[20.3.0]
This correctly captures the strict dependency firebase-messaging-directboot has on firebase-messaging.

Observed in 6.4.1 and higher:
com.google.firebase:firebase-messaging-directboot:20.3.0 ->  com.google.firebase:firebase-messaging:20.3.0
This incorrectly erases the strict dependency.

### Your Environment
Bug is reproducible with gradle version 6.4.1 and higher, change gradle version in wrapper to 6.3 to see expected behavior.
