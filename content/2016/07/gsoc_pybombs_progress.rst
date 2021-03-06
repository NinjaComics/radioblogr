[GSoC] Pybombs and more  - Weekly Update
########################################

:date: 2016-07-22 20:50
:tags: gsoc, weekly progress, coding period
:category: /bin
:author: Ravi Sharan
:slug: gsoc_pybombs_progress

In the last week, I have worked on two things - main one being Pybombs GUI and
a bit on addressing the pybombs' support for airgapped systems. Read along to know
the updates on `pybombs-qtgui`_ and the idea for this pybombs `issue`_

Pybombs - final touches
=======================

Like I mentioned in my last week's update, I have added a dialog to collect the
logs generated by pybombs-qtgui and the `pybombs-cli`_ running as the backend.
Another problem I worked on is to deal with the mutliprocess functionality introduced
in pybombs-gui to make the user experience smooth while browsing the apps on app-store.
Earlier, I had pushed a part of the GUI stuff to a non-main thread and that created
few issues while running the app - newbie mistakes ! It took some good amount of
time to figure out the problem and fix it. The app now works smooth (no warnings
or Qt complaints from the non-main thread).

Another problem I faced(wroked on) this week is the use of `pkexec`_ with pybombs
app store. If pybombs were just a GUI for one package manager, a single policy
file will do the trick. But pybombs is a wrapper around the multiple package managers
that are native to the operating system, example: pip, pacman, dnf/yum etc.,

Here's the tricky part, even when we add a policy file to each of the package
managers native to the distro, pybombs may call a native package manager and pip
to build a system wide package and a pypi package consequetively. Due to pkexec's
nice security feature, user is prompted with a authentication agent a lot of times
depending on the package managers invoked. I am currently working on this and
this is the only issue to be addressed before releasing the app store.


GNU Radio OOT Module mirror repos
=================================

What happens when you host a GNU Radio hackathon, where you are supposed to provide
GNU Radio and the OOT Modules but have limited internet access ? That's just one
simple scenario where an end user has little or no access to internet.

One solution is to maintain a mirror of GNU Radio and all the OOT Modules on a
central location and which can be easily accessible by the airgapped systems as
well. Gitlab has a nice feature of hosting mirror repositories and updates the
repo once in an hour. The idea is similar to maintaining vim scripts mirror repo
where a user can clone the complete set of modules with a single command or select
those repos which will fit the need. This idea also addresses the archiving problem
for current CGRAN website. The CGRAN site can update the information available from
the mirror repos.

Similar projects that I have come across in similar lines are GDG Suzhou's
`android-repository`_, `vim scripts`_ and a recent activity on GNU Radio `mailing list`_.
I will update more on this idea in next week's progress report. That's the update for now,
Pip pip ! If you followed this post till here, enjoy this random `xkcd comic strip`_ !

.. _pybombs-cli: https://github.com/gnuradio/pybombs
.. _pybombs-qtgui: https://www.gitlab.com/NinjaComics/pybombs-qtgui
.. _xkcd comic strip: https://c.xkcd.com/random/comic/
.. _pkexec: https://www.freedesktop.org/software/polkit/docs/0.105/pkexec.1.html
.. _issue: https://github.com/gnuradio/pybombs/issues/236
.. _vim scripts: https://github.com/vim-scripts
.. _android-repository: https://github.com/renfeng/android-repository
.. _mailing list: https://lists.gnu.org/archive/html/discuss-gnuradio/2016-06/msg00162.html
