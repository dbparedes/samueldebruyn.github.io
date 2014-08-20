---
layout: post
title: "Queue for MessageDialog in Windows RT"
---

While I was writing a few of my Windows Store applications I used the MessageDialog class a lot.
It's the easiest way to show a quick informative pop-up message or question to the user.
However, when you tend to use this quite often you'll probably run into a problem.

The Windows Runtime framework doesn't allow you to stack MessageDialogs, queue them etc.
So if you need to display one, you'll have to make sure that no other MessageDialog is already open.
There are a few cases in which this would be annoying.

The Singleton class below will make sure that you can queue MessageDialogs and that this problem will never occur.

Instead of using

    myDialog.ShowAsync()

use

    MessageDialogQueue.PushMessageDialog(myDialog)

The dialog will be displayed after all previous MessageDialogs are closed.

{% gist SamuelDebruyn/efaf5ae8e0af3ac2e0d9 %}
