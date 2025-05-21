# advprog-module10-timer

### Tutorial 1.2
![alt text](image.png)

Even though the line `"Catherine's Komputer: hey hey"` comes **after** the `spawner.spawn(...)` line, it is printed **first** in the output because it is the **main function**.

The line `spawner.spawn(...)` does not run the async block immediately, it just **schedules the task for later**. The actual async task: printing `"Catherine's Komputer: howdy!"` and `"Catherine's Komputer: done!"` starts running only **after** we call `executor.run()`.

### Tutorial 1.3
![alt text](<Screenshot (315).png>)
![alt text](<Screenshot (316).png>)

The line `println!("Catherine's Komputer: hey hey")` gets printed **immediately** because it's synchronous and in the `main` function.
- Each `spawner.spawn(...)` call schedules an asynchronous task, but these tasks **do not start immediately**.
- Only when `executor.run()` is called does the executor begin polling the tasks.
- Since we **didn't call `drop(spawner)`**, the `executor.run()` will keep running, waiting for more tasks indefinitely.