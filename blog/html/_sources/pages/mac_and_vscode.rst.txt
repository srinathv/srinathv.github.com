Macs and VS Code
===================================

.. conten: Tricks for VS Code on Mac Os X

.. highlight:: bash

VS Code Helper udpate issue fix 
-------------------------------

I have found that the helper app for VS code seems to have ownership issues.
A possible fix is ::

    $sudo chown -R $USER:admin ~/Library/Caches/com.microsoft.VSCode
    $sudo chown -R $USER:admin ~/Library/Caches/com.microsoft.VSCode.ShipIt
    $sudo chown -R $USER:admin /Applications/Visual\ Studio\ Code.app/


