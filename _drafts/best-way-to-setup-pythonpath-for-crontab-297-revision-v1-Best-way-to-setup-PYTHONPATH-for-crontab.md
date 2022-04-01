---
id: 103
title: 'Best way to setup PYTHONPATH for crontab'
date: '2018-08-12T18:57:43+00:00'
author: 'Asif Rehan'
layout: revision
guid: 'https://asifrehan.com/97-revision-v1/'
permalink: /97-revision-v1/
---

<article class="post-160 post type-post status-publish format-standard hentry category-uncategorized tag-coding tag-crontab tag-linux tag-programming tag-python tag-pythonpath tag-system" id="post-160"><header class="entry-header"></header></article><article class="post-120 post type-post status-publish format-standard hentry category-tech category-tech-tech tag-backend tag-crontab tag-linux tag-server tag-software tag-system" id="post-120"><div class="entry-content">When setting up a crontab job in Linux machine, these essential steps are required for a successful system operation

1. Update the cron file by adding the new script on schedule
2. Check the frequency of the schedule. Such as for running at 7 minutes interval, use ```
    */7 * * * *   python /path/to/script.py
    ```
    
    Or for running every hour at 7th minute, use
    
    ```
    7  *  *  *  *  python /path/to/script.py
    ```
3. Check the file permission for the script. If it is not executable, then make it executable ```
    ls -l /path/to/script.py
    ```
    
    Then if the file is not executable by the user add the permission by
    
    ```
    chmod 755 /path/to/script.py
    ```
    
    (you may need to have sudo access if you are not the owner of the file. For changing ownership of a file or folder, use chown command on Linux variants)
4. Check the file permission for the output site if the script produces some files. If the continuing folder or the output file does not have a write-access, ensure it is writable. Follow the similar process as in step#3.
5. You may channel any print statements to a file such as ```
    7 * * * * python /path/to/script.py /path/to/output/file.txt 2&1
    ```
6. Or better yet, use [Python logging library](https://web.archive.org/web/20170607032258/https://docs.python.org/2/library/logging.html) to create useful log files and show if the program ran correctly.

</div></article>