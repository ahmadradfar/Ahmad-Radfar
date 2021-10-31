# Life
This app helps user to manage time more efficiently. User adds tasks with duration, clicks to one which he is going to do and app starts to count how much time left to finish task. While user does his task he can close the app, block a screen and he will be notified when ever task time will be over. After that user can chose another task or take a rest.

# Preview
![reviw](https://user-images.githubusercontent.com/56368532/139577921-12d47a19-e293-4cbf-ad0b-3ac93d8aadc4.gif)

# Logic behind the app

MainActivity is a launcher activity with RecyclerView in it. RecyclerView contains tasks. 
When some task is clicked MainActivity starts a TimerService via bindService() and startService() methods. So TimerService is both bound and started service, it is responsible for counting time which left to finish clicked task. 
When TimerService is running MainActivity gets updated information from it and updates RecyclerView's adapter every second. 
When MainActivity becomes invisible it unbinds from TimerService and stops updating RecyclerView's adapter but TimerService doesn't stop working and displays task's information in notification. 
If user opens app again MainActivity will update RecyclerView's adapter every second in case of TimerService is running, otherwise it just will show current state of RecyclerView.
