GitHub's notification system is a thing of beauty, and it's led me to "watch" more projects. When you [watch something on GitHub](https://help.github.com/articles/watching-repositories), it notifies you of all new discussions happening on that project. It's a terrific way to ambiently track the evolution of a project relevant to your work.

However, as I did more of this, notifications for threads I was **participating in** became easier to miss. GitHub considers you `Participating` if you're @-mentioned or if you opened/commented on an issue.

GitHub does draw this distinction in its [Notification Settings](https://github.com/settings/notifications) - you can decide whether `Watching` or `Participating` notices should go into a web-only notification feed, or your email. 

<img src="https://konklone.com/assets/images/blog/github-notifications.png" class="block" />

But I hate web notifications (anywhere), and always fall behind on them. Email is the one place I've fully committed to staying on top of.

Fortunately, GitHub's smart about marking `Participating` notifications as `To:` your email address, so I was able to fix this for me with a filter:

```text
from:(notifications@github.com) to:me
```

And making any emails matching that filter get auto-labeled with something colorful:

<img src="https://konklone.com/assets/images/blog/github-labels.png" class="block" />

This makes notifications I'm `Participating` in stand out visually, and lets me brush over notifications more quickly from projects I'm merely `Watching`. Overall, it makes me **more** likely to watch other people's work, knowing I can dispatch non-relevant emails more easily.

This does feel like at least a small failure in GitHub's notification system. I shouldn't be forced to decide to whether to drive Watch notifications out of my email entirely, or to manually set up a filter and colored label me. Email's an old, alien environment for GitHub to innovate in, and there are probably better solutions, but the simplest fix might be a small prefix to the subject line, like `[@username]` or `[direct]` or `[ME]` or something. 

Either way, I hope this filter hack is helpful to someone!
